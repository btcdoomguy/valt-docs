# Moedas Suportadas 💱

O Valt suporta 32 moedas fiat diferentes para contas e transações.

## Lista de Moedas 🌍

| Código | Nome | Símbolo |
|--------|------|---------|
| AUD | Dólar Australiano | A$ |
| BGN | Lev Búlgaro | лв |
| BRL | Real Brasileiro | R$ |
| CAD | Dólar Canadense | C$ |
| CHF | Franco Suíço | CHF |
| CNY | Yuan Chinês | ¥ |
| CZK | Coroa Tcheca | Kč |
| DKK | Coroa Dinamarquesa | kr |
| EUR | Euro | € |
| GBP | Libra Esterlina | £ |
| HKD | Dólar de Hong Kong | HK$ |
| HUF | Florim Húngaro | Ft |
| IDR | Rupia Indonésia | Rp |
| ILS | Novo Shekel Israelense | ₪ |
| INR | Rupia Indiana | ₹ |
| ISK | Coroa Islandesa | kr |
| JPY | Iene Japonês | ¥ |
| KRW | Won Sul-Coreano | ₩ |
| MXN | Peso Mexicano | $ |
| MYR | Ringgit Malaio | RM |
| NOK | Coroa Norueguesa | kr |
| NZD | Dólar Neozelandês | NZ$ |
| PHP | Peso Filipino | ₱ |
| PLN | Zloty Polonês | zł |
| RON | Leu Romeno | lei |
| SEK | Coroa Sueca | kr |
| SGD | Dólar de Singapura | S$ |
| THB | Baht Tailandês | ฿ |
| TRY | Lira Turca | ₺ |
| USD | Dólar Americano | $ |
| ZAR | Rand Sul-Africano | R |

## Moedas Mais Usadas ⭐

### BRL - Real Brasileiro

A moeda padrão para usuários brasileiros. Todos os cálculos de preço médio para IR devem usar BRL.

### USD - Dólar Americano

Referência internacional. Útil para quem:
- Opera em corretoras internacionais
- Quer comparar com preços globais de Bitcoin
- Tem contas em dólar

### EUR - Euro

Segunda maior moeda do mundo. Comum para:
- Moradores da zona do Euro
- Operações em corretoras europeias

## Conversão de Moedas 🔄

### Cotações Automáticas

O Valt busca cotações de moedas automaticamente do serviço Frankfurter:
- Cotações atuais: atualizadas frequentemente
- Cotações históricas: para cálculos de transações passadas

### Transferências Entre Moedas

Ao fazer uma transferência **Fiat para Fiat** entre contas de moedas diferentes, você pode informar:
- Valor de origem na moeda de origem
- Valor de destino na moeda de destino

O Valt registra ambos os valores, refletindo a taxa de câmbio real da operação.

### Exemplo

Transferência de conta em BRL para conta em USD:
- Origem: R$ 5.000 (conta Itaú - BRL)
- Destino: $1.000 (conta Wise - USD)
- Taxa implícita: 5 BRL/USD

## Moeda Principal

Nos relatórios, você pode escolher em qual moeda deseja visualizar os totais:
- Na moeda de cada conta
- Convertido para uma moeda específica
- Em satoshis (BTC)

## Adicionando Novas Moedas

Atualmente, a lista de moedas é fixa. Se você precisa de uma moeda não listada:
1. Abra uma issue no [GitHub](https://github.com/btcdoomguy/valt/issues)
2. Descreva qual moeda precisa
3. A moeda pode ser adicionada em versões futuras

## Precisão

Os valores em moeda fiat são armazenados com precisão de 2 casas decimais, adequado para a maioria das moedas.

!!! note "Exceções"
    Algumas moedas usam subdivisões diferentes (ex: JPY não tem centavos). O Valt trata todas com 2 casas decimais por simplicidade.

## Bitcoin ₿

Além das moedas fiat, o Valt trabalha nativamente com Bitcoin:

- **Armazenamento**: Em satoshis (inteiro de 64 bits)
- **Exibição**: Pode mostrar em BTC ou sats
- **Precisão**: 8 casas decimais (1 sat = 0.00000001 BTC)

### Conversão BTC ↔ Sats

| BTC | Satoshis |
|-----|----------|
| 1 | 100.000.000 |
| 0.1 | 10.000.000 |
| 0.01 | 1.000.000 |
| 0.001 | 100.000 |
| 0.0001 | 10.000 |
| 0.00001 | 1.000 |
| 0.000001 | 100 |
| 0.0000001 | 10 |
| 0.00000001 | 1 |

## Fontes de Cotação 📡

### Bitcoin

- **Preço atual**: Coinbase
- **Preço histórico**: Kraken (OHLC)

### Moedas Fiat

- **Todas**: Frankfurter (baseado no BCE - Banco Central Europeu)

As cotações são buscadas automaticamente em background quando há conexão com internet.
