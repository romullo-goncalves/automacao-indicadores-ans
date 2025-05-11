# 📊 README – Painel Power BI: Monitoramento dos Indicadores ANS

Este painel foi desenvolvido como parte da solução para a avaliação técnica da vaga de **Analista de Processos II**. Ele permite o **monitoramento mensal dos indicadores dos Acordos de Nível de Serviço (ANS)** da Diretoria Corporativa, com foco em eficiência, transparência e usabilidade.

---

## 🎯 Objetivos do Painel

- Visualizar o cumprimento mensal das metas por superintendência e gerência;
- Identificar índices de não conformidade por indicador, período, complexidade e periodicidade;
- Viabilizar tomada de decisão rápida com base em dados atualizados e contextualizados;
- Garantir rastreabilidade e confiabilidade com exibição da data/hora da última atualização.

---

## 🧩 Componentes do Painel

### 1. **Cartões de Resumo**
- Total de Indicadores
- Metas Atingidas / Não Atingidas
- Percentual de Cumprimento

### 2. **Gráfico de Barras Empilhadas**
- Exibe o desempenho de cada **superintendência** e **gerência** em relação ao cumprimento das metas.

### 3. **Gráfico de Rosca (Donut)**
- Apresenta a **distribuição da complexidade** dos indicadores (Alta, Média, Baixa).

### 4. **Tabela Detalhada**
- Lista os indicadores com colunas como:
  - `SUPERINTENDÊNCIA.`, `GERÊNCIA`, `INDICADOR`, `MÊS`, `META 2024`, `REAL 2024`, `Meta Atingida`
- Inclui **formatação condicional** para destaque visual de conformidades e não conformidades.

### 5. **Subtítulo Dinâmico**
- Informa o **período selecionado** de forma contextualizada (ex: "Período: Julho de 2024").

### 6. **Data/Hora de Atualização**
- Apresenta a data e hora da última execução do processo de coleta automatizada.

### 7. **Botão de Redefinir Filtros**
- Permite limpar todos os filtros aplicados com um clique.

---

## 🎛️ Filtros Disponíveis (Segmentações)

- `SUPERINTENDÊNCIA`
- `GERÊNCIA.`
- `MÊS`
- `META ATINGIDA`
- `COMPLEXIDADE`
- `PERIODICIDADE`

> As segmentações atuam de forma conjunta, afetando todos os componentes do painel em tempo real.

---

## 🔐 Segurança de Nível de Linha (RLS)

A estrutura do painel permite a aplicação de **RLS (Row-Level Security)** para restringir o acesso aos dados por superintendência ou gerência.

### 📌 Exemplo de regra RLS:
```dax
[Usuário Logado] = LOOKUPVALUE('Acessos'[EMAIL], 'Acessos'[SIGLA SUP.], 'Indicadores_ANS'[SIGLA SUP.])
```

Ou para filtrar por gerência:
```dax
[Usuário Logado] = LOOKUPVALUE('Acessos'[EMAIL], 'Acessos'[SIGLA GER.], 'Indicadores_ANS'[SIGLA GER.])
```

> Isso exige uma tabela de controle como `Acessos` com colunas como:
> - `USUÁRIO`
> - `EMAIL`
> - `MATRÍCULA`

### ⚠️ Observação:
> As regras RLS **não foram implementadas nesta versão** devido à **ausência de um campo de identificação único por usuário** (ex: e-mail institucional) que permita aplicar o filtro de segurança de forma adequada.

---

## 🧠 Destaques Técnicos

- Colunas calculadas e medidas DAX otimizadas para performance
- Controle de filtros
- Formatação condicional e legibilidade priorizadas
- Layout responsivo e agrupamento temático dos visuais
- Paleta de cores inspirada na identidade visual do Sistema Indústria

---

## 🗂 Arquivos Relacionados

- [`powerbi/Dashboard.pbix`](./Dashboard.pbix): Arquivo original do painel
- [`powerbi/capturas/`](./capturas/): Capturas de tela em PNG
- Exemplo de imagem:
  [Exemplo do Painel](./capturas/Dashboard_01.pdf)

