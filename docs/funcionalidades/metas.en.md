# Goals 🎯

Goals allow you to define financial objectives and automatically track your progress. Whether it's accumulating Bitcoin, controlling spending, or maintaining a DCA routine, Valt calculates your progress in real time.

## What Are Goals

Goals are financial objectives with a defined timeframe that Valt monitors automatically. You define what you want to achieve and the system tracks your transactions to calculate progress.

## Available Goal Types

Valt offers different goal types for different objectives:

### Progress Goals (Accumulation)

These goals start at 0% and increase as you make progress. Upon reaching 100%, the goal is marked as **completed**.

| Type | Description | Example |
|------|-------------|---------|
| **Stack Bitcoin** | Accumulate a quantity of satoshis | "Stack 1 million sats this month" |
| **DCA** | Make a number of Bitcoin purchases | "Make 4 BTC purchases this month" |
| **Fiat Income** | Reach a fiat currency income target | "Earn $10,000 this month" |
| **Bitcoin Income** | Receive a quantity of satoshis | "Receive 500,000 sats in income this month" |

### Limit Goals (Control)

These goals also start at 0%, but increase as you approach the limit. Upon reaching 100%, the goal is marked as **failed**.

| Type | Description | Example |
|------|-------------|---------|
| **Spending Limit** | Don't exceed a spending amount | "Spend at most $3,000 this month" |
| **Reduce Category** | Limit spending in a specific category | "Spend at most $500 on delivery" |
| **HODL Bitcoin** | Limit Bitcoin sales | "Sell at most 100,000 sats" |

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

#### Spending Limit
- **Limit value**: Maximum you can spend
- **Currency**: In which currency

#### Reduce Category
- **Limit value**: Maximum you can spend
- **Category**: Which category you want to control

#### HODL Bitcoin
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

If a goal was marked as Completed or Failed, but you want to recalculate:

1. Right-click the goal
2. Select **Recalculate**
3. The goal returns to "Open" state and progress is recalculated

This is useful when you edit past transactions that affect the goal.

## Automatic Calculation

Valt automatically recalculates your goals' progress when:

- A new transaction is created
- A transaction is edited
- A transaction is deleted
- Exchange rates are updated (for goals involving currency conversion)

!!! info "Multi-Currency Goals"
    **Fiat Income**, **Spending Limit**, and **Reduce Category** goals use exchange rate data to convert transactions in different currencies. These goals display an asterisk (*) indicating they depend on price data.

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
- **Type**: Reduce Category
- **Period**: Monthly
- **Category**: Food > Delivery
- **Limit**: $400
- **Objective**: Reduce delivery spending

### Bitcoin Preservation

**Full HODL:**
- **Type**: HODL Bitcoin
- **Period**: Yearly
- **Sell limit**: 0 sats
- **Objective**: Don't sell any Bitcoin during the year (any sale will mark the goal as failed)

**Partial HODL:**
- **Type**: HODL Bitcoin
- **Period**: Monthly
- **Sell limit**: 500,000 sats
- **Objective**: Limit emergency sales

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

For "Reduce Category" goals:
- Create specific categories for spending you want to control
- Example: Create "Entertainment > Delivery" to monitor food orders

## Next Steps

- [Transactions](transacoes.md) - How transactions work
- [Categories](categorias.md) - Organizing expenses
- [Reports](relatorios.md) - Analyzing spending
