# Transactions 💱

Transactions are the heart of Valt. Every financial movement is recorded as a transaction, allowing you to have complete control over your finances.

## Transaction Types

Valt offers six transaction types to cover all possible scenarios:

| Type | Description | Example |
|------|-------------|---------|
| **Fiat** | Entry or exit in fiat account | Salary, purchases, bills |
| **Bitcoin** | Entry or exit in Bitcoin account | Mining, donations |
| **Fiat to Fiat** | Transfer between fiat accounts | Wire transfer, between banks |
| **Bitcoin to Bitcoin** | Transfer between wallets | From exchange to Ledger |
| **Fiat to Bitcoin** | Bitcoin purchase | Purchase on Coinbase |
| **Bitcoin to Fiat** | Bitcoin sale | Sale on Kraken |

## Fiat Transaction 💵

### When to Use

Use for any entry or exit of money in traditional currency:

**Income (entries)**:
- Salary
- Freelance payment
- Refunds
- Dividends
- Sales

**Expenses (exits)**:
- Grocery shopping
- Electric, water, internet bills
- Subscriptions (Netflix, Spotify)
- Restaurants
- Transportation

### How to Record

1. Click **New Transaction**
2. Select **Fiat Transaction**
3. Fill in:

| Field | Description |
|-------|-------------|
| **Date** | When it occurred |
| **Type** | Income or Expense |
| **Account** | Which account was affected |
| **Amount** | How much it was |
| **Category** | Classification of the expense/income |
| **Description** | (Optional) Details |

4. Click **Save**

!!! tip "Built-in Calculator"
    In the amount field, you can type mathematical expressions like `150+35.50` and Valt will calculate automatically.

## Bitcoin Transaction ₿

### How to Record

1. Click **New Transaction**
2. Select **Bitcoin Transaction**
3. Fill in:

| Field | Description |
|-------|-------------|
| **Date** | When it occurred |
| **Type** | Income or Expense |
| **Bitcoin Account** | Which wallet |
| **Amount** | Quantity in sats or BTC |
| **Category** | Classification |
| **Description** | (Optional) Details |

4. Click **Save**

## Fiat to Fiat

### How to Record

1. Click **New Transaction**
2. Select **Fiat to Fiat**
3. Fill in:

| Field | Description |
|-------|-------------|
| **Date** | When it occurred |
| **Source Account** | Where the money came from |
| **Source Amount** | How much came out |
| **Destination Account** | Where it went |
| **Destination Amount** | How much arrived |
| **Description** | (Optional) Details |

4. Click **Save**

!!! info "Different Amounts"
    Amounts can differ between source and destination (e.g., currency exchange or transfer fees).

## Bitcoin to Bitcoin

### How to Record

1. Click **New Transaction**
2. Select **Bitcoin to Bitcoin**
3. Fill in:

| Field | Description |
|-------|-------------|
| **Date** | When it occurred |
| **Source Account** | Outgoing wallet |
| **Source Amount** | Quantity sent |
| **Destination Account** | Destination wallet |
| **Destination Amount** | Quantity received |
| **Description** | (Optional) Details |

4. Click **Save**

## Fiat to Bitcoin (Purchase) 🛒

### How to Record

1. Click **New Transaction**
2. Select **Fiat to Bitcoin**
3. Fill in:

| Field | Description |
|-------|-------------|
| **Date** | When you bought |
| **Fiat Account** | Where the money came from |
| **Fiat Amount** | How much you paid |
| **Bitcoin Account** | Where the bitcoins went |
| **Bitcoin Amount** | How many sats/BTC you received |
| **Description** | (Optional) Exchange, fee, etc. |

4. Click **Save**

## Bitcoin to Fiat (Sale)

### How to Record

1. Click **New Transaction**
2. Select **Bitcoin to Fiat**
3. Fill in:

| Field | Description |
|-------|-------------|
| **Date** | When you sold |
| **Bitcoin Account** | Where the bitcoins came from |
| **Bitcoin Amount** | How many sats/BTC you sold |
| **Fiat Account** | Where the money went |
| **Fiat Amount** | How much you received |
| **Description** | (Optional) Details |

4. Click **Save**

## Automatic Satoshi Value Calculation ⚡

### What It Is

The Sats field is a feature that automatically calculates how much a fiat transaction represented in satoshis on the date it occurred.

### How It Works

1. You record a fiat transaction (e.g., $20 expense)
2. Valt fetches the Bitcoin price on the transaction date
3. Calculates how many satoshis $20 could buy that day
4. Stores that value with the transaction

!!! info "When is the value calculated?"
    Valt needs to get the closing Bitcoin price on the entry date to perform this calculation. Therefore, when you enter today's transactions, this value always appears empty. Don't worry, the next day the system will calculate it automatically.

### Benefit

This allows you to see the **opportunity cost** of each expense:

- A $5 lunch in 2020 could be 100,000 sats
- Today, those 100,000 sats are worth $100
- You "spent" much more than $5 in Bitcoin terms

## Editing Transactions

1. In the transaction list, click on the desired transaction
2. Click the edit icon
3. Modify the necessary fields
4. Click **Save**

## Deleting Transactions

1. Click on the transaction
2. Click the delete icon (trash)
3. Confirm the deletion

!!! warning "Attention"
    Deletion cannot be undone.

## Filters and Search 🔍

### Filter by Date

Use the period selector to see transactions from:
- This month
- Previous month
- This year
- All time

### Filter by Account

Click on an account to see only its transactions.

If you want to see all accounts at once, click **View all accounts**

### Search

Use the search bar to find transactions by:
- Description
- Category
- Amount

## Best Practices ✨

### Consistency

- Record transactions regularly (daily or weekly)
- Keep standardized descriptions
- Use categories consistently

### Detail

- For large expenses, add detailed descriptions
- Include useful information like installments, etc.

### Verification

- Periodically compare Valt's balance with the real balance of your accounts
- Adjust if necessary

## Next Steps

- [Categories](categorias.md) - Organize your transactions
- [Fixed Expenses](despesas-fixas.md) - Recurring expenses
- [Reports](relatorios.md) - Analysis of your transactions
