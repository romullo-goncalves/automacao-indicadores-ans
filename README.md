# 🛠️ Automação de Monitoramento dos ANS – Avaliação Técnica

Este repositório contém a solução desenvolvida para a avaliação técnica do processo seletivo de **Analista de Processos II – ANS 2024**, conforme solicitado pela **Gerência de Processos e Qualidade (GPQ)**.

O objetivo é demonstrar a automação do processo de monitoramento dos Acordos de Nível de Serviço (ANS) da Diretoria Corporativa, incluindo coleta automatizada de dados, geração de relatórios, painéis de visualização e lógica de alertas.

---

## 📁 Estrutura do Repositório

- `README.md` – Visão geral da solução e instruções
- `docs/` – Documentação do processo:
  - `user-stories.md` – Histórias do usuário
  - `requirements.md` – Requisitos funcionais e não funcionais
  - `rules.md` – Regras de negócio
  - `forms.md` – Modelo de formulário de entrada
  - `notifications.md` – Templates de notificação por e-mail
  - `prototypes.md` – Protótipos e mockups
- `bizagi/` – Fluxo do processo modelado em Bizagi (PDF)
- `powerbi/` – Painel de indicadores e prints do Power BI
- `code/` – Script de coleta e geração de dados (Python)
- `link_processo.md` – Link de acesso ao processo automatizado em funcionamento

---

## ✅ Entregas

### 1. Documentação Técnica
Disponível na pasta `docs/`, contempla:

- Histórias do usuário
- Requisitos (funcionais, não funcionais e regras)
- Protótipos
- Templates de notificação
- Formulário de entrada de dados

### 2. Fluxo Bizagi
Arquivo PDF do processo modelado com início na coleta dos dados até o envio de alertas de não conformidade (`bizagi/fluxo-ans.pdf`).

### 3. Painel Power BI
Visualização mensal dos KPIs, com filtros por superintendência e indicador, disponível em `powerbi/`.

### 4. Link do Processo Automatizado
Endereço para visualização do processo em funcionamento (Power Automate ou ambiente simulado), disponível em `link_processo.md`.

---

## 🧠 Tecnologias Utilizadas

- **Python** – Coleta e formatação dos dados dos ANS
- **Power BI** – Dashboards com indicadores e KPIs
- **Bizagi** – Modelagem do fluxo do processo
- **Power Automate** – Agendamento e notificações (simulado)
- **GitHub** – Organização e versionamento do projeto

---

## 📚 Contexto

Atualmente, os dados das superintendências são recebidos em planilhas Excel e tratados manualmente, o que:

- Introduz risco de erros e inconsistências
- Gera atrasos na produção dos relatórios
- Dificulta a análise preditiva de desempenho

A solução proposta automatiza esse processo para promover **eficiência, rastreabilidade e confiabilidade**, alinhando-se à missão da GPQ de garantir a melhoria contínua e a visão sistêmica dos processos.

---

## 📬 Contato

Rômullo Gonçalves  
romullodf@gmail.com
