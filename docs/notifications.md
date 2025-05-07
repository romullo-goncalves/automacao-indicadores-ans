# ✉️ Templates de Notificação por E-mail – Automação dos ANS

Este documento apresenta os modelos de mensagens que serão utilizados nas notificações automáticas geradas durante o processo de monitoramento dos ANS.

As mensagens são enviadas por meio de ferramentas de automação (ex: Power Automate) para informar desvios, pendências ou confirmação de atualização dos dados.

---

## 📬 Template 1 – Indicador Fora do Padrão

**Assunto:** 🚨 Indicador fora do padrão – [NOME_DO_INDICADOR]

**Mensagem:**

> Prezado(a) [NOME_DO_RESPONSÁVEL],
>
> O indicador **[NOME_DO_INDICADOR]** da Superintendência **[NOME_DA_SUPERINTENDÊNCIA]** apresentou o valor **[VALOR_APURADO]**, que está fora dos parâmetros esperados para o mês **[MÊS_REFERÊNCIA]**.
>
> **Faixa esperada:** [VALOR_MÍNIMO] a [VALOR_MÁXIMO]  
> **Meta:** [META_DO_INDICADOR]
>
> Por favor, verifique e registre justificativa no formulário padrão, caso necessário.
>
> Atenciosamente,  
> *Sistema de Monitoramento de Indicadores ANS*

---

## 🕑 Template 2 – Dados Não Enviados

**Assunto:** ⏰ Pendência no envio de dados – [NOME_DA_SUPERINTENDÊNCIA]

**Mensagem:**

> Prezado(a) [NOME_DO_RESPONSÁVEL],
>
> Verificamos que os dados da sua superintendência para o mês de **[MÊS_REFERÊNCIA]** ainda **não foram recebidos** no sistema.
>
> Solicitamos o envio do formulário de indicadores até o **3º dia útil do mês**, conforme as diretrizes vigentes.
>
> Em caso de dúvidas, entre em contato com a equipe de Processos.
>
> Atenciosamente,  
> *Sistema de Monitoramento de Indicadores ANS*

---

## ✅ Template 3 – Dados Atualizados com Sucesso

**Assunto:** ✅ Indicadores atualizados – [MÊS_REFERÊNCIA]

**Mensagem:**

> Prezado(a),
>
> Os dados de indicadores ANS do mês **[MÊS_REFERÊNCIA]** foram recebidos e processados com sucesso.
>
> O painel no Power BI foi atualizado e já está disponível para consulta.
>
> 📊 Acesse aqui: [LINK_PAINEL_POWERBI]
>
> Atenciosamente,  
> *Sistema de Monitoramento de Indicadores ANS*
