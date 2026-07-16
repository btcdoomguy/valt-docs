# Metas 🎯

As metas permitem que você defina objetivos financeiros e acompanhe automaticamente seu progresso. Seja para acumular Bitcoin, controlar gastos ou manter uma rotina de DCA, o Valt calcula seu avanço em tempo real.

## O Que São Metas

Metas são objetivos financeiros com prazo definido que o Valt monitora automaticamente. Você define o que quer alcançar e o sistema acompanha suas transações para calcular o progresso.

## Tipos de Meta Disponíveis

O Valt oferece diferentes tipos de meta para diferentes objetivos:

<!-- Source: src/Valt.Core/Modules/Goals/GoalTypeNames.cs + src/Valt.UI/Lang/language.pt-BR.resx -->

## Dados de Cotação e Taxas de Câmbio

Algumas metas dependem de dados de cotação e taxas de câmbio para converter valores entre moedas ou para bitcoin. Quando o valor exibido depende desses dados, o Valt mostra um asterisco (*) ao lado da meta.

<!-- Source: src/Valt.UI/Views/Main/Tabs/Transactions/Models/GoalEntryViewModel.cs + GoalsPanelView.axaml -->

Os seis tipos de meta que dependem de dados de preço são:

- **Renda em Fiat** — converte receitas em diferentes moedas para a moeda principal.
- **Limite de Gastos** — converte gastos em diferentes moedas para a moeda principal.
- **Limite por Categoria** — converte gastos de uma categoria para a moeda principal.
- **Economizar Fiat** — calcula a economia líquida (renda menos despesas) entre moedas.
- **Taxa de Economia** — calcula o percentual de economia a partir de renda e despesas.
- **Patrimônio em BTC** — converte saldos de contas para satoshis usando a cotação do BTC.

O asterisco indica que o valor pode estar temporariamente desatualizado até que a próxima atualização de taxas de câmbio seja aplicada. Passe o mouse sobre o asterisco para ver a seguinte mensagem:

> *Este valor pode estar desatualizado e será atualizado quando as taxas de câmbio diárias estiverem disponíveis.*

<!-- Source: src/Valt.UI/Lang/language.pt-BR.resx Goals_PriceDataTooltip -->

### Metas de Progresso (Acumulação)

Essas metas começam em 0% e aumentam conforme você avança. Ao atingir 100%, a meta é marcada como **concluída**.

<!-- Source: src/Valt.Core/Modules/Goals/ProgressionMode.cs ZeroToSuccess -->

| Tipo | Descrição | Exemplo |
|------|-----------|---------|
| **Stackar Bitcoin** | Define uma quantidade específica para stackar no período selecionado comparado à quantidade anterior | "Stackar 1 milhão de sats a mais este mês" |
| **DCA** | Acompanhe compras regulares de bitcoin (Dollar Cost Averaging) | "Fazer 4 compras de BTC este mês" |
| **Renda em Fiat** | Acompanhe metas de renda na sua moeda principal | "Receber R$ 10.000 este mês" |
| **Renda em Bitcoin** | Acompanhe metas de renda em bitcoin (ex: trabalho, mineração, recompensas) | "Receber 500.000 sats de renda este mês" |
| **Economizar Fiat** | Economizar um valor alvo em fiat (renda menos despesas) | "Economizar R$ 1.000 este mês" |
| **Taxa de Economia** | Economizar um percentual alvo da renda | "Economizar 20% da renda este mês" |
| **Patrimônio em BTC** | Atingir um patrimônio alvo em bitcoin | "Atingir 50.000.000 de sats (0,5 BTC) de patrimônio" |

### Metas de Limite (Controle)

Essas metas também começam em 0%, mas aumentam conforme você se aproxima do limite. Ao atingir 100%, a meta é marcada como **falha**.

<!-- Source: src/Valt.Core/Modules/Goals/ProgressionMode.cs DecreasingSuccess -->

| Tipo | Descrição | Exemplo |
|------|-----------|---------|
| **Limite de Gastos** | Acompanhe seus gastos em relação a um limite de orçamento na sua moeda principal | "Gastar no máximo R$ 3.000 este mês" |
| **Limite por Categoria** | Limite os gastos em uma categoria específica | "Gastar no máximo R$ 500 em delivery" |
| **HODL** | Acompanhe vendas de bitcoin. Defina 0 para modo HODL completo (sem vendas permitidas) | "Vender no máximo 100.000 sats" |

**Patrimônio em BTC** soma todos os saldos de contas visíveis (contas fiat, contas bitcoin, ativos externos e empréstimos BTC) e converte o total para satoshis antes de comparar com o valor alvo. Apenas contas marcadas como visíveis são incluídas no cálculo.

<!-- Source: src/Valt.Core/Modules/Goals/GoalTypes/NetWorthBtcGoalType.cs + NetWorthBtcProgressCalculator.cs -->

!!! note "Economizar Fiat vs Renda em Fiat"
    **Economizar Fiat** acompanha a economia líquida (`renda − despesas`), enquanto **Renda em Fiat** acompanha a renda bruta em direção a um alvo. Use *Economizar Fiat* quando quiser medir quanto sobra no final do mês, e *Renda em Fiat* quando quiser apenas acompanhar uma meta de receita.

## Como Funciona o Progresso

### Metas de Acumulação (Barra Verde)

- Progresso começa em **0%**
- Aumenta conforme você faz transações relacionadas
- Ao atingir **100%**, a meta é automaticamente marcada como **Concluída**
- A barra de progresso é verde

**Exemplo - Stackar Bitcoin:**
```
Meta: Stackar 1.000.000 sats
Progresso atual: 250.000 sats acumulados
Barra de progresso: 25% (verde)
```

### Metas de Limite (Barra Vermelha)

- Progresso começa em **0%** (nada gasto = bom)
- Aumenta conforme você gasta/vende
- Ao atingir **100%**, a meta é automaticamente marcada como **Falha**
- A barra de progresso é vermelha
- Metas de limite de gastos podem ultrapassar 100%

**Exemplo - Limite de Gastos:**
```
Meta: Gastar no máximo R$ 2.000
Progresso atual: R$ 1.000 gastos
Barra de progresso: 50% (vermelho)
```

## Períodos Disponíveis

| Período | Descrição |
|---------|-----------|
| **Mensal** | Meta válida para um mês específico |
| **Anual** | Meta válida para um ano inteiro |

## Criando uma Meta

1. Acesse a aba **Transações**
2. Na seção de **Metas**, clique em **Nova Meta**
3. Selecione o **período** (Mensal ou Anual)
4. Escolha o **mês/ano de referência**
5. Selecione o **tipo de meta**
6. Configure os parâmetros específicos do tipo escolhido
7. Clique em **Salvar**

### Configuração por Tipo

#### Stackar Bitcoin
- **Valor alvo**: Quantidade de satoshis que deseja acumular

#### DCA (Dollar Cost Average)
- **Número de compras**: Quantidade de compras de Bitcoin que deseja fazer

#### Renda em Fiat
- **Valor alvo**: Quanto deseja receber
- **Moeda**: Em qual moeda

#### Renda em Bitcoin
- **Valor alvo**: Quantidade de satoshis que deseja receber como renda

#### Economizar Fiat
- **Valor alvo de economia**: Quanto deseja economizar no período
- **Moeda**: Em qual moeda

#### Taxa de Economia
- **Taxa alvo de economia (%)**: Percentual da renda que deseja economizar

#### Patrimônio em BTC
- **Valor alvo (sats)**: Quantidade de satoshis de patrimônio líquido desejada

#### Limite de Gastos
- **Valor limite**: Quanto pode gastar no máximo
- **Moeda**: Em qual moeda

#### Limite por Categoria
- **Valor limite**: Quanto pode gastar no máximo
- **Categoria**: Qual categoria deseja controlar

#### HODL
- **Limite de venda**: Máximo de satoshis que pode vender (0 = HODL total)

## Estados da Meta

Uma meta pode estar em três estados:

| Estado | Descrição | Exibição |
|--------|-----------|----------|
| **Em Aberto** | Meta ainda em andamento | Barra de progresso |
| **Concluída** | Meta de acumulação atingiu 100% | Badge "SUCESSO" (verde) |
| **Falha** | Meta de limite atingiu 100% | Badge "FALHA" (vermelho) |

## Gerenciando Metas

### Editando

1. Clique na meta desejada
2. Clique em **Editar**
3. Modifique os parâmetros
4. Salve

!!! note "Nota"
    Ao editar uma meta, o progresso calculado é preservado e será recalculado automaticamente.

### Excluindo

1. Clique na meta desejada
2. Clique em **Excluir**
3. Confirme

### Recalculando

Se uma meta foi marcada como **Concluída** ou **Falha**, mas você deseja recalcular:

1. Clique com o botão direito na meta
2. Selecione **Recalcular**
3. A meta volta ao estado **Em Aberto** e o progresso é recalculado com os dados mais recentes

Isso é útil quando você edita transações do passado que afetam a meta, ou quando deseja reavaliar uma meta já concluída com novas transações.

<!-- Source: src/Valt.Core/Modules/Goals/Goal.cs Recalculate() -->

## Cálculo Automático

O Valt recalcula automaticamente o progresso das metas quando transações são criadas, editadas ou excluídas, e quando taxas de câmbio são atualizadas. Quando algo muda, o Valt marca as metas afetadas como desatualizadas e recalcula o progresso em segundo plano.

<!-- Source: src/Valt.Core/Modules/Goals/Goal.cs IsUpToDate + MarkAsStale() + GoalProgressUpdaterJob.cs -->

O asterisco (*) exibido ao lado de algumas metas indica que o valor depende de dados de câmbio e pode estar temporariamente desatualizado. A mensagem do tooltip explica que o valor será atualizado quando as taxas de câmbio diárias estiverem disponíveis. Esse mesmo mecanismo de "desatualização" (ou *staleness*) é o que permite ao Valt saber quais metas precisam ser recalculadas quando novos dados chegam.

<!-- Source: src/Valt.Infra/Modules/Goals/Services/GoalProgressState.cs + GoalProgressUpdaterJob.cs -->

Quando o recálculo termina, as metas de acumulação que atingirem 100% são marcadas como **Concluídas**, e as metas de limite que atingirem 100% são marcadas como **Falha**. Você não precisa fazer nada manualmente; o sistema atualiza os estados automaticamente.

## Visualização

As metas são exibidas na aba de Transações e são organizadas na seguinte ordem:

1. Metas mensais em aberto
2. Metas anuais em aberto
3. Metas concluídas
4. Metas com falha

A barra de progresso é animada, mostrando de forma suave a transição quando o progresso muda.

## Exemplos de Uso 💡

### Estratégia de Acumulação

**Meta Mensal de DCA:**
- **Tipo**: DCA
- **Período**: Mensal
- **Alvo**: 4 compras
- **Objetivo**: Garantir que você faça pelo menos uma compra por semana

**Meta Anual de Acumulação:**
- **Tipo**: Stackar Bitcoin
- **Período**: Anual
- **Alvo**: 10.000.000 sats (0,1 BTC)
- **Objetivo**: Acumular um valor significativo ao longo do ano

### Controle de Gastos

**Orçamento Mensal:**
- **Tipo**: Limite de Gastos
- **Período**: Mensal
- **Limite**: R$ 5.000
- **Objetivo**: Não ultrapassar seu orçamento mensal

**Controle de Categoria:**
- **Tipo**: Limite por Categoria
- **Período**: Mensal
- **Categoria**: Alimentação > Delivery
- **Limite**: R$ 400
- **Objetivo**: Reduzir gastos com delivery

### Preservação de Bitcoin

**HODL Total:**
- **Tipo**: HODL
- **Período**: Anual
- **Limite de venda**: 0 sats
- **Objetivo**: Não vender nenhum Bitcoin durante o ano (qualquer venda marcará a meta como falha)

**HODL Parcial:**
- **Tipo**: HODL
- **Período**: Mensal
- **Limite de venda**: 500.000 sats
- **Objetivo**: Limitar vendas emergenciais

### Economizar Fiat

**Meta Mensal de Economia:**
- **Tipo**: Economizar Fiat
- **Período**: Mensal
- **Alvo**: R$ 1.000
- **Objetivo**: Acompanhar quanto de renda líquida sobra após despesas no mês
- **Progresso**: Se a renda for R$ 5.000 e as despesas R$ 4.200, a economia será R$ 800 → 80% de progresso

!!! note "Economizar Fiat vs Renda em Fiat"
    **Economizar Fiat** acompanha a economia líquida (`renda menos despesas`), enquanto **Renda em Fiat** acompanha a renda bruta em direção a um alvo. Use *Economizar Fiat* para medir o que sobra no final do mês e *Renda em Fiat* para acompanhar apenas uma meta de receita.

### Taxa de Economia

**Meta Mensal de Taxa de Economia:**
- **Tipo**: Taxa de Economia
- **Período**: Mensal
- **Alvo**: 20%
- **Objetivo**: Economizar pelo menos 20% da renda no mês
- **Progresso**: Se a renda for R$ 5.000 e as despesas R$ 4.000, a taxa de economia é 20% → 100% de progresso (Concluída)

### Patrimônio em BTC

**Meta Anual de Patrimônio:**
- **Tipo**: Patrimônio em BTC
- **Período**: Anual
- **Alvo**: 50.000.000 sats (0,5 BTC)
- **Objetivo**: Atingir um patrimônio líquido total de 0,5 BTC em todas as contas
- **Progresso**: O Valt soma todos os saldos de contas visíveis (fiat, bitcoin, ativos, empréstimos) em satoshis; se o total for 45.000.000 sats → 90% de progresso

## Boas Práticas ✨

### Defina Metas Realistas

- Comece com metas alcançáveis
- Aumente gradualmente conforme você ganha confiança
- Use o histórico de metas para calibrar suas expectativas

### Combine Diferentes Tipos

- Use metas de acumulação para objetivos de longo prazo
- Use metas de limite para controle do dia a dia
- Crie metas mensais e anuais complementares

### Revise Periodicamente

- No início de cada mês, crie suas metas mensais
- No início do ano, defina metas anuais
- Analise metas passadas para aprender com seu histórico

### Use Categorias a Seu Favor

Para metas do tipo "Limite por Categoria":
- Crie categorias específicas para gastos que deseja controlar
- Exemplo: Crie "Lazer > Delivery" para monitorar pedidos de comida

## Próximos Passos

- [Transações](transacoes.md) - Como funcionam as transações
- [Categorias](categorias.md) - Organizando despesas
- [Relatórios](relatorios.md) - Analisando gastos
