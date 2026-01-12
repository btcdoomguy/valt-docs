# Contas 🏦

As contas são a base do Valt. Elas representam todos os lugares onde você mantém dinheiro, seja em moeda fiat ou Bitcoin.

## Visão Geral

O Valt trabalha com dois tipos de contas:

- **Contas Fiat**: Para moedas tradicionais (Real, Dólar, Euro, etc.)
- **Contas Bitcoin**: Para armazenar saldos em satoshis

Cada transação no Valt está associada a pelo menos uma conta.

## Contas Fiat 💵

### O Que São

Contas fiat representam onde você mantém dinheiro em moeda tradicional:

- Bancos (Nubank, Itaú, Bradesco, Santander, etc.)
- Fintechs (PicPay, Mercado Pago, PagBank, etc.)
- Corretoras (saldo em reais)
- Dinheiro físico (carteira, cofre)
- Cartões de crédito (para controle de gastos)

### Criando uma Conta Fiat

1. Na aba **Transações**, clique no botão **+** na seção de contas
2. Selecione **Conta Fiat**
3. Preencha os campos:

| Campo | Descrição |
|-------|-----------|
| **Nome** | Identificação da conta (ex: "Nubank", "Carteira") |
| **Moeda** | A moeda da conta (Real, Dólar, etc.) |
| **Saldo Inicial** | Valor inicial da conta (opcional) |
| **Ícone** | Ícone visual para identificação |
| **Cor** | Cor associada à conta |

4. Clique em **Salvar**

### Moedas Suportadas

O Valt suporta mais de 32 moedas fiat diferentes e a lista continua aumentando. Veja a lista completa em [Moedas Suportadas](../referencia/moedas.md).

As mais comuns são:

- BRL (Real Brasileiro)
- USD (Dólar Americano)
- EUR (Euro)

## Contas Bitcoin ₿

### O Que São

Contas Bitcoin representam onde você guarda seus bitcoins:

- Hardware wallets
- Software wallets (Electrum, Blue Wallet, Sparrow)
- Corretoras
- Custódia institucional
- Lightning Network wallets

### Criando uma Conta Bitcoin

1. Na aba **Transações**, clique no botão **+** na seção de contas
2. Selecione **Conta Bitcoin**
3. Preencha os campos:

| Campo | Descrição |
|-------|-----------|
| **Nome** | Identificação da wallet (ex: "Ledger", "Binance") |
| **Saldo Inicial** | Valor inicial em satoshis ou BTC (opcional) |
| **Ícone** | Ícone visual para identificação |
| **Cor** | Cor associada à conta |

4. Clique em **Salvar**

!!! tip "Satoshis vs BTC"
    Ao informar o saldo inicial, você pode digitar em BTC (ex: 0.001) ou em satoshis (ex: 100000). O Valt armazena internamente tudo em satoshis para máxima precisão.

## Gerenciando Contas ⚙️

### Editando uma Conta

1. Clique na conta que deseja editar
2. Clique no ícone de edição (lápis)
3. Modifique os campos desejados
4. Clique em **Salvar**

### Ocultando uma Conta

Se você não quer mais ver uma conta (mas quer manter o histórico):

1. Edite a conta
2. Desmarque a opção **Visível**
3. Salve

A conta não aparecerá na lista principal, mas as transações são mantidas.

### Ordenando Contas

Você pode mover as contas para reordená-las da forma que preferir através do botão direito do mouse e as opções Mover pra Cima ou Mover pra Baixo, ou segure Ctrl e utilize as setas do teclado para mover a conta. A ordem é salva automaticamente.

### Excluindo uma Conta

!!! warning "Atenção"
    Excluir uma conta só é permitido caso não exista nenhuma transação registrada. Se você não utiliza mais a conta, apenas remova a visibilidade dela na lista.

Para excluir:

1. Edite a conta
2. Clique em **Excluir**
3. Confirme a exclusão

## Selecionando Ícones

O Valt oferece uma biblioteca de ícones para personalizar suas contas:

1. Ao criar ou editar uma conta, clique no campo **Ícone**
2. Uma janela com ícones disponíveis será aberta
3. Use a busca para encontrar ícones específicos (ex: "bank", "wallet", "bitcoin")
4. Clique no ícone desejado
5. Escolha uma cor para o ícone

## Saldo das Contas

### Visualização do Saldo

O saldo de cada conta é exibido:

1. Na lista de contas (coluna de saldo)
2. No resumo total do patrimônio
3. Convertido para satoshis (para análise em Bitcoin)

## Patrimônio Total 💰

Na parte superior da seção de contas, você verá o **Patrimônio Total**, que soma:

- Todas as contas fiat (convertidas para sua moeda principal)
- Todas as contas Bitcoin (convertidas para sua moeda principal)
- Total geral em moeda fiat e em satoshis

Isso dá uma visão completa de quanto você possui.

## Boas Práticas ✨

### Organização

1. **Uma conta por instituição**: Crie contas separadas para cada banco/wallet
2. **Nomes claros**: Use nomes que você reconheça facilmente
3. **Ícones consistentes**: Use ícones que representem a instituição
4. **Agrupe por tipo**: Mantenha bancos juntos, wallets juntas

### Quando Usar Saldo Inicial

Use saldo inicial quando:

- Você está começando a usar o Valt e já tem dinheiro nas contas
- Não quer (ou não consegue) lançar todo o histórico de transações

O saldo inicial é considerado como "ponto de partida" para os cálculos.

## Relacionamento com Outras Funcionalidades

### Transações

Toda transação está ligada a pelo menos uma conta:

- Receitas e despesas: uma conta
- Transferências: duas contas
- Compras/vendas de Bitcoin: uma conta fiat + uma conta Bitcoin

### Despesas Fixas

Despesas fixas podem ser vinculadas a uma conta específica, facilitando o lançamento.

### Relatórios

Os relatórios consideram todas as contas visíveis para calcular totais e gerar gráficos.

## Próximos Passos

- [Transações](transacoes.md) - Como lançar movimentações
- [Despesas Fixas](despesas-fixas.md) - Gastos recorrentes
- [Relatórios](relatorios.md) - Análise do seu patrimônio
