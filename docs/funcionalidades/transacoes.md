# Transações

As transações são o coração do Valt. Cada movimentação financeira é registrada como uma transação, permitindo que você tenha controle total sobre suas finanças.

## Tipos de Transações

O Valt oferece seis tipos de transações para cobrir todos os cenários possíveis:

| Tipo | Descrição | Exemplo |
|------|-----------|---------|
| **Fiat** | Entrada ou saída em conta fiat | Salário, compras, contas |
| **Bitcoin** | Entrada ou saída em conta Bitcoin | Mining, doações |
| **Fiat para Fiat** | Transferência entre contas fiat | TED, PIX entre bancos |
| **Bitcoin para Bitcoin** | Transferência entre wallets | Da corretora para Ledger |
| **Fiat para Bitcoin** | Compra de Bitcoin | Compra na Binance |
| **Bitcoin para Fiat** | Venda de Bitcoin | Venda no Mercado Bitcoin |

## Transação Fiat

### Quando Usar

Use para qualquer entrada ou saída de dinheiro em moeda tradicional:

**Receitas (entradas)**:
- Salário
- Pagamento de freelance
- Reembolsos
- Dividendos
- Vendas

**Despesas (saídas)**:
- Compras no supermercado
- Contas de luz, água, internet
- Assinaturas (Netflix, Spotify)
- Restaurantes
- Transporte

### Como Lançar

1. Clique em **Nova Transação**
2. Selecione **Transação Fiat**
3. Preencha:

| Campo | Descrição |
|-------|-----------|
| **Data** | Quando ocorreu |
| **Tipo** | Receita ou Despesa |
| **Conta** | Qual conta foi afetada |
| **Valor** | Quanto foi |
| **Categoria** | Classificação do gasto/receita |
| **Descrição** | (Opcional) Detalhes |

4. Clique em **Salvar**

!!! tip "Calculadora Integrada"
    No campo valor, você pode digitar expressões matemáticas como `150+35.50` e o Valt calculará automaticamente.

## Transação Bitcoin

### Quando Usar

Use para entradas ou saídas de Bitcoin que não envolvem troca por moeda fiat:

**Receitas**:
- Mineração
- Airdrops
- Presentes recebidos em BTC
- Pagamentos em Bitcoin

**Despesas**:
- Doações em Bitcoin
- Presentes dados em BTC
- Compras pagas diretamente em Bitcoin

### Como Lançar

1. Clique em **Nova Transação**
2. Selecione **Transação Bitcoin**
3. Preencha:

| Campo | Descrição |
|-------|-----------|
| **Data** | Quando ocorreu |
| **Tipo** | Receita ou Despesa |
| **Conta Bitcoin** | Qual wallet |
| **Valor** | Quantidade em sats ou BTC |
| **Categoria** | Classificação |
| **Descrição** | (Opcional) Detalhes |

4. Clique em **Salvar**

## Fiat para Fiat

### Quando Usar

Use para transferências entre suas contas em moeda fiat:

- PIX de um banco para outro
- TED/DOC
- Transferência para conta de terceiros (que você controla)
- Câmbio de moedas (Real para Dólar)
- Saque do banco para carteira física

### Como Lançar

1. Clique em **Nova Transação**
2. Selecione **Fiat para Fiat**
3. Preencha:

| Campo | Descrição |
|-------|-----------|
| **Data** | Quando ocorreu |
| **Conta Origem** | De onde saiu o dinheiro |
| **Valor Origem** | Quanto saiu |
| **Conta Destino** | Para onde foi |
| **Valor Destino** | Quanto chegou |
| **Descrição** | (Opcional) Detalhes |

4. Clique em **Salvar**

!!! info "Valores Diferentes"
    Os valores podem ser diferentes na origem e destino (ex: câmbio de moedas ou taxas de transferência).

## Bitcoin para Bitcoin

### Quando Usar

Use para transferências entre suas wallets Bitcoin:

- Da corretora para hardware wallet
- Entre hardware wallets diferentes
- Para Lightning Network
- Consolidação de UTXOs

### Como Lançar

1. Clique em **Nova Transação**
2. Selecione **Bitcoin para Bitcoin**
3. Preencha:

| Campo | Descrição |
|-------|-----------|
| **Data** | Quando ocorreu |
| **Conta Origem** | Wallet de saída |
| **Valor Origem** | Quantidade enviada |
| **Conta Destino** | Wallet de destino |
| **Valor Destino** | Quantidade recebida |
| **Descrição** | (Opcional) Detalhes |

4. Clique em **Salvar**

## Fiat para Bitcoin (Compra)

### Quando Usar

Use quando você compra Bitcoin:

- Compra em corretora (Binance, Mercado Bitcoin, Foxbit)
- Compra P2P
- Compra em ATM de Bitcoin
- Qualquer aquisição de BTC com moeda fiat

### Como Lançar

1. Clique em **Nova Transação**
2. Selecione **Fiat para Bitcoin**
3. Preencha:

| Campo | Descrição |
|-------|-----------|
| **Data** | Quando comprou |
| **Conta Fiat** | De onde saiu o dinheiro |
| **Valor Fiat** | Quanto pagou |
| **Conta Bitcoin** | Para onde foram os bitcoins |
| **Valor Bitcoin** | Quantos sats/BTC recebeu |
| **Descrição** | (Opcional) Corretora, taxa, etc. |

4. Clique em **Salvar**

## Bitcoin para Fiat (Venda)

### Quando Usar

Use quando você vende Bitcoin:

- Venda em corretora
- Venda P2P
- Qualquer conversão de BTC para moeda fiat

### Como Lançar

1. Clique em **Nova Transação**
2. Selecione **Bitcoin para Fiat**
3. Preencha:

| Campo | Descrição |
|-------|-----------|
| **Data** | Quando vendeu |
| **Conta Bitcoin** | De onde saíram os bitcoins |
| **Valor Bitcoin** | Quantos sats/BTC vendeu |
| **Conta Fiat** | Para onde foi o dinheiro |
| **Valor Fiat** | Quanto recebeu |
| **Descrição** | (Opcional) Detalhes |

4. Clique em **Salvar**

## Cálculo automático do valor em satoshis

### O Que É

O campo Sats é uma funcionalidade que calcula automaticamente quanto uma transação fiat representava em satoshis na data em que ocorreu.

### Como Funciona

1. Você lança uma transação fiat (ex: despesa de R$ 200)
2. O Valt busca a cotação do Bitcoin na data da transação
3. Calcula quantos satoshis R$ 200 compravam naquele dia
4. Armazena esse valor junto com a transação

!!! info "Em que momento o valor é calculado"?
    O Valt precisa obter a cotação de fechamento do Bitcoin na data do lançamento para poder realizar esse cálculo. Portanto quando você lança suas transações do dia atual esse valor sempre aparece vazio. Não se preocupe, no dia seguinte o sistema irá calcular automaticamente.

### Benefício

Isso permite que você veja o **custo de oportunidade** de cada gasto:

- Um almoço de R$ 50 em 2020 poderia ser 100.000 sats
- Hoje, esses 100.000 sats valem R$ 500
- Você "gastou" muito mais do que R$ 50 em termos de Bitcoin

## Editando Transações

1. Na lista de transações, clique na transação desejada
2. Clique no ícone de edição
3. Modifique os campos necessários
4. Clique em **Salvar**

## Excluindo Transações

1. Clique na transação
2. Clique no ícone de exclusão (lixeira)
3. Confirme a exclusão

!!! warning "Atenção"
    A exclusão não pode ser desfeita.

## Filtros e Busca

### Filtrar por Data

Use o seletor de período para ver transações de:
- Este mês
- Mês anterior
- Este ano
- Tudo

### Filtrar por Conta

Clique em uma conta para ver apenas as transações dela.

Caso você queira ver todas as contas ao mesmo tempo, clique em **Ver todas as contas**

### Buscar

Use a barra de busca para encontrar transações por:
- Descrição
- Categoria
- Valor

## Boas Práticas

### Consistência

- Lance transações regularmente (diária ou semanalmente)
- Mantenha descrições padronizadas
- Use categorias consistentemente

### Detalhamento

- Para gastos grandes, adicione descrições detalhadas
- Inclua informações úteis como parcelamento, etc.

### Verificação

- Compare periodicamente o saldo do Valt com o saldo real das suas contas
- Ajuste se necessário

## Próximos Passos

- [Categorias](categorias.md) - Organize suas transações
- [Despesas Fixas](despesas-fixas.md) - Gastos recorrentes
- [Relatórios](relatorios.md) - Análise das suas transações
