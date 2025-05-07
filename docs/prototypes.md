# 🧩 Protótipos e Wireframes – Automação dos ANS

Este documento descreve as propostas visuais e sugestões de interface para o sistema de monitoramento dos ANS, incluindo o formulário de entrada, notificações e painel Power BI.

---

## 📝 Formulário de Envio de Indicadores

- Estrutura: Tabela simples em Excel (.xlsx) com colunas padronizadas.
- Campos obrigatórios destacados em amarelo.
- Validação de dados com mensagens automáticas (ex: "Campo obrigatório", "Valor inválido").

📌 Referência: ver `docs/forms.md`

---

## ✉️ Notificações Automáticas

- Estilo: E-mails em HTML simples, com assunto claro e linguagem objetiva.
- Cores:
  - Vermelho (🚨) para alertas de desvio
  - Azul (⏰) para pendências
  - Verde (✅) para confirmações

📌 Referência: ver `docs/notifications.md`

---

## 📊 Painel Power BI

O painel está estruturado para responder rapidamente às seguintes perguntas:

| Objetivo                               | Elemento Visual                   |
|----------------------------------------|-----------------------------------|
| Indicador fora do padrão?              | Cartões com regras de cores       |
| Qual superintendência está em atraso?  | Tabela com semáforo vermelho      |
| Evolução do desempenho ao longo dos meses? | Gráfico de linhas ou colunas empilhadas |
| Comparativo entre superintendências?   | Gráfico de barras agrupadas       |
| Tendência geral dos KPIs?             | KPI cards com meta vs. real       |

### Filtros Disponíveis:

- Mês/Ano
- Superintendência
- Tipo de Indicador
- Status (Conforme, Fora do padrão, Atrasado, Sem dados)

---

## 🔧 Protótipos visuais

Caso não haja tempo hábil para criação de mockups gráficos no Figma ou PowerPoint, recomenda-se:

- Inserir capturas de tela do painel Power BI real na pasta `powerbi/`
- Incluir modelo de planilha de entrada na pasta `code/` ou `docs/`
- Anexar PDF do fluxo do processo na pasta `bizagi/`

---

Esses elementos visuais são suficientes para demonstrar usabilidade, lógica do processo e adequação às necessidades dos usuários.
