# 🛠️ Automação de Monitoramento dos ANS – Avaliação Técnica

Este repositório contém a solução desenvolvida para a avaliação técnica do processo seletivo de **Analista de Processos II – ANS 2024**, conforme solicitado pela **Gerência de Processos e Qualidade (GPQ)**.

O objetivo é demonstrar a automação do processo de monitoramento dos Acordos de Nível de Serviço (ANS) da Diretoria Corporativa, incluindo coleta automatizada de dados, geração de relatórios, painéis de visualização e lógica de alertas.

---

## 📌 Estrutura do Repositório

├── README.md
├── docs/
│ ├── user-stories.md
│ ├── requirements.md
│ ├── rules.md
│ ├── forms.md
│ ├── notifications.md
│ └── prototypes.md
├── bizagi/
│ └── fluxo-ans.pdf
├── powerbi/
│ └── painel-ans.png
├── code/
│ └── script_coleta_ans.py
└── link_processo.md


## 🧾 Entregas

✅ **1. Documentação Técnica**  
Disponível na pasta `docs/`, contempla:

- Histórias do usuário
- Requisitos funcionais e não funcionais
- Regras de negócio
- Protótipos de interface
- Templates de notificação
- Exemplos de formulário de entrada de dados

📥 **2. Fluxo modelado no Bizagi**  
O arquivo `fluxo-ans.pdf`, na pasta `bizagi/`, ilustra o processo completo da coleta à emissão de alertas.

📊 **3. Dashboard Power BI**  
Exemplos e prints do painel estão na pasta `powerbi/`, contendo KPIs mensais e insights.

🔗 **4. Link do processo automatizado em funcionamento**  
Está descrito no arquivo `link_processo.md`.

---

## 🧠 Tecnologias Utilizadas

- **Python** – Coleta e formatação dos dados dos ANS
- **Power BI** – Dashboards com indicadores e KPIs
- **Bizagi** – Modelagem do fluxo do processo
- **Power Automate** – Agendamento e notificações (simulado)
- **Markdown/GitHub** – Documentação

---

## 🧑‍💼 Contexto

Atualmente, os dados das superintendências são recebidos em planilhas Excel, sendo tratados manualmente para geração dos dashboards. Esse processo apresenta riscos como:

- Inconsistência nos dados
- Atrasos na entrega de relatórios
- Dificuldade na análise preditiva

A proposta é substituir esse processo por uma solução automatizada, utilizando ferramentas livres e corporativas, garantindo **precisão, rastreabilidade e agilidade** na gestão dos ANS.

---

## 📬 Contato

Rômullo Gonçalves  
romullodf@gmail.com

