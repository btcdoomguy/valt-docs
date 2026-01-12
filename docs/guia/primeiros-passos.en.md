# Getting Started 🚀

This guide will help you set up Valt and start managing your finances in just a few minutes.

## Interface Overview 🖥️

When you open Valt, you'll see three main tabs at the top:

1. **Transactions** - Where you manage accounts and record transactions
2. **Reports** - Charts and analysis of your data
3. **Average Price** - Bitcoin acquisition cost calculation

## Step 1: Create Your Accounts 🏦

Before recording transactions, you need to create accounts that represent where your money is.

### Creating a Fiat Account

1. In the **Transactions** tab, locate the accounts section
2. Click the **+** button to add a new account
3. Select **Fiat Account**
4. Fill in the fields:
   - **Name**: E.g., "Chase", "Wells Fargo", "Cash"
   - **Currency**: Select the currency (Dollar, Euro, etc.)
   - **Initial Balance**: The current amount in the account (optional)
   - **Icon**: Choose an icon to identify the account
5. Click **Save**

### Creating a Bitcoin Account ₿

1. Click the **+** button to add a new account
2. Select **Bitcoin Account**
3. Fill in the fields:
   - **Name**: E.g., "Ledger", "Coinbase", "Cold Wallet"
   - **Initial Balance**: The value in satoshis or BTC (optional)
   - **Icon**: Choose an icon
4. Click **Save**

!!! tip "How many accounts to create?"
    Create an account for each place where you keep money: banks, exchanges, Bitcoin wallets, cash, etc. This helps you have a complete view of your wealth.

## Step 2: Set Up Categories 🏷️

Valt comes with default categories, but you can customize them.

1. Access the settings menu
2. Click **Manage Categories**
3. Here you can:
   - Add new categories
   - Edit existing categories
   - Create subcategories (categories within categories)
   - Choose icons and colors

Examples of useful categories:

- **Income**: Salary, Freelance, Investments
- **Expenses**: Food, Transportation, Housing, Entertainment
- **Transfers**: Between accounts

## Step 3: Record Your First Transaction 📝

Now let's record a transaction.

### Recording an Expense

1. In the **Transactions** tab, click the **New Transaction** button
2. Select type **Fiat Expense**
3. Fill in:
   - **Date**: When the expense occurred
   - **Account**: Which account the money came from
   - **Amount**: How much was spent
   - **Category**: Where this expense fits
   - **Description**: (Optional) Details about the transaction
4. Click **Save**

### Recording a Bitcoin Purchase

1. Click **New Transaction**
2. Select type **Fiat to Bitcoin**
3. Fill in:
   - **Date**: When you bought
   - **Fiat Account**: Where the money came from
   - **Bitcoin Account**: Where the bitcoins went
   - **Fiat Amount**: How much you paid in dollars/euros
   - **Bitcoin Amount**: How many satoshis/BTC you received
4. Click **Save**

!!! info "Value in Satoshis"
    Valt automatically fetches the Bitcoin price on the transaction date. If you record an expense in dollars, the system will automatically calculate how much that represented in satoshis on that day.

## Step 4: Explore Reports 📊

With some transactions recorded, go to the **Reports** tab to view:

### Monthly Totals
See your income and expenses month by month in a bar chart.

### Spending by Category
Understand where your money is going with a pie chart showing the distribution by category.

### All-Time High
Track the peak of your wealth in Bitcoin terms.

### Statistics
View metrics like median spending and wealth coverage.

## Step 5: Set Up Fixed Expenses (Optional) 🔄

If you have recurring expenses, set them up for easier recording:

1. In the **Transactions** tab, access **Fixed Expenses**
2. Click **Add Fixed Expense**
3. Fill in:
   - **Name**: E.g., "Netflix", "Rent", "Gym"
   - **Amount**: How much you pay
   - **Frequency**: Monthly, Weekly, Biweekly, or Annual
   - **Account**: Which account is debited
   - **Category**: How to categorize
4. Click **Save**

With fixed expenses configured, you can quickly record these recurring costs.

## Next Steps

Now that you know the basics, explore:

- [Basic Concepts](conceitos-basicos.md) - Better understand how Valt works
- [Transactions](../funcionalidades/transacoes.md) - All available transaction types
- [Average Price](../funcionalidades/preco-medio.md) - Configure acquisition cost calculation

## Final Tips 💡

1. **Be consistent**: Record your transactions regularly for accurate data
2. **Use categories**: Good categorization makes later analysis easier
3. **Backup**: Periodically copy your `.valt` file to a safe location
4. **Explore reports**: The charts reveal patterns you wouldn't notice looking at individual transactions
