# 📤 Fluxo Power Automate – Validação e Armazenamento dos Indicadores ANS

Este fluxo automatiza o recebimento, validação e consolidação dos dados dos indicadores ANS enviados por e-mail em formato Excel. A validação é realizada por uma Azure Function e, após o sucesso, os dados são organizados mensalmente em arquivos .xlsx com uma aba por planilha original.

---

## 🔄 Descrição do Fluxo

### 📥 1. Gatilho: Quando um novo e-mail chega
- Ação: `When a new email arrives (V3)` [Outlook 365]
- Filtro: `Subject contains 'Dados - ANS'`
- Saída esperada: Corpo do e-mail com anexo(s) Excel

### 📦 2. Inicializar variável 'AnexosXLSX'
- Tipo: `Array`
- Valor inicial: `[]`
- Uso: Armazenar anexo(s) válidos .xlsx como JSON

### 📁 3. Condição: Há anexos?
- Expressão: `triggerOutputs()?['body/hasAttachments'] is equal to true`
- Se **Não**: Enviar e-mail com aviso "Arquivo não encontrado para validação dos ANS" e `Terminate (Cancelled)`
- Se **Sim**: Continuar

### 🔁 4. Para cada anexo (For each Attachment)
- Itens: `triggerOutputs()?['body/attachments']`

#### 🧪 4.1 Condição: nome termina com `.xlsx`
- Expressão: `endsWith(item()?['name'], 'xlsx')`
- Se **Sim**:
  - `Get attachment (V2)`
    - `Mensagem ID`: `triggerOutputs()?['body/Id']`
    - `Attachment ID`: `item()?['Id']`
  - `Append to array variable 'AnexosXLSX'` com:
```json
{
  "Name": "@{outputs('Get_Attachment_(V2)')?['body/name']}",
  "ContentBytes": "@{outputs('Get_Attachment_(V2)')?['body/contentBytes']}"
}
```

### 🌐 5. HTTP: Enviar para Azure Function
- Método: `POST`
- URL: `https://funcaovalidar.azurewebsites.net/api/HttpTrigger_validate_excel_base64?code=chaveaqui` //link genérico e não funcional
- Headers: `Content-Type: application/json`
- Body: `@{variables('AnexosXLSX')}`
- Saída esperada: JSON com validações por arquivo e aba

### 🧾 6. Parse JSON
- Content: `@body('HTTP')`
- Schema: objeto com `additionalProperties`, conforme retorno da função

### 📁 7. Inicializar variável 'ErrosValidacao'
- Tipo: `String`
- Valor: `''`
- Uso: Acumular mensagens de erro das abas com falha

### 🔁 8. Apply to each (Arquivo)
- Itens: `outputs('Parse_JSON')`
- Nome: `ParaCadaArquivo`

#### 🔁 8.1 Apply to each (Aba)
- Itens: `@items('ParaCadaArquivo')?['Value']`
- Nome: `ParaCadaAba`

#### 🔎 8.2 Condição: Validação OK?
- Expressão: `@equals(items('ParaCadaAba')?['Value']?['validação_OK'], false)`
- Se **Sim (erro)**:
  - `Append to string variable 'ErrosValidacao'` com:
    `concat('* Arquivo: ', items('ParaCadaArquivo')?['Key'], ' | Aba: ', items('ParaCadaAba')?['Key'], '\n')`

### 📌 9. Verificar erros acumulados
- Condição: `length(variables('ErrosValidacao')) > 0`
- Se **Sim**:
  - Enviar e-mail para remetente com: `@{variables('ErrosValidacao')}`
  - `Terminate (Status: Failed)`

---

## ✅ Execução com sucesso

### 🗓️ Compose nome do arquivo mensal
- Valor: `Indicadores_@{formatDateTime(utcNow(), 'yyyy_MM')}.xlsx`

### 📂 List files in folder
- Verifica se o arquivo do mês já existe no OneDrive/SharePoint

### 🔍 Condição: Arquivo já existe?
- Expressão:
```plaintext
@equals(filter(body('List_files_in_folder')?['value'], item()?['name']), @outputs('Compose'))
```
- Se **Não**:
  - Criar novo arquivo Excel
  - File Name: `outputs('Compose')`
  - File Content: `""`

### 🔁 10. Para cada arquivo (Parse_JSON)
#### 🔁 10.1 Para cada aba (item()?['Value'])
- Executar `Run script (Office Script)` para adicionar aba
  - Parâmetros:
    - `sheetName`: `@items('Apply_to_each_2')?['Key']`
    - `data`: `@items('Apply_to_each_2')?['Value']?['dados']`

### ✅ Finalização
- Enviar e-mail informando sucesso do processamento
