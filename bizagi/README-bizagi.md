# 🔄 README – Processo Bizagi: Monitoramento dos Indicadores ANS

Este documento descreve o fluxo automatizado modelado no Bizagi para o **Monitoramento dos Indicadores ANS** da Diretoria Corporativa, como parte da solução entregue na avaliação técnica para a vaga de **Analista de Processos II – ANS 2024**.

O processo tem como objetivo substituir o monitoramento manual por uma abordagem automatizada, com integrações entre sistemas, lógica de validação e envio de alertas.

---

## 🧭 Visão Geral do Processo

O fluxo completo está estruturado em três grandes subprocessos:

### 1. **Processamento Individual por E-mail**
- Detecção automática de e-mails com anexos de indicadores (Power Automate);
- Coleta dos dados do arquivo recebido;
- Validação de estrutura e tipos de dados com Python;
- Armazenamento dos dados válidos em SharePoint ou Excel;
- Notificação imediata ao remetente em caso de erros.
  
### 2. **Verificação de Envios por Setor**
- Audita os envios feitos por cada superintendência;
- Caso alguma não tenha enviado os dados, é enviado alerta ao gestor correspondente.
  
### 3. **Validação Final e Dashboard**
- Avalia se os valores reais estão dentro dos limites das metas definidas;
- Em caso de não conformidade, é enviado alerta ao gestor da unidade;
- Atualização automatizada do dashboard com os dados validados.

---

## ⚙️ Elementos Técnicos

- **Plataforma de Modelagem:** Bizagi Modeler
- **Integração com sistemas:** Power Automate, Python, SharePoint
- **Orquestração de eventos:** via timer e controle de execução por e-mail
- **Validação:** baseada em regras definidas e consistência de dados
- **Notificações:** baseadas em templates definidos na documentação (`notifications.md`)

---

## 🗂 Arquivos Relacionados

- [`bizagi/fluxo-ans.pdf`](./processo.pdf): Fluxo completo exportado em PDF
- [`docs/notifications.md`](../docs/notifications.md): Templates usados nas mensagens automáticas
- [`docs/rules.md`](../docs/rules.md): Regras de negócio e lógica de decisão

---
