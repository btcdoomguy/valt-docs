# Conceitos Básicos 📚

Este guia explica os conceitos fundamentais do Valt e como ele difere de aplicativos financeiros tradicionais.

## Bitcoin como Unidade de Conta ₿

O diferencial do Valt é mostrar todas as suas finanças através da perspectiva do Bitcoin. Mas o que isso significa na prática?

### O Problema da Inflação

Quando você olha para uma transação de 5 anos atrás e vê "R$ 1.000", esse valor não representa o mesmo poder de compra de hoje. A inflação corrói o valor do dinheiro ao longo do tempo. Moedas fiduciárias foram projetadas para escravizarem a população, drenando o valor do trabalho de quem produz e redirecionando para o bolso dos parasitas e vagabundos.

### A Solução do Valt

O Valt converte automaticamente todas as suas transações para **satoshis** (a menor unidade do Bitcoin: 1 BTC = 100.000.000 satoshis) usando a cotação do dia da transação.

Isso permite que você:

- Compare gastos de diferentes épocas de forma justa
- Entenda o custo de oportunidade das suas decisões
- Veja seu patrimônio em uma unidade monetária deflacionária

### Exemplo Prático

Você comprou um celular em janeiro de 2020 por R$ 3.000.

- Na época, 1 BTC valia R$ 30.000
- Portanto, o celular custou 0.1 BTC (ou 10.000.000 satoshis)
- Se hoje 1 BTC vale R$ 300.000, esses 10.000.000 sats valeriam R$ 30.000

O Valt mostra essa realidade: seu celular não custou "apenas" R$ 3.000, ele custou o equivalente a R$ 30.000 em poder de compra futuro.

## Tipos de Contas 🏦

O Valt trabalha com dois tipos fundamentais de contas:

### Contas Fiat

Representam dinheiro em moeda tradicional:

- Contas bancárias (Nubank, Itaú, Bradesco, etc.)
- Carteiras digitais (PicPay, Mercado Pago, etc.)
- Dinheiro em espécie
- Corretoras (saldo em reais)

Cada conta fiat tem uma **moeda associada** (Real, Dólar, Euro, etc.). O Valt suporta 32 moedas diferentes.

### Contas Bitcoin

Representam onde você guarda seus bitcoins:

- Hardware wallets (Ledger, Trezor, Coldcard)
- Software wallets (Electrum, Blue Wallet, etc.)
- Corretoras (saldo em BTC)
- Custódia de terceiros

Os valores são armazenados em **satoshis** para máxima precisão.

## Tipos de Transações 💱

O Valt oferece seis tipos de transações para cobrir todos os cenários:

### 1. Transação Fiat

Uma entrada ou saída simples em uma conta fiat.

- **Receita**: Salário, vendas, reembolsos
- **Despesa**: Compras, contas, pagamentos

### 2. Transação Bitcoin

Uma entrada ou saída simples em uma conta Bitcoin.

- **Receita**: Mining, airdrops, presentes recebidos
- **Despesa**: Doações, presentes dados

### 3. Fiat para Fiat

Transferência entre duas contas fiat.

- Transferência entre bancos
- Câmbio de moedas (Real para Dólar)
- Saque do banco para carteira

### 4. Bitcoin para Bitcoin

Transferência entre duas contas Bitcoin.

- Movimentação entre wallets
- Da corretora para hardware wallet

### 5. Fiat para Bitcoin

Compra de Bitcoin.

- Compra em corretora
- Compra P2P
- Qualquer aquisição de BTC com moeda fiat

### 6. Bitcoin para Fiat

Venda de Bitcoin.

- Venda em corretora
- Venda P2P
- Qualquer conversão de BTC para moeda fiat

## Sats / Valor Atual em Sats ⚡

Todas as transações fiduciárias no Valt recebem também o valor relativo em sats de acordo com o fechamento daquela data, bem como uma coluna que demonstra o preço atual daquela quantidade de sats no preço atual.

Com isso, você consegue observar o custo de oportunidade de todas as suas transações passadas.

### Como Funciona

Quando você lança uma transação em moeda fiat, o Valt automaticamente:

1. Busca a cotação do Bitcoin na data da transação
2. Calcula quantos satoshis aquele valor representava
3. Armazena esse valor junto com a transação

Caso a transação seja registrada na data atual ou em data futura, a coluna Sats só será preenchida após o fechamento do mercado.

### Por Que Isso Importa

Isso permite que você veja o **custo de oportunidade** de cada gasto. Por exemplo:

- Um jantar de R$ 200 em 2020 = 200.000 sats
- Hoje, esses 200.000 sats valem R$ 2.000

O Valt não está dizendo que você não deveria ter jantado. Está mostrando uma perspectiva diferente sobre o valor do dinheiro ao longo do tempo.

## Preço Médio de Aquisição 📊

Para quem investe em Bitcoin, saber o **preço médio** de compra é essencial, tanto para facilitar operações fiscais quanto para saber sua evolução patrimonial.

### O Que É

O preço médio é o custo médio de aquisição dos seus bitcoins, considerando todas as compras que você fez ao longo do tempo.

### Métodos de Cálculo

O Valt oferece dois métodos:

#### Regra Brasileira

O preço médio é recalculado a cada nova compra, considerando o estoque anterior e a nova aquisição.

#### FIFO (First In, First Out)

Método internacional onde as primeiras unidades compradas são consideradas as primeiras vendidas. Útil para quem precisa seguir regras fiscais de outros países.

### Por Que Usar

- **Declaração de IR**: Facilita o preenchimento do seu stack com KYC
- **Controle pessoal**: Saber se você está no lucro ou prejuízo
- **Estratégia de venda**: Decidir quando vender com base no preço médio

## Cotações e Preços 💹

O Valt busca cotações de diferentes fontes (com planos de expandir os sources para garantir o funcionamento):

### Bitcoin

- **Preço atual**: Coinbase (atualizado a cada 30 segundos)
- **Histórico**: Kraken (dados OHLC)

### Moedas Fiat

- **Taxas de câmbio**: Frankfurter (atuais e históricas)

### Funcionamento

- Cotações são buscadas automaticamente em background
- Requer conexão com internet
- Dados históricos são armazenados localmente para consultas offline

Além disso o repositório do Valt possui uma lista de histórico de preços das moedas disponíveis com dados desde 2010. Fique à vontade para utilizar em seus projetos!

## Privacidade e Segurança 🔒

### Dados Locais

Todos os seus dados ficam armazenados **localmente** no seu computador, em um arquivo `.valt`. Não há:

- Servidores externos
- Sincronização em nuvem
- Coleta de dados
- Telemetria

### Criptografia

O arquivo de dados é protegido por senha usando criptografia. Sem a senha, é impossível acessar os dados.

### Sua Responsabilidade

Como os dados são locais, **você é responsável** por:

- Fazer backups regulares
- Guardar sua senha em local seguro
- Proteger o arquivo contra perda ou roubo

## Próximos Passos

Agora que você entende os conceitos, explore as funcionalidades em detalhes:

- [Contas](../funcionalidades/contas.md)
- [Transações](../funcionalidades/transacoes.md)
- [Categorias](../funcionalidades/categorias.md)
- [Relatórios](../funcionalidades/relatorios.md)
