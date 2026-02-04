# Import and Export 📥📤

Valt allows you to import and export your transactions in CSV format, making data migration, backups, and spreadsheet integration easy.

## Overview

| Feature | Description |
|---------|-------------|
| **Import** | Loads transactions from a CSV file through a guided wizard |
| **Export** | Saves all transactions to a CSV file |

Both features use the same CSV format, allowing you to export data from Valt and import it back without losing any information.

## Import Transactions 📥

### Accessing the Wizard

1. In the main menu, click **Import Transactions**
2. The import wizard will open

### Step 1: File Selection

In this step you select the CSV file to import.

**Available options:**

- **Select File**: Choose a CSV file from your computer
- **Download Template**: Downloads a CSV template with examples of all transaction types

After selecting the file, Valt will validate the content and show:

- ✅ Number of valid rows
- ❌ Number of parsing errors (if any)

!!! tip "Sample Template"
    If this is your first time importing, download the template first. It contains examples of all supported transaction types.

!!! warning "Parsing Errors"
    If there are errors, you can expand the list to see details. Fix the errors in the CSV file and select it again.

### Step 2: Account Mapping

Valt automatically detects accounts from the CSV file and maps them to existing or new accounts.

**Automatic detection:**

- Accounts with `[btc]` are detected as Bitcoin accounts
- Accounts with currency codes (e.g., `[USD]`, `[BRL]`) are detected as fiat accounts

**Summary displayed:**

| Information | Description |
|-------------|-------------|
| **New accounts** | Will be created during import |
| **Existing accounts** | Already exist in Valt and will be reused |

!!! info "Automatic Matching"
    Valt tries to match CSV account names with existing accounts (case-insensitive). If a match is found, the existing account will be used.

### Step 3: Category Preview

Similar to account mapping, Valt shows the categories found in the CSV.

**Summary displayed:**

| Information | Description |
|-------------|-------------|
| **New categories** | Will be created during import |
| **Existing categories** | Already exist in Valt and will be reused |

### Step 4: Summary

Before executing the import, you'll see a complete summary:

- Total transactions to import
- Total accounts (new ones highlighted)
- Total categories (new ones highlighted)

Review the numbers and click **Import** to continue.

### Step 5: Progress

During import you'll see:

- Animated progress bar
- Current action being executed
- Counter of imported transactions

When finished, a success message will be displayed and you can close the wizard.

## CSV File Format 📄

### Required Columns

| Column | Format | Description |
|--------|--------|-------------|
| `date` | YYYY-MM-DD | Transaction date |
| `description` | Text | Transaction description |
| `amount` | Number | Amount (negative = debit, positive = credit) |
| `account` | Text [CURRENCY] | Source account with currency in brackets |
| `category` | Text | Category name |

### Optional Columns

| Column | Format | Description |
|--------|--------|-------------|
| `to_account` | Text [CURRENCY] | Destination account (for transfers) |
| `to_amount` | Number | Amount in destination account (for exchanges) |

### Account Name Format

The account name must include the currency type in brackets:

| Type | Format | Example |
|------|--------|---------|
| **Fiat** | `Name [CURRENCY]` | `Checking [USD]`, `Savings [EUR]` |
| **Bitcoin** | `Name [btc]` | `Ledger [btc]`, `Coinbase [btc]` |

### Amount Format

| Type | Format | Example |
|------|--------|---------|
| **Fiat** | 2 decimal places | `150.00`, `-35.50` |
| **Bitcoin** | 8 decimal places | `0.00100000`, `-0.05000000` |

## Transaction Examples 📝

### Fiat Expense

```csv
date,description,amount,account,to_account,to_amount,category
2024-01-15,Grocery shopping,-150.00,Checking [USD],,,"Food"
```

### Fiat Income

```csv
date,description,amount,account,to_account,to_amount,category
2024-01-16,Salary,5000.00,Savings [USD],,,"Income"
```

### Bitcoin Income

```csv
date,description,amount,account,to_account,to_amount,category
2024-01-21,Mining rewards,0.00100000,Ledger [btc],,,"Income"
```

### Fiat to Fiat Transfer

```csv
date,description,amount,account,to_account,to_amount,category
2024-01-19,Transfer between banks,-1000.00,Checking [USD],Savings [USD],1000.00,"Transfer"
```

### Bitcoin to Bitcoin Transfer

```csv
date,description,amount,account,to_account,to_amount,category
2024-01-20,Wallet consolidation,-0.05000000,Coinbase [btc],Ledger [btc],0.05000000,"Transfer"
```

### Buy Bitcoin (Fiat to Bitcoin)

```csv
date,description,amount,account,to_account,to_amount,category
2024-01-17,Stack sats,-500.00,Checking [USD],Ledger [btc],0.00850000,"Investment"
```

### Sell Bitcoin (Bitcoin to Fiat)

```csv
date,description,amount,account,to_account,to_amount,category
2024-01-18,Sold BTC,-0.01000000,Ledger [btc],Checking [USD],450.00,"Trading"
```

## Export Transactions 📤

### How to Export

1. In the main menu, click **Export Transactions**
2. Choose the location and file name
3. Click **Save**

The file will be saved with all your transactions.

### What Gets Exported

The exported CSV file contains:

1. **Initial Balances**: For each account with an initial balance, a special row with category `InitialValue`
2. **All Transactions**: Ordered by date, in import-compatible format

### Example Exported File

```csv
date,description,amount,account,to_account,to_amount,category
2024-01-01,InitialValue,5000.00,Checking [USD],,,"InitialValue"
2024-01-01,InitialValue,0.05000000,Ledger [btc],,,"InitialValue"
2024-01-15,Grocery shopping,-150.00,Checking [USD],,,"Food"
2024-01-16,Salary,5000.00,Savings [USD],,,"Income"
```

!!! info "InitialValue Category"
    The `InitialValue` category is reserved by the system. When importing, rows with this category set the account's initial balance instead of creating a transaction.

## Use Cases 💡

### Data Backup

1. Export your transactions periodically
2. Store the CSV file in a safe location
3. If needed, import the file back

### Migration Between Computers

1. On the old computer, export your transactions
2. On the new computer, install Valt
3. Import the CSV file

### Spreadsheet Integration

The CSV format allows you to:

- Open in Excel or Google Sheets
- Create custom analyses
- Build custom charts
- Edit in bulk and re-import

### Import from Other Apps

If you have data in another financial app:

1. Export from the original app to CSV
2. Adjust the columns to match Valt's format
3. Import into Valt

## Best Practices ✨

### Before Importing

- Create a backup by exporting current data
- Test with a few transactions first
- Verify dates are in the correct format (YYYY-MM-DD)
- Confirm Bitcoin amounts have 8 decimal places

### Account Names

- Use consistent names with existing accounts
- Always include the currency in brackets
- For Bitcoin, always use `[btc]` in lowercase

### Categories

- Use existing category names when possible
- Avoid creating duplicate categories with different spellings

## Troubleshooting 🔧

### Error "Invalid date"

**Cause**: The date is not in YYYY-MM-DD format

**Solution**: Use the year-month-day format (e.g., `2024-01-15`)

### Error "Account not recognized"

**Cause**: The account name doesn't have the currency code in brackets

**Solution**: Add `[USD]`, `[EUR]`, `[btc]`, etc. to the end of the name

### Error "Invalid amount"

**Cause**: The amount contains invalid characters or incorrect formatting

**Solution**: Use only numbers and decimal point (e.g., `150.00`, not `$150.00`)

### Duplicate transactions after import

**Cause**: You imported the same file more than once

**Solution**: Valt doesn't automatically detect duplicates. Delete the duplicate transactions manually or restore a previous backup.

## Next Steps

- [Transactions](transacoes.md) - Manage your transactions manually
- [Accounts](contas.md) - Organize your accounts
- [Reports](relatorios.md) - Analyze your finances
