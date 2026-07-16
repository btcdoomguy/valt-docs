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

<!-- Source: src/Valt.Core/Modules/Budget/FixedExpenses/FixedExpense.cs SetDefaultAccountId/SetCurrency + src/Valt.UI/Lang/language.resx ManageFixedExpenses.CurrencyDefinition.* -->
!!! info "Account or currency, not both"
    A fixed expense is bound to either an **account** or a **currency**, never both. In the editor, choose **From default account** to link a fiat account, or **Direct set** to choose a currency directly. Selecting one mode clears the other.

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

Each occurrence of a fixed expense can be in one of four states:

<!-- Source: src/Valt.Core/Modules/Budget/FixedExpenses/FixedExpenseRecordState.cs + src/Valt.UI/Lang/language.resx FixedExpenseOverview.Status.* -->
| State | Meaning |
|-------|---------|
| **Paid** | A transaction is already linked to that reference date. |
| **Manually Paid** | Marked as paid without a linked transaction. |
| **Ignored** | Expense ignored for that reference date. |
| **Pending** | No action has been taken yet. |

TIPS: right-clicking a pending fixed expense lets you use the **Ignore for this date** or **Mark as paid** options. You can also manually link a fixed expense to an existing transaction: keep the desired fixed expense selected in the sidebar and right-click on a transaction, where the Link to Fixed Expense option will appear.

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

## Yearly Overview

<!-- Source: src/Valt.UI/Views/Main/Modals/FixedExpenseOverview/FixedExpenseOverviewView.axaml + FixedExpenseOverviewViewModel.cs + src/Valt.UI/Views/Main/Tabs/Transactions/FixedExpensesPanelView.axaml + src/Valt.UI/Lang/language.resx -->
The yearly overview screen is opened from the calendar icon in the Fixed Expenses panel header, on the **Transactions** tab. It displays a grid with the 12 months of the selected year, showing, for each expense, the expected amount, the actual amount, and the occurrence status. The year selector lets you switch between available years, and the **Paid Total** and **Future Expenses** totals are displayed in the footer.

### Out-of-range detection

<!-- Source: src/Valt.UI/Views/Main/Modals/FixedExpenseOverview/FixedExpenseOverviewViewModel.cs IsAmountOutOfRange -->
When a fixed expense has a fixed amount, the system flags the occurrence if the paid amount differs from the expected value. For expenses with a variable amount, the occurrence is flagged when the paid amount falls outside the expected minimum–maximum range.

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
