# Average Price 📊

The Average Price (or Average Acquisition Cost) module is an essential tool for those who invest in Bitcoin and need to calculate how much they paid, on average, for their bitcoins.

## Why Calculate Average Price 🎯

### Personal Control

Knowing your average price allows you to:

- Understand if you're in profit or loss
- Evaluate the right moment to buy more
- Make informed decisions about sales

### Tax Declaration (US)

In the US, to report capital gains on Bitcoin sales, you need to:

1. Know the acquisition cost (cost basis/average price)
2. Calculate the gain: Sale Value - Cost Basis
3. Pay tax on the gain (if applicable)

!!! warning "Important"
    Sales may be subject to capital gains tax. Consult an accountant or tax professional for specific guidance.

## Calculation Methods 🧮

Valt offers two calculation methods:

### 🇧🇷 Brazilian Rule

**How it works**:

1. With each purchase, the average price is recalculated
2. Formula: `(Previous Stock × Previous Average Price + New Purchase) ÷ New Total Stock`
3. Sales don't change the average price, only reduce the stock

**Example**:

| Date | Operation | BTC Qty | Value $ | Stock | Average Price |
|------|-----------|---------|---------|-------|---------------|
| Jan | Buy | 0.1 | 5,000 | 0.1 | 50,000 |
| Feb | Buy | 0.2 | 8,000 | 0.3 | 43,333 |
| Mar | Sell | -0.05 | 3,000 | 0.25 | 43,333 |
| Apr | Buy | 0.1 | 6,000 | 0.35 | 45,714 |

### 🌎 FIFO (First In, First Out)

International method where the first units purchased are considered the first sold.

**How it works**:

1. Each purchase keeps its individual price
2. When selling, the price of the oldest purchases is used first
3. Useful for those who follow tax rules from other countries

**Example**:

| Date | Operation | BTC Qty | Value $ | Available Lots |
|------|-----------|---------|---------|----------------|
| Jan | Buy | 0.1 | 5,000 | [0.1 @ 50k] |
| Feb | Buy | 0.2 | 8,000 | [0.1 @ 50k, 0.2 @ 40k] |
| Mar | Sell | -0.15 | - | [0.15 @ 40k] |

In the March sale, the following were used:
- 0.1 BTC from the January purchase (cost: $5,000)
- 0.05 BTC from the February purchase (cost: $2,000)

## Creating an Average Price Profile

Valt allows you to create multiple average price profiles (e.g., one for each exchange or a consolidated one).

### Step by Step

1. Go to the **Average Price** tab
2. Click **New Profile** or **Manage Profiles**
3. Fill in:

| Field | Description |
|-------|-------------|
| **Name** | Profile identifier (e.g., "Coinbase", "Consolidated") |
| **Method** | Brazilian Rule or FIFO |
| **Currency** | Reference currency (usually USD) |

4. Click **Create**

## Adding Lines

Each buy or sell operation is a "line" in the profile.

### Line Types

| Type | Use |
|------|-----|
| **Buy** | Bitcoin acquisition |
| **Sell** | Bitcoin sale |
| **Setup** | Initial setup (previous balance) |

### Recording a Purchase

1. In the profile, click **Add Line**
2. Select **Buy**
3. Fill in:

| Field | Description |
|-------|-------------|
| **Date** | When you bought |
| **Quantity** | How many BTC (or sats) |
| **Value** | How much you paid in $ |
| **Comment** | (Optional) Notes |

4. Click **Save**

### Recording a Sale

1. Click **Add Line**
2. Select **Sell**
3. Fill in:

| Field | Description |
|-------|-------------|
| **Date** | When you sold |
| **Quantity** | How many BTC you sold |
| **Value** | How much you received in $ |
| **Comment** | (Optional) Notes |

4. Click **Save**

### Initial Setup

If you already had Bitcoin before starting to use Valt:

1. Click **Add Line**
2. Select **Setup**
3. Fill in:
   - **Date**: Reference date
   - **Quantity**: How much you had
   - **Value**: Total acquisition cost (if known)
4. Click **Save**

## Viewing Calculations

After adding lines, Valt shows:

### Profile Summary

- **Current stock**: How many BTC you have
- **Total cost**: How much you paid in total
- **Average price**: Cost per BTC

### Operations Table

All lines with:
- Date
- Type (Buy/Sell/Setup)
- Quantity
- Value
- Average price after operation
- Stock after operation

### Gain/Loss on Sales

For each sale, Valt calculates:
- Acquisition cost (using average price)
- Sale value
- Gain or loss

## Integration with Transactions

!!! tip "Tip"
    The Average Price module is **separate** from normal transactions. This allows more flexibility, but requires you to keep both synchronized if you want.

### Why They're Separate

- Transactions = cash flow (where money comes from and goes to)
- Average Price = tax control (acquisition cost)

You can have Bitcoin purchase transactions and also enter them in the average price profile, but they are independent records.

## Export for Taxes 📄

Valt can generate useful reports for tax declaration:

- List of operations for the year
- Current average price
- Gains/losses on sales

!!! note "Note"
    Valt is an assistance tool. The responsibility for correct declaration is yours. Consult an accountant if you have questions.

## Multiple Profiles

You can create several profiles for different purposes:

### By Exchange

- "Coinbase" profile
- "Kraken" profile
- "P2P" profile

### By Wallet

- "Trading" profile
- "Long-term hold" profile

### Consolidated

- A single profile with all operations

## Best Practices ✨

### Keep Updated

Record your purchases and sales as soon as they occur. It's easier than trying to reconstruct the history later.

### Keep Receipts

Keep invoices, transfer receipts, and statements. They may be needed in case of audit.

### Check Calculations

Periodically verify that the stock in Valt matches what you actually have in your wallets.

### Separate Trading from Hold

If you do trading and also long-term hold, consider separate profiles to facilitate analysis.

## Common Scenarios 📋

### Starting from Zero

1. Create a profile with the desired method
2. Record each purchase as a line
3. The average price is calculated automatically

### Migrating from Another System

1. Create a profile
2. Use a **Setup** line with your current balance and cost
3. Continue recording new operations normally

### Consolidating Multiple Exchanges

1. Create a "Consolidated" profile
2. Record all operations from all exchanges
3. Valt calculates the overall average price

## Next Steps

- [Transactions](transacoes.md) - Recording purchases and sales
- [Reports](relatorios.md) - Wealth analysis
- [FAQ](../referencia/faq.md) - Frequently asked questions
