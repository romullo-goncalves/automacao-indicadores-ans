# 📐 Regras de Negócio – Automação dos ANS

Este documento define as regras de negócio aplicadas no processo automatizado de monitoramento dos Acordos de Nível de Serviço (ANS).

---

## 📌 Regras Gerais

1. Cada superintendência é responsável pelo envio mensal dos indicadores no formato padronizado.
2. Os dados devem ser enviados até o 3º dia útil de cada mês.
3. Indicadores enviados fora do prazo são considerados **"Em atraso"** e sinalizados no painel.
4. Todos os campos obrigatórios devem estar preenchidos; dados incompletos bloqueiam a geração do dashboard e disparam alerta de erro.

---

## 🎯 Regras de Cálculo e Avaliação

5. Os indicadores são avaliados conforme parâmetros definidos previamente (meta, valor mínimo, valor máximo).
6. Quando um valor **excede os limites estabelecidos**, o indicador é classificado como **"Fora do padrão"**.
7. Indicadores fora do padrão disparam **alertas automáticos por e-mail** para o responsável da superintendência e para o analista de processos.

---

## 🔄 Regras de Atualização

8. A atualização dos dashboards no Power BI deve ocorrer até o 5º dia útil do mês.
9. O processo automatizado deve verificar periodicamente se novos dados foram disponibilizados.
10. Se não houver atualização de dados no mês corrente, o painel exibirá o status **"Sem dados"** para aquele período.

---

## 🧪 Regras de Teste (Homologação)

11. O sistema deve permitir simulação de dados para fins de homologação, sem afetar os dados reais do painel.
12. Os dados de teste devem ser identificados e descartados da visualização oficial.

---

Essas regras garantem consistência, rastreabilidade e resposta rápida às não conformidades no processo de monitoramento dos ANS.
