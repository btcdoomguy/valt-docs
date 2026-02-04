# Supported Currencies 💱

Valt supports 32 different fiat currencies for accounts and transactions.

## Currency List 🌍

| Code | Name | Symbol |
|------|------|--------|
| AUD | Australian Dollar | A$ |
| BGN | Bulgarian Lev | лв |
| BRL | Brazilian Real | R$ |
| CAD | Canadian Dollar | C$ |
| CHF | Swiss Franc | CHF |
| CNY | Chinese Yuan | ¥ |
| CZK | Czech Koruna | Kč |
| DKK | Danish Krone | kr |
| EUR | Euro | € |
| GBP | British Pound | £ |
| HKD | Hong Kong Dollar | HK$ |
| HUF | Hungarian Forint | Ft |
| IDR | Indonesian Rupiah | Rp |
| ILS | Israeli New Shekel | ₪ |
| INR | Indian Rupee | ₹ |
| ISK | Icelandic Krona | kr |
| JPY | Japanese Yen | ¥ |
| KRW | South Korean Won | ₩ |
| MXN | Mexican Peso | $ |
| MYR | Malaysian Ringgit | RM |
| NOK | Norwegian Krone | kr |
| NZD | New Zealand Dollar | NZ$ |
| PHP | Philippine Peso | ₱ |
| PLN | Polish Zloty | zł |
| RON | Romanian Leu | lei |
| SEK | Swedish Krona | kr |
| SGD | Singapore Dollar | S$ |
| THB | Thai Baht | ฿ |
| TRY | Turkish Lira | ₺ |
| USD | US Dollar | $ |
| ZAR | South African Rand | R |

## Most Used Currencies ⭐

### USD - US Dollar

The reference currency for international users. All average price calculations for US taxes should use USD.

### EUR - Euro

Second largest currency in the world. Common for:
- Eurozone residents
- Operations on European exchanges

### BRL - Brazilian Real

The default currency for Brazilian users. All average price calculations for Brazilian taxes should use BRL.

## Currency Conversion 🔄

### Automatic Quotes

Valt automatically fetches currency quotes from the Frankfurter service:
- Current quotes: updated frequently
- Historical quotes: for past transaction calculations

### Transfers Between Currencies

When making a **Fiat to Fiat** transfer between accounts of different currencies, you can enter:
- Source value in source currency
- Destination value in destination currency

Valt records both values, reflecting the actual exchange rate of the operation.

### Example

Transfer from USD account to EUR account:
- Source: $5,000 (Chase - USD)
- Destination: €4,500 (Wise - EUR)
- Implicit rate: 0.9 EUR/USD

## Main Currency

In reports, you can choose which currency to view totals in:
- In each account's currency
- Converted to a specific currency
- In satoshis (BTC)

## Adding New Currencies

Currently, the currency list is fixed. If you need a currency not listed:
1. Open an issue on [GitHub](https://github.com/btcdoomguy/valt/issues)
2. Describe which currency you need
3. The currency may be added in future versions

## Precision

Fiat currency values are stored with 2 decimal places precision, adequate for most currencies.

!!! note "Exceptions"
    Some currencies use different subdivisions (e.g., JPY has no cents). Valt treats all with 2 decimal places for simplicity.

## Bitcoin ₿

Besides fiat currencies, Valt works natively with Bitcoin:

- **Storage**: In satoshis (64-bit integer)
- **Display**: Can show in BTC or sats
- **Precision**: 8 decimal places (1 sat = 0.00000001 BTC)

### BTC ↔ Sats Conversion

| BTC | Satoshis |
|-----|----------|
| 1 | 100,000,000 |
| 0.1 | 10,000,000 |
| 0.01 | 1,000,000 |
| 0.001 | 100,000 |
| 0.0001 | 10,000 |
| 0.00001 | 1,000 |
| 0.000001 | 100 |
| 0.0000001 | 10 |
| 0.00000001 | 1 |

## Quote Sources 📡

### Bitcoin

- **Current price**: Coinbase
- **Historical price**: Kraken (OHLC)

### Fiat Currencies

- **All**: Frankfurter (based on ECB - European Central Bank)

Quotes are fetched automatically in the background when there's an internet connection.
