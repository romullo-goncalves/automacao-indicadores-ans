# 📝 Formulário de Entrada de Dados – Automação dos ANS

Este documento apresenta o modelo de formulário padronizado utilizado pelas superintendências para envio mensal dos indicadores dos Acordos de Nível de Serviço (ANS).

O preenchimento correto deste formulário é fundamental para o sucesso do processo automatizado.

---

## 📋 Estrutura do Formulário

| Campo                          | Tipo        | Obrigatório | Descrição                                                                 |
|-------------------------------|-------------|-------------|---------------------------------------------------------------------------|
| Nome da Superintendência      | Texto       | Sim         | Nome completo da unidade responsável pelo envio dos dados.               |
| Mês de Referência             | Mês/Ano     | Sim         | Mês correspondente aos dados enviados (ex: 04/2025).                     |
| Indicador                     | Texto       | Sim         | Nome do indicador (ex: Tempo Médio de Atendimento).                      |
| Valor Apurado                 | Numérico    | Sim         | Valor registrado no mês de referência.                                   |
| Unidade de Medida             | Texto       | Sim         | Unidade do indicador (ex: minutos, %, etc.).                             |
| Meta do Indicador             | Numérico    | Sim         | Meta mensal acordada.                                                    |
| Valor Mínimo Aceitável        | Numérico    | Não         | Valor mínimo dentro da faixa de aceitação.                              |
| Valor Máximo Aceitável        | Numérico    | Não         | Valor máximo dentro da faixa de aceitação.                              |
| Justificativa (se necessário) | Texto longo | Não         | Em caso de desvio, registrar a justificativa para análise posterior.     |
| Responsável pelo Preenchimento| Texto       | Sim         | Nome do responsável técnico pelo envio das informações.                  |

---

## 💡 Observações

- O formulário deve ser preenchido em formato Excel (.xlsx), conforme modelo fornecido.
- Os campos obrigatórios devem estar 100% preenchidos. Dados incompletos serão rejeitados pelo validador automático.
- O campo “Justificativa” deve ser preenchido sempre que houver desvio em relação à meta estabelecida.
- Os valores devem ser consistentes com a unidade de medida informada.

---

Este formulário serve como base para integração com o Power BI e para validação automatizada dos dados enviados por cada superintendência.
