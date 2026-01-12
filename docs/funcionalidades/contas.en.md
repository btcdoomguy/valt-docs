# Accounts 🏦

Accounts are the foundation of Valt. They represent all the places where you keep money, whether in fiat currency or Bitcoin.

## Overview

Valt works with two types of accounts:

- **Fiat Accounts**: For traditional currencies (Dollar, Euro, etc.)
- **Bitcoin Accounts**: For storing balances in satoshis

Every transaction in Valt is associated with at least one account.

## Fiat Accounts 💵

### What They Are

Fiat accounts represent where you keep money in traditional currency:

- Banks (Chase, Wells Fargo, Bank of America, Citibank, etc.)
- Fintechs (Venmo, Cash App, PayPal, etc.)
- Exchanges (balance in dollars)
- Physical cash (wallet, safe)
- Credit cards (for expense tracking)

### Creating a Fiat Account

1. In the **Transactions** tab, click the **+** button in the accounts section
2. Select **Fiat Account**
3. Fill in the fields:

| Field | Description |
|-------|-------------|
| **Name** | Account identifier (e.g., "Chase", "Cash") |
| **Currency** | The account currency (Dollar, Euro, etc.) |
| **Initial Balance** | Starting value of the account (optional) |
| **Icon** | Visual icon for identification |
| **Color** | Color associated with the account |

4. Click **Save**

### Supported Currencies

Valt supports more than 32 different fiat currencies and the list keeps growing. See the complete list at [Supported Currencies](../referencia/moedas.md).

The most common are:

- USD (US Dollar)
- EUR (Euro)
- GBP (British Pound)

## Bitcoin Accounts ₿

### What They Are

Bitcoin accounts represent where you store your bitcoins:

- Hardware wallets
- Software wallets (Electrum, Blue Wallet, Sparrow)
- Exchanges
- Institutional custody
- Lightning Network wallets

### Creating a Bitcoin Account

1. In the **Transactions** tab, click the **+** button in the accounts section
2. Select **Bitcoin Account**
3. Fill in the fields:

| Field | Description |
|-------|-------------|
| **Name** | Wallet identifier (e.g., "Ledger", "Coinbase") |
| **Initial Balance** | Starting value in satoshis or BTC (optional) |
| **Icon** | Visual icon for identification |
| **Color** | Color associated with the account |

4. Click **Save**

!!! tip "Satoshis vs BTC"
    When entering the initial balance, you can type in BTC (e.g., 0.001) or in satoshis (e.g., 100000). Valt stores everything internally in satoshis for maximum precision.

## Managing Accounts ⚙️

### Editing an Account

1. Click on the account you want to edit
2. Click the edit icon (pencil)
3. Modify the desired fields
4. Click **Save**

### Hiding an Account

If you don't want to see an account anymore (but want to keep the history):

1. Edit the account
2. Uncheck the **Visible** option
3. Save

The account won't appear in the main list, but transactions are preserved.

### Reordering Accounts

You can move accounts to reorder them as you prefer using the right-click menu and the Move Up or Move Down options, or hold Ctrl and use the keyboard arrows to move the account. The order is saved automatically.

### Deleting an Account

!!! warning "Attention"
    Deleting an account is only allowed if there are no registered transactions. If you no longer use the account, just hide it from the list.

To delete:

1. Edit the account
2. Click **Delete**
3. Confirm the deletion

## Selecting Icons

Valt offers an icon library to customize your accounts:

1. When creating or editing an account, click the **Icon** field
2. A window with available icons will open
3. Use search to find specific icons (e.g., "bank", "wallet", "bitcoin")
4. Click the desired icon
5. Choose a color for the icon

## Account Balance

### Balance Display

Each account's balance is shown:

1. In the account list (balance column)
2. In the total wealth summary
3. Converted to satoshis (for Bitcoin analysis)

## Total Wealth 💰

At the top of the accounts section, you'll see the **Total Wealth**, which sums:

- All fiat accounts (converted to your main currency)
- All Bitcoin accounts (converted to your main currency)
- Grand total in fiat currency and satoshis

This gives a complete view of how much you own.

## Best Practices ✨

### Organization

1. **One account per institution**: Create separate accounts for each bank/wallet
2. **Clear names**: Use names you'll easily recognize
3. **Consistent icons**: Use icons that represent the institution
4. **Group by type**: Keep banks together, wallets together

### When to Use Initial Balance

Use initial balance when:

- You're starting to use Valt and already have money in accounts
- You don't want (or can't) enter the entire transaction history

The initial balance is considered the "starting point" for calculations.

## Relationship with Other Features

### Transactions

Every transaction is linked to at least one account:

- Income and expenses: one account
- Transfers: two accounts
- Bitcoin purchases/sales: one fiat account + one Bitcoin account

### Fixed Expenses

Fixed expenses can be linked to a specific account, making recording easier.

### Reports

Reports consider all visible accounts to calculate totals and generate charts.

## Next Steps

- [Transactions](transacoes.md) - How to record movements
- [Fixed Expenses](despesas-fixas.md) - Recurring expenses
- [Reports](relatorios.md) - Wealth analysis
