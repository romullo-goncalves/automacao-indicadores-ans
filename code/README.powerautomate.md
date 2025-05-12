📥 1. Gatilho: Quando um novo e-mail chega
- Ação: 'When a new email arrives (V3)' [Outlook 365]
- Filtro: Subject contains 'Dados - ANS'
- Saída esperada: Corpo do e-mail com anexo(s) Excel

📦 2. Inicializar variável 'AnexosXLSX'
- Tipo: Array
- Valor: []
- Uso: Armazenar anexo(s) válidos .xlsx como JSON

📁 3. Condição: Attachment?
- Condição: triggerOutputs()?['body/hasAttachments'] is equal to true
- Não: Enviar e-mail com aviso 'Arquivo não encontrado para validação dos ANS' e Terminate (Cancelled)
- Sim: Continuar

🔁 4. For each (Attachment)
- Itens: triggerOutputs()?['body/attachments']

🧪 4.1 Condição: Nome do anexo termina com .xlsx?
- Expressão: endsWith(item()?['name'],'xlsx')
- Sim:
  - Ação: Get attachment (V2)
  - Mensagem ID: triggerOutputs()?['body/Id']
  - Attachment ID: item()?['Id']

  - Append to array variable 'AnexosXLSX' com:
    {
       "Name": "@{outputs('Get_Attachment_(V2)')?['body/name']}",
       "ContentBytes": "@{outputs('Get_Attachment_(V2)')?['body/contentBytes']}"
    }

🌐 5. HTTP: Enviar para Azure Function
- Método: POST
- URL: https://funcaovalidar.azurewebsites.net/api/HttpTrigger_validate_excel_base64?code=chaveaqui
- Headers: Content-Type: application/json
- Body: @{variables('AnexosXLSX')}
- Saída esperada: JSON com validações por arquivo e aba

🧾 6. Parse JSON
- Content: @body('HTTP')
- Schema: 
{
    "type": "object",
    "additionalProperties": {
        "type": "object",
        "properties": {
            "validação_OK": {
                "type": "boolean"
            },
            "colunas_faltando": {
                "type": "array",
                "items": {
                    "type": "string"
                }
            },
            "colunas_extras": {
                "type": "array",
                "items": {
                    "type": "string"
                }
            },
            "tipos_incorretos": {
                "type": "object",
                "additionalProperties": {
                    "type": "object",
                    "properties": {
                        "esperado": {
                            "type": "string"
                        },
                        "encontrado": {
                            "type": "string"
                        }
                    }
                }
            },
            "valores_em_branco": {
                "type": "object",
                "additionalProperties": {
                    "type": "integer"
                }
            },
            "linhas_encontradas": {
                "type": "integer"
            }
        },
        "required": [
            "validação_OK",
            "linhas_encontradas"
        ]
    }
}

📁 7. Inicializar variável 'ErrosValidacao'
- Tipo: String
- Valor: ''
- Uso: Acumular mensagem de erro para todas as abas com falha

🔁 8. Apply to each (Arquivo)
- Itens: outputs('Parse_JSON')
- Nome do loop: ParaCadaArquivo
- Dentro:
  ▸ Nome do arquivo: @items('ParaCadaArquivo')?['Key']
  ▸ Conteúdo do arquivo: @items('ParaCadaArquivo')?['Value']

🔁 8.1 Apply to each (Aba)
- Itens: @items('ParaCadaArquivo')?['Value']
- Nome do loop: ParaCadaAba
- Dentro:
  ▸ Nome da aba: @items('ParaCadaAba')?['Key']
  ▸ Dados da aba: @items('ParaCadaAba')?['Value']

🔎 8.2 Condição: Validação OK?
- Expressão: @equals(items('ParaCadaAba')?['Value']?['validação_OK'], false)
- Se SIM (erro):
  ▸ Append to string variable 'ErrosValidacao':
    concat('* Arquivo: ', items('ParaCadaArquivo')?['Key'], ' | Aba: ', items('ParaCadaAba')?['Key'], '\n')

📌 9. Verificar erros acumulados
- Condição: length(variables('ErrosValidacao')) > 0
- Se SIM:
  ▸ Send email (V2)
    - Para: remetente
    - Assunto: 'Erros na validação dos indicadores ANS'
    - Corpo: @{variables('ErrosValidacao')}
  ▸ Terminate (Status: Failed)

- Se NÃO:
▸ Compose nome do arquivo Excel mensal
- Valor: Indicadores_@{formatDateTime(utcNow(), 'yyyy_MM')}.xlsx
- Saída: 'Indicadores_2024_05.xlsx'

▸  List files in folder
- Pasta: onde ficam os arquivos Excel no OneDrive/SharePoint
- Usado para checar existência do arquivo do mês

🔍 9.1 Condição: Arquivo existe?
- Expressão: @equals(filter(body('List_files_in_folder')?['value'], item()?['name']), @outputs('Compose')]
- Se NÃO:
  ▸ File Name: outputs('Compose')
  ▸ File Content: ""

🔁 10. Apply to each (Arquivo)
- Mesmos itens de Parse_JSON
🔁 10.1 Apply to each (Aba)
- Itens: item()?['Value']
- Dentro:
  ▸ Executar 'Run script' (Office Script) para adicionar aba
    - Parâmetros:
      - Nome da aba: @items('Apply_to_each_2')?['Key']
      - Dados da aba: (retorno estruturado da Azure Function)
  ▸ Enviar e-mail de fluxo realizado com êxito.
