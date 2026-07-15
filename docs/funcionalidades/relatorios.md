# Relatórios 📊

A aba de **Relatórios** mostra uma visão consolidada do seu patrimônio, stack de BTC, análises de renda e gastos, além de indicadores de mercado. Todos os valores podem ser visualizados na moeda fiat principal ou sob uma simulação de preço de BTC.

<!-- Source: src/Valt.UI/Views/Main/Tabs/Reports/ReportsView.axaml lines 31-159 + language.pt-BR.resx -->
## Visão Geral

A aba de **Relatórios** tem quatro áreas principais:

1. **Resumo** — painéis com **Patrimônio**, **Sua máxima histórica**, **Seu stack**, **Estatísticas**, **Indicadores**, **Preços Simulados**, **Posições Alavancadas** (quando houver dados) e **Empréstimos BTC** (quando houver dados).
2. **Visão Geral de Patrimônio** — gráfico de linha do patrimônio ao longo do tempo.
3. **Totais por mês** — gráfico de linha e tabela detalhada por mês.
4. **Por categorias** — gráficos de barras horizontais de **Gastos** e **Receitas**, com filtros por contas e categorias.

!!! note "Modo Seguro"
    Quando o **Modo Seguro** está ativado, a aba Relatórios mostra apenas a mensagem *Saia do Modo Seguro para ver os dados*. Nenhum gráfico, painel ou dado é exibido.

<!-- Source: src/Valt.UI/Views/Main/Tabs/Reports/ReportsView.axaml lines 40-74 + FixedPriceConfigViewModel.cs -->
## Simulação de Preço de BTC

No topo da seção **Resumo**, a barra de **Simulação de Preço BTC** mostra o preço atual do BTC e os controles de simulação.

### Como usar

1. Clique em **Simular**.
2. No modal **Preço Customizado de BTC**, insira um preço na sua moeda principal.
3. Clique em **Simular** novamente.
4. Uma badge **SIMULAÇÃO** aparece. Os painéis **Patrimônio**, **Seu stack**, **Preços Simulados**, **Posições Alavancadas** e **Empréstimos BTC** recalculam com o preço simulado.
5. Clique em **Resetar** para voltar ao preço ao vivo.

### Validação

- O campo de preço é obrigatório.
- O valor deve ser um decimal válido.
- O valor deve ser não negativo.
- As mensagens de erro são *O preço é obrigatório* e *O preço deve ser não negativo*.

!!! note "O que não é afetado"
    O preço customizado não altera dados históricos. **Máxima histórica**, **Estatísticas**, **Indicadores**, **Visão Geral de Patrimônio**, **Totais por mês** e **Por categorias** continuam usando dados ao vivo ou históricos.

### Relação com o painel Preços Simulados

A barra de preço fixo é uma substituição global do preço ao vivo do BTC. O painel **Preços Simulados** é uma lista separada de até 6 cenários (porcentagem do preço atual ou preço fixo em USD). Quando o preço customizado está ativo, o painel **Preços Simulados** continua mostrando os cenários configurados, mas o preço base passa a ser o preço customizado, não o preço ao vivo. A configuração é aberta pelo ícone de engrenagem do painel, no modal **Configuração de Preços Simulados**. Cada linha pode ser **Porcentagem** ou **Preço Fixo**, com porcentagem mínima de 5%.

<!-- Source: src/Valt.UI/Views/Main/Tabs/Reports/ReportsView.axaml lines 76-159 + Panels/*.cs + language.pt-BR.resx -->
## Painéis do Resumo

A seção **Resumo** exibe até oito painéis. Cada painel mostra título, ícone e linhas de rótulo e valor. Os painéis **Posições Alavancadas** e **Empréstimos BTC** só aparecem quando você tem os dados correspondentes.

!!! info "Visibilidade condicional"
    O painel **Posições Alavancadas** só aparece quando você tem pelo menos uma posição alavancada visível incluída no patrimônio líquido. O painel **Empréstimos BTC** só aparece quando você tem pelo menos um empréstimo BTC ativo.

### Patrimônio

Título: **Patrimônio**

| Rótulo | Valor |
|--------|-------|
| **Total (as BTC)** | Patrimônio total representado em BTC |
| **Total (as Fiat)** | Patrimônio total na moeda fiat principal |
| **Meu Stack** | Stack de BTC em BTC |
| **Meu Outro** | Patrimônio não-BTC na moeda fiat principal |
| **Total (em USD)** | Patrimônio total em USD (somente quando a moeda principal não é USD) |
| **Meus Ativos** | Valor de ativos externos na moeda fiat principal |
| **% à Vista em BTC** | Percentual do patrimônio total em BTC spot |

!!! tip "Dica sobre o primeiro campo"
    Esse é o seu patrimônio total representado em bitcoin como unidade de conta.

### Sua máxima histórica

Título: **Sua máxima histórica**

| Rótulo | Valor |
|--------|-------|
| **Máxima histórica** | Maior valor que o patrimônio já atingiu |
| **Data** | Data em que ocorreu a máxima histórica |
| **Diferença atual** | Percentual de queda em relação à máxima histórica |
| **Maior queda** | Percentual máximo de queda (drawdown), quando disponível |
| **Data da maior queda** | Data da maior queda, quando disponível |
| **Preço do BTC p/ bater ATH** | Preço do BTC necessário para atingir a máxima histórica novamente, quando positivo |

### Seu stack

Título: **Seu stack**

| Rótulo | Valor |
|--------|-------|
| **Stack atual** | Stack atual de BTC |
| **% do supply total** | Stack como percentual do supply total de 21.000.000 BTC |
| **Ranking global** | Estimativa do número máximo de pessoas que podem ter o mesmo stack |
| **Stack máximo** | Maior stack de BTC já registrado, quando disponível |
| **Data do stack máximo** | Data do maior stack, quando disponível |
| **Queda do máximo** | Percentual de queda em relação ao stack máximo, quando disponível |

!!! tip "Dica sobre Ranking global"
    Quantidade máxima de pessoas que podem ter o mesmo stack que você.

### Estatísticas

Título: **Estatísticas**

| Rótulo | Valor |
|--------|-------|
| **Despesas medianas (12m)** | Mediana mensal de despesas nos últimos 12 meses |
| **Despesas medianas (12m ant)** | Mediana mensal de despesas nos 12 meses anteriores, quando disponível |
| **Evolução anual** | Variação ano a ano da mediana de despesas em fiat, quando disponível |
| **Mediana sats (12m)** | Mediana mensal de despesas em satoshis, quando disponível |
| **Mediana sats (12m ant)** | Mediana anterior em satoshis, quando disponível |
| **Evolução anual (sats)** | Variação ano a ano da mediana de despesas em satoshis, quando disponível |
| **Cobertura do patrimônio** | Quantos meses o patrimônio atual cobre as despesas |

!!! tip "Dica sobre Cobertura do patrimônio"
    Tempo que você consegue se sustentar com o patrimônio atual sem novas entradas.

O painel possui um ícone de engrenagem que abre a configuração para excluir categorias do cálculo da mediana de despesas.

### Indicadores

Título: **Indicadores**

| Rótulo | Valor |
|--------|-------|
| **Mayer Multiple** | Múltiplo de Mayer do mercado de BTC |
| **Rainbow Chart** | Zona atual do gráfico arco-íris |
| **Medo & Ganância** | Índice de medo e ganância do mercado cripto |
| **Dominância BTC** | Percentual de dominância do BTC no mercado cripto |

Os indicadores podem aparecer como desatualizados se os dados não tiverem sido atualizados recentemente.

### Preços Simulados

Título: **Preços Simulados**

Cada linha mostra um cenário configurado: o preço simulado de BTC e o patrimônio total projetado na moeda fiat principal. O painel possui um ícone de engrenagem que abre a configuração de até 6 linhas, sendo cada uma **Porcentagem** ou **Preço Fixo**.

### Posições Alavancadas

Título: **Posições Alavancadas**

| Rótulo | Valor |
|--------|-------|
| **Stack Alavancado** | BTC spot + exposição efetiva de BTC em posições alavancadas |
| **Exposição de Alavancagem** | Exposição líquida de BTC das posições alavancadas (positiva para comprada, negativa para vendida) |
| **% de Alavancagem** | Percentual do stack alavancado que vem de alavancagem |
| **Posições Ativas** | Número de posições alavancadas ativas |
| **Resultado atual** | Resultado total (P&L) na moeda fiat principal |
| **Resultado atual (BTC)** | Resultado total em BTC |
| **Preço BTC para atingir ATH** | Preço do BTC necessário para atingir a máxima histórica com o stack alavancado, quando disponível |

### Empréstimos BTC

Título: **Empréstimos BTC**

| Rótulo | Valor |
|--------|-------|
| **Empr. ativos** | Número de empréstimos ativos |
| **Dívida total** | Dívida total na moeda fiat principal |
| **Dívida total (BTC)** | Dívida total em BTC |
| **Total emprestado** | Principal total emprestado na moeda fiat principal |
| **LTV médio** | Média de LTV ponderada pela dívida |
| **APR médio** | Média de APR ponderada pela dívida |
| **Colateral total** | Colateral total em BTC |
| **Colateral (fiat)** | Colateral total na moeda fiat principal |
| **% do stack travado** | Colateral como percentual do stack total de BTC |
| **BTC livre** | Stack de BTC não comprometido como colateral |
| **Saúde dos empr.** | Contagem de empréstimos saudáveis / em alerta / em risco |
| **Maior LTV** | Maior LTV entre todos os empréstimos |
| **Próximo da liq.** | Menor distância em LTV até a liquidação |
| **Preço de liq. (pior caso)** | Maior preço do BTC em que algum empréstimo ainda estaria em risco |
| **Juros acumulados** | Juros acumulados na moeda fiat principal |
| **Taxas pagas** | Taxas pagas na moeda fiat principal |
| **Idade média** | Idade média dos empréstimos em dias |
| **Próximo vencimento** | Próxima data de vencimento e dias restantes, quando disponível |

<!-- Source: src/Valt.UI/Views/Main/Tabs/Reports/ReportsView.axaml lines 163-219 + language.pt-BR.resx -->
## Visão Geral de Patrimônio

A seção **Visão Geral de Patrimônio** mostra um gráfico de linha do patrimônio ao longo do tempo.

### Controles

- **Seletor de período**: **Diário**, **Semanal**, **Mensal** ou **Anual**.
- **Máximo de elementos**: escolha entre **12**, **18** ou **24** pontos no gráfico.

### Gráfico

O gráfico de linha mostra três séries:

- **Patrimônio total** — valor total acumulado.
- **Bitcoin** — patrimônio denominado em BTC.
- **Fiat** — patrimônio em moeda fiat principal.

!!! note "Ativos não incluídos"
    *não inclui Ativos* — o gráfico não inclui o valor de ativos externos cadastrados na aba **Ativos**.

<!-- Source: src/Valt.UI/Views/Main/Tabs/Reports/ReportsView.axaml lines 221-377 + language.pt-BR.resx -->
## Totais por mês

A seção **Totais por mês** combina um gráfico de linha e uma tabela detalhada por mês.

### Controles

- **Seletor de data**: escolha **Ano** ou **Tudo**.

### Gráfico de linha

Mostra as tendências de patrimônio em fiat e em BTC ao longo do período selecionado.

### Tabela de dados

| Coluna | Descrição |
|--------|-----------|
| **Data** | Mês/ano da linha |
| **Bitcoin** | Total em BTC |
| **% do último mês** | Variação percentual em relação ao mês anterior (BTC) |
| **% do último ano** | Variação percentual em relação ao ano anterior (BTC) |
| **Patrimônio total** | Patrimônio total na moeda fiat principal |
| **% do último mês** | Variação percentual em relação ao mês anterior (fiat) |
| **% do último ano** | Variação percentual em relação ao ano anterior (fiat) |
| **Todas as entradas em fiat** | Total de receitas em fiat (incluindo conversões) |
| **Todas as saídas em fiat** | Total de despesas em fiat (incluindo conversões) |
| **Entradas (Fiat)** | Receitas em fiat |
| **Saídas (Fiat)** | Despesas em fiat |
| **BTC Comprados** | Quantidade de BTC comprados no mês |
| **BTC Vendidos** | Quantidade de BTC vendidos no mês |
| **Entradas em BTC** | Receitas em BTC |
| **Saídas em BTC** | Despesas em BTC |

!!! note "Observações"
    *o total atual é baseado nos valores do dia anterior*  
    *não inclui Ativos*

<!-- Source: src/Valt.UI/Views/Main/Tabs/Reports/ReportsView.axaml lines 379-526 + language.pt-BR.resx -->
## Por categorias

A seção **Por categorias** mostra dois gráficos de barras horizontais: um de **Gastos** e outro de **Receitas**.

### Controles

- **Seletor de data**: escolha **Mês**, **Ano** ou **Tudo**.
- **Filtros**: painel à esquerda com multi-seleção de **Contas** e **Categorias**.
- **Ícone de engrenagem**: salva o filtro atual como padrão ou carrega o filtro padrão salvo.

### Gráficos

- **Gastos** — barras horizontais com as categorias de maior despesa.
- **Receitas** — barras horizontais com as categorias de maior receita.

Use os filtros para incluir ou excluir contas e categorias, e para focar em grupos específicos de transações.

<!-- Source: ReportsView.axaml + ReportsViewModel.cs + CsvExportService.cs -->
## Exportação

!!! note "Sem exportação de relatórios"
    A aba **Relatórios** não possui funcionalidade de exportação. Para exportar seus dados de transações, use **Exportar Transações...** no menu principal. Também é possível exportar linhas de preço-médio a partir da aba **Preço-médio**.

<!-- Source: ReportsView.axaml + language.pt-BR.resx -->
## Dicas de Uso 💡

### Revisão mensal

Faça uma revisão mensal dos seus relatórios:

1. Verifique os painéis do **Resumo**.
2. Analise a **Visão Geral de Patrimônio**.
3. Olhe os **Totais por mês** e compare com meses anteriores.
4. Use **Por categorias** para identificar desvios nos gastos e receitas.

### Use a simulação de preço para planejamento

Teste diferentes preços de BTC para ver como seu patrimônio, stack e posições alavancadas reagem. Isso ajuda a planejar cenários de alta e de queda sem alterar dados reais.

### Visualize em satoshis

Observar tudo em satoshis dá uma perspectiva diferente:

- Gastos parecem maiores (custo de oportunidade).
- Aumenta a motivação para economizar.
- Fortalece a visão de longo prazo.

### Modo Seguro

Quando o **Modo Seguro** está ativado, todos os dados da aba Relatórios ficam ocultos. Saia do Modo Seguro para visualizar os gráficos e painéis.

## Próximos Passos

- [Conceitos Básicos](../guia/conceitos-basicos.md) - Entenda a filosofia do Valt
- [Transações](transacoes.md) - Melhore a qualidade dos dados
- [Categorias](categorias.md) - Organize melhor seus gastos
