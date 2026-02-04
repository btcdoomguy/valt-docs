# Fixed Expenses 🔄

Fixed expenses are recurring costs that you can configure once and quickly record every month. This feature saves time and helps with financial planning.

## What Are Fixed Expenses

Fixed expenses are costs that occur regularly at predictable intervals:

- **Housing**: Rent, HOA fees, property taxes
- **Utilities**: Electric, water, gas, internet, phone
- **Subscriptions**: Netflix, Spotify, Amazon Prime, gym
- **Financing**: Car payments, loans
- **Insurance**: Health, car, life

## Why Use Them 🎯

### Quick Recording

Instead of filling in all the fields of a transaction, you can record a fixed expense with just a few clicks.

### Recurring Cost Control

Easily see how much you spend on fixed commitments per month.

### Value History

Valt keeps a history of how much you paid in each period, useful for tracking price increases.

### Planning

Know in advance how much you'll need to cover your fixed expenses.

## Creating a Fixed Expense

1. In the **Transactions** tab, access the **Fixed Expenses** section
2. Click **Add Fixed Expense**
3. Fill in the fields:

| Field | Description |
|-------|-------------|
| **Name** | Identifier (e.g., "Netflix", "Rent") |
| **Amount** | How much you pay |
| **Frequency** | How often it occurs |
| **Account** | Which account is debited (optional) |
| **Currency** | If not linked to account, which currency |
| **Category** | How to categorize |
| **Icon** | Visual icon |

4. Click **Save**

## Available Frequencies

| Frequency | Description | Example |
|-----------|-------------|---------|
| **Monthly** | Once a month | Rent, Netflix |
| **Weekly** | Once a week | House cleaner |
| **Biweekly** | Every two weeks | Some insurance |
| **Annual** | Once a year | Car registration, annual insurance |

## Linking to an Account

You can link a fixed expense to a specific account:

### With Linked Account

- When recording, the account comes pre-filled
- Faster for expenses that always come from the same account
- Example: Netflix always debits from the Chase card

### Without Linked Account

- When recording, you choose the account
- Useful for expenses that can be paid different ways
- Example: Electric bill can be paid via transfer from any bank

## Value History (Ranges) 📈

A powerful feature is value history. When the value of an expense changes, you can keep a record:

### Example: Rent

```
Jan/2023 - Jun/2023: $1,500
Jul/2023 - Dec/2023: $1,600
Jan/2024 - current:  $1,700
```

### How It Works

1. Edit the fixed expense, changing the current value or the recurrence period
2. The previous period is automatically closed
3. View the history through the context menu on the fixed expense management screen

### Benefits

- See how your fixed costs evolved
- Compare what you paid before vs. now
- Identify excessive increases

## Recording a Fixed Expense

When it's time to pay a fixed expense:

1. In the **Fixed Expenses** section on the main screen, locate the expense and double-click or press Enter
2. The add transaction screen will open with pre-filled data. Edit what's needed and you're done. That transaction will be linked to your fixed expense.

TIPS: you can also perform other operations like ignoring that fixed expense only for that month, or manually link a fixed expense to an existing transaction by keeping the desired fixed expense selected in the sidebar and right-clicking on a transaction, where the Link to Fixed Expense option will appear.

## Managing Fixed Expenses

### Editing

1. Click the fixed expense
2. Click **Edit**
3. Modify the necessary fields
4. Save

### Deleting

1. Click the fixed expense
2. Click **Delete**
3. Confirm

!!! note "Note"
    Deleting a fixed expense does not remove already recorded transactions, only removes the link between them.

### Pausing

If you want to temporarily stop seeing a fixed expense (e.g., canceled Netflix):

1. Edit the expense
2. Mark as **Inactive**
3. Save

It won't appear in the main list, but the history is preserved.

## Fixed Expenses Report 📊

Valt will automatically generate a summary of your fixed expenses:

- Monthly total of commitments
- How much it represents of your budget
- Annual projection

This helps answer: "How much do I need per month just to cover fixed expenses?"

## Best Practices ✨

### Categorization

- Categorize your fixed expenses appropriately
- This allows analysis like "how much do I spend on subscriptions?"

### Periodic Review

- Every 3-6 months, review your fixed expenses
- Identify subscriptions you no longer use
- Negotiate values when possible

### Value Updates

- When a value changes (rent adjustment, internet increase), update it in Valt
- Use value history to keep the record

### Due Dates

Use the description field to note the due date:
- "Netflix - due on the 15th"
- "Rent - due on the 10th"

Valt asks for a start date to begin displaying the fixed expense on the main screen. Depending on the selected frequency, this date serves as a base to calculate the next occurrences. For example, setting the start date on a Friday for a weekly fixed expense will make the system calculate all future entries for Fridays.

## Configuration Examples 💡

### Netflix

- **Name**: Netflix
- **Amount**: $15.99
- **Frequency**: Monthly
- **Account**: Chase Card
- **Category**: Entertainment > Streaming

### Rent

- **Name**: Rent
- **Amount**: $2,500
- **Frequency**: Monthly
- **Account**: Wells Fargo
- **Category**: Housing > Rent

### Car Registration

- **Name**: Car Registration
- **Amount**: $300
- **Frequency**: Annual
- **Account**: (not linked)
- **Category**: Transportation > Taxes

### House Cleaner

- **Name**: Cleaning
- **Amount**: $150
- **Frequency**: Biweekly
- **Account**: (not linked)
- **Category**: Housing > Services

## Next Steps

- [Transactions](transacoes.md) - How transactions work
- [Categories](categorias.md) - Organizing expenses
- [Reports](relatorios.md) - Analyzing spending
