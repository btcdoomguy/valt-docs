# Goals 🎯

Goals allow you to define financial objectives and automatically track your progress. Whether it's accumulating Bitcoin, controlling spending, or maintaining a DCA routine, Valt calculates your progress in real time.

## What Are Goals

Goals are financial objectives with a defined timeframe that Valt monitors automatically. You define what you want to achieve and the system tracks your transactions to calculate progress.

## Available Goal Types

Valt offers different goal types for different objectives:

<!-- Source: src/Valt.Core/Modules/Goals/GoalTypeNames.cs + src/Valt.UI/Lang/language.resx -->

## Price Data and Exchange Rates

Some goals depend on price data and exchange rates to convert values between currencies or into bitcoin. When the displayed value depends on this data, Valt shows an asterisk (*) next to the goal.

<!-- Source: src/Valt.UI/Views/Main/Tabs/Transactions/Models/GoalEntryViewModel.cs + GoalsPanelView.axaml -->

The six price-dependent goal types are:

- **Fiat Income** — converts income in different currencies to your main fiat currency.
- **Spending Limit** — converts spending in different currencies to your main fiat currency.
- **Category Budget** — converts category spending to your main fiat currency.
- **Save Fiat** — calculates net savings (income minus expenses) across currencies.
- **Savings Rate** — calculates the savings percentage from income and expenses.
- **Net Worth in BTC** — converts account balances to satoshis using the BTC price.

The asterisk indicates that the value may be temporarily outdated until the next exchange-rate update is applied. Hover over the asterisk to see the following message:

> *This value may be outdated and will be updated when daily exchange rates are available.*

<!-- Source: src/Valt.UI/Lang/language.resx Goals_PriceDataTooltip -->

### Progress Goals (Accumulation)

These goals start at 0% and increase as you make progress. Upon reaching 100%, the goal is marked as **completed**.

<!-- Source: src/Valt.Core/Modules/Goals/ProgressionMode.cs ZeroToSuccess -->

| Type | Description | Example |
|------|-------------|---------|
| **Stack Bitcoin** | Defines a specific quantity to stack on the selected period compared to the previous quantity | "Stack 1 million more sats this month" |
| **DCA** | Track regular bitcoin purchases (Dollar Cost Averaging) | "Make 4 BTC purchases this month" |
| **Fiat Income** | Track income targets in your main fiat currency | "Earn $10,000 this month" |
| **Bitcoin Income** | Track bitcoin income targets (e.g. from work, mining, rewards) | "Receive 500,000 sats in income this month" |
| **Save Fiat** | Save a target fiat amount (income minus expenses) | "Save $1,000 this month" |
| **Savings Rate** | Save a target percentage of income | "Save 20% of income this month" |
| **Net Worth in BTC** | Reach a target net worth in bitcoin | "Reach a net worth of 50,000,000 sats (0.5 BTC)" |

### Limit Goals (Control)

These goals also start at 0%, but increase as you approach the limit. Upon reaching 100%, the goal is marked as **failed**.

<!-- Source: src/Valt.Core/Modules/Goals/ProgressionMode.cs DecreasingSuccess -->

| Type | Description | Example |
|------|-------------|---------|
| **Spending Limit** | Track spending against a budget limit in your main fiat currency | "Spend at most $3,000 this month" |
| **Category Budget** | Limit spending in a specific category | "Spend at most $500 on delivery" |
| **HODL** | Track bitcoin sales. Set to 0 for full HODL mode (no sales allowed) | "Sell at most 100,000 sats" |

**Net Worth in BTC** sums all visible account balances (fiat accounts, bitcoin accounts, external assets, and BTC-backed loans) and converts the total to satoshis before comparing it to the target. Only accounts marked as visible are included in the calculation.

<!-- Source: src/Valt.Core/Modules/Goals/GoalTypes/NetWorthBtcGoalType.cs + NetWorthBtcProgressCalculator.cs -->

!!! note "Save Fiat vs Fiat Income"
    **Save Fiat** tracks net savings (`income − expenses`), while **Fiat Income** tracks raw income toward a target. Use *Save Fiat* when you want to measure how much is left at the end of the month, and *Fiat Income* when you only want to track an income target.

## How Progress Works

### Accumulation Goals (Green Bar)

- Progress starts at **0%**
- Increases as you make related transactions
- Upon reaching **100%**, the goal is automatically marked as **Completed**
- The progress bar is green

**Example - Stack Bitcoin:**
```
Goal: Stack 1,000,000 sats
Current progress: 250,000 sats stacked
Progress bar: 25% (green)
```

### Limit Goals (Red Bar)

- Progress starts at **0%** (nothing spent = good)
- Increases as you spend/sell
- Upon reaching **100%**, the goal is automatically marked as **Failed**
- The progress bar is red
- Spending limit goals can exceed 100%

**Example - Spending Limit:**
```
Goal: Spend at most $2,000
Current progress: $1,000 spent
Progress bar: 50% (red)
```

## Available Periods

| Period | Description |
|--------|-------------|
| **Monthly** | Goal valid for a specific month |
| **Yearly** | Goal valid for an entire year |

## Creating a Goal

1. Access the **Transactions** tab
2. In the **Goals** section, click **New Goal**
3. Select the **period** (Monthly or Yearly)
4. Choose the **reference month/year**
5. Select the **goal type**
6. Configure the specific parameters for the chosen type
7. Click **Save**

### Configuration by Type

#### Stack Bitcoin
- **Target value**: Quantity of satoshis you want to accumulate

#### DCA (Dollar Cost Average)
- **Number of purchases**: Number of Bitcoin purchases you want to make

#### Fiat Income
- **Target value**: How much you want to earn
- **Currency**: In which currency

#### Bitcoin Income
- **Target value**: Quantity of satoshis you want to receive as income

#### Save Fiat
- **Target savings amount**: How much you want to save in the period
- **Currency**: In which currency

#### Savings Rate
- **Target savings rate (%)**: Percentage of income you want to save

#### Net Worth in BTC
- **Target value (sats)**: Desired net worth in satoshis

#### Spending Limit
- **Limit value**: Maximum you can spend
- **Currency**: In which currency

#### Category Budget
- **Limit value**: Maximum you can spend
- **Category**: Which category you want to control

#### HODL
- **Sell limit**: Maximum satoshis you can sell (0 = full HODL)

## Goal States

A goal can be in three states:

| State | Description | Display |
|-------|-------------|---------|
| **Open** | Goal still in progress | Progress bar |
| **Completed** | Accumulation goal reached 100% | "SUCCESS" badge (green) |
| **Failed** | Limit goal reached 100% | "FAILED" badge (red) |

## Managing Goals

### Editing

1. Click the desired goal
2. Click **Edit**
3. Modify the parameters
4. Save

!!! note "Note"
    When editing a goal, the calculated progress is preserved and will be recalculated automatically.

### Deleting

1. Click the desired goal
2. Click **Delete**
3. Confirm

### Recalculating

If a goal was marked as **Completed** or **Failed**, but you want to recalculate:

1. Right-click the goal
2. Select **Recalculate**
3. The goal returns to **Open** state and progress is recalculated with the latest data

This is useful when you edit past transactions that affect the goal, or when you want to re-evaluate a completed goal against new transactions.

<!-- Source: src/Valt.Core/Modules/Goals/Goal.cs Recalculate() -->

## Automatic Calculation

Valt automatically recalculates your goals' progress when transactions are created, edited, or deleted, and when exchange rates are updated. When something changes, Valt marks affected goals as stale and recalculates progress in the background.

<!-- Source: src/Valt.Core/Modules/Goals/Goal.cs IsUpToDate + MarkAsStale() + GoalProgressUpdaterJob.cs -->

The asterisk (*) displayed next to some goals indicates that the value depends on exchange-rate data and may be temporarily outdated. The tooltip message explains that the value will be updated when daily exchange rates are available. This same staleness mechanism is what allows Valt to know which goals need to be recalculated when new data arrives.

<!-- Source: src/Valt.Infra/Modules/Goals/Services/GoalProgressState.cs + GoalProgressUpdaterJob.cs -->

When recalculation completes, accumulation goals that reach 100% are marked as **Completed**, and limit goals that reach 100% are marked as **Failed**. You do not need to do anything manually; the system updates the states automatically.

## Display

Goals are displayed in the Transactions tab and are organized in the following order:

1. Open monthly goals
2. Open yearly goals
3. Completed goals
4. Failed goals

The progress bar is animated, smoothly showing the transition when progress changes.

## Usage Examples 💡

### Accumulation Strategy

**Monthly DCA Goal:**
- **Type**: DCA
- **Period**: Monthly
- **Target**: 4 purchases
- **Objective**: Ensure you make at least one purchase per week

**Yearly Accumulation Goal:**
- **Type**: Stack Bitcoin
- **Period**: Yearly
- **Target**: 10,000,000 sats (0.1 BTC)
- **Objective**: Accumulate a significant amount throughout the year

### Spending Control

**Monthly Budget:**
- **Type**: Spending Limit
- **Period**: Monthly
- **Limit**: $5,000
- **Objective**: Don't exceed your monthly budget

**Category Control:**
- **Type**: Category Budget
- **Period**: Monthly
- **Category**: Food > Delivery
- **Limit**: $400
- **Objective**: Reduce delivery spending

### Bitcoin Preservation

**Full HODL:**
- **Type**: HODL
- **Period**: Yearly
- **Sell limit**: 0 sats
- **Objective**: Don't sell any Bitcoin during the year (any sale will mark the goal as failed)

**Partial HODL:**
- **Type**: HODL
- **Period**: Monthly
- **Sell limit**: 500,000 sats
- **Objective**: Limit emergency sales

### Save Fiat

**Monthly Savings Goal:**
- **Type**: Save Fiat
- **Period**: Monthly
- **Target**: $1,000
- **Objective**: Track how much net income remains after expenses this month
- **Progress**: If income is $5,000 and expenses are $4,200, savings are $800 → 80% progress

!!! note "Save Fiat vs Fiat Income"
    **Save Fiat** tracks net savings (`income − expenses`), while **Fiat Income** tracks raw income toward a target. Use *Save Fiat* to measure what is left at the end of the month and *Fiat Income* to track only an income target.

### Savings Rate

**Monthly Savings Rate Goal:**
- **Type**: Savings Rate
- **Period**: Monthly
- **Target**: 20%
- **Objective**: Save at least 20% of income this month
- **Progress**: If income is $5,000 and expenses are $4,000, the savings rate is 20% → 100% progress (Completed)

### Net Worth in BTC

**Yearly Net Worth Goal:**
- **Type**: Net Worth in BTC
- **Period**: Yearly
- **Target**: 50,000,000 sats (0.5 BTC)
- **Objective**: Reach a total net worth of 0.5 BTC across all accounts
- **Progress**: Valt sums all visible account balances (fiat, bitcoin, assets, loans) in satoshis; if the total is 45,000,000 sats → 90% progress

## Best Practices ✨

### Set Realistic Goals

- Start with achievable goals
- Gradually increase as you gain confidence
- Use goal history to calibrate your expectations

### Combine Different Types

- Use accumulation goals for long-term objectives
- Use limit goals for day-to-day control
- Create complementary monthly and yearly goals

### Review Periodically

- At the beginning of each month, create your monthly goals
- At the beginning of the year, set yearly goals
- Analyze past goals to learn from your history

### Use Categories to Your Advantage

For "Category Budget" goals:
- Create specific categories for spending you want to control
- Example: Create "Entertainment > Delivery" to monitor food orders

## Next Steps

- [Transactions](transacoes.md) - How transactions work
- [Categories](categorias.md) - Organizing expenses
- [Reports](relatorios.md) - Analyzing spending
