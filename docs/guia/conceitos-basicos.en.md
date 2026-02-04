# Basic Concepts 📚

This guide explains the fundamental concepts of Valt and how it differs from traditional financial apps.

## Bitcoin as a Unit of Account ₿

Valt's differentiator is showing all your finances through a Bitcoin perspective. But what does this mean in practice?

### The Inflation Problem

When you look at a transaction from 5 years ago and see "$1,000", that value doesn't represent the same purchasing power as today. Inflation erodes the value of money over time. Fiat currencies were designed to enslave the population, draining the value of work from those who produce and redirecting it to the pockets of parasites and freeloaders.

### Valt's Solution

Valt automatically converts all your transactions to **satoshis** (the smallest unit of Bitcoin: 1 BTC = 100,000,000 satoshis) using the exchange rate on the transaction date.

This allows you to:

- Compare expenses from different times fairly
- Understand the opportunity cost of your decisions
- See your wealth in a deflationary monetary unit

### Practical Example

You bought a phone in January 2020 for $300.

- At the time, 1 BTC was worth $10,000
- Therefore, the phone cost 0.03 BTC (or 3,000,000 satoshis)
- If today 1 BTC is worth $100,000, those 3,000,000 sats would be worth $3,000

Valt shows this reality: your phone didn't cost "just" $300, it cost the equivalent of $3,000 in future purchasing power.

## Account Types 🏦

Valt works with two fundamental types of accounts:

### Fiat Accounts

Represent money in traditional currency:

- Bank accounts (Chase, Wells Fargo, Bank of America, etc.)
- Digital wallets (Venmo, PayPal, etc.)
- Cash
- Exchanges (balance in dollars)

Each fiat account has an **associated currency** (Dollar, Euro, etc.). Valt supports 32 different currencies.

### Bitcoin Accounts

Represent where you store your bitcoins:

- Hardware wallets (Ledger, Trezor, Coldcard)
- Software wallets (Electrum, Blue Wallet, etc.)
- Exchanges (BTC balance)
- Third-party custody

Values are stored in **satoshis** for maximum precision.

## Transaction Types 💱

Valt offers six transaction types to cover all scenarios:

### 1. Fiat Transaction

A simple entry or exit in a fiat account.

- **Income**: Salary, sales, refunds
- **Expense**: Purchases, bills, payments

### 2. Bitcoin Transaction

A simple entry or exit in a Bitcoin account.

- **Income**: Mining, airdrops, gifts received
- **Expense**: Donations, gifts given

### 3. Fiat to Fiat

Transfer between two fiat accounts.

- Transfer between banks
- Currency exchange (Dollar to Euro)
- Bank withdrawal to cash

### 4. Bitcoin to Bitcoin

Transfer between two Bitcoin accounts.

- Movement between wallets
- From exchange to hardware wallet

### 5. Fiat to Bitcoin

Bitcoin purchase.

- Exchange purchase
- P2P purchase
- Any BTC acquisition with fiat currency

### 6. Bitcoin to Fiat

Bitcoin sale.

- Exchange sale
- P2P sale
- Any BTC conversion to fiat currency

## Sats / Current Sats Value ⚡

All fiat transactions in Valt also receive the relative value in sats according to that date's closing price, as well as a column showing the current price of that amount of sats at today's price.

With this, you can observe the opportunity cost of all your past transactions.

### How It Works

When you record a fiat transaction, Valt automatically:

1. Fetches the Bitcoin price on the transaction date
2. Calculates how many satoshis that amount represented
3. Stores that value with the transaction

If the transaction is recorded on the current date or a future date, the Sats column will only be filled after market close.

### Why This Matters

This allows you to see the **opportunity cost** of each expense. For example:

- A $20 dinner in 2020 = 200,000 sats
- Today, those 200,000 sats are worth $200

Valt isn't saying you shouldn't have had dinner. It's showing a different perspective on the value of money over time.

## Average Acquisition Price 📊

For Bitcoin investors, knowing the **average price** is essential, both for tax operations and to track your wealth evolution.

### What It Is

The average price is the average acquisition cost of your bitcoins, considering all purchases you've made over time.

### Calculation Methods

Valt offers two methods:

#### Brazilian Rule

The average price is recalculated with each new purchase, considering the previous stock and the new acquisition.

#### FIFO (First In, First Out)

An international method where the first units purchased are considered the first sold. Useful for those who need to follow tax rules from other countries.

### Why Use It

- **Tax Declaration**: Facilitates filling out your KYC stack
- **Personal Control**: Know if you're in profit or loss
- **Selling Strategy**: Decide when to sell based on average price

## Quotes and Prices 💹

Valt fetches quotes from different sources (with plans to expand sources to ensure functionality):

### Bitcoin

- **Current price**: Coinbase (updated every 30 seconds)
- **Historical**: Kraken (OHLC data)

### Fiat Currencies

- **Exchange rates**: Frankfurter (current and historical)

### How It Works

- Quotes are fetched automatically in the background
- Requires internet connection
- Historical data is stored locally for offline queries

Additionally, the Valt repository has a price history list of available currencies with data since 2010. Feel free to use it in your projects!

## Privacy and Security 🔒

### Local Data

All your data is stored **locally** on your computer, in a `.valt` file. There is no:

- External servers
- Cloud sync
- Data collection
- Telemetry

### Encryption

The data file is password-protected using encryption. Without the password, it's impossible to access the data.

### Your Responsibility

Since data is local, **you are responsible** for:

- Making regular backups
- Keeping your password in a safe place
- Protecting the file against loss or theft

## Next Steps

Now that you understand the concepts, explore the features in detail:

- [Accounts](../funcionalidades/contas.md)
- [Transactions](../funcionalidades/transacoes.md)
- [Categories](../funcionalidades/categorias.md)
- [Reports](../funcionalidades/relatorios.md)
