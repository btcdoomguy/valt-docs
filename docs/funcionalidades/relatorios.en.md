# Reports 📊

The **Reports** tab shows a consolidated view of your wealth, BTC stack, income and expense analyses, and market indicators. All values can be viewed in your main fiat currency or under a custom BTC price simulation.

<!-- Source: src/Valt.UI/Views/Main/Tabs/Reports/ReportsView.axaml lines 31-159 + language.resx -->
## Overview

The **Reports** tab has four main areas:

1. **Summary** — dashboards for **Wealth**, **Your all-time high**, **Your Stack**, **Statistics**, **Indicators**, **Simulated Prices**, **Leverage Positions** (when data exists), and **BTC Loans** (when data exists).
2. **Wealth Overview** — line chart of wealth over time.
3. **Monthly Totals** — line chart and detailed month-by-month table.
4. **By Categories** — horizontal bar charts for **Expenses** and **Income**, with filters by accounts and categories.

!!! note "Secure Mode"
    When **Secure Mode** is enabled, the Reports tab shows only the message *Leave Secure Mode to see the data*. No charts, panels, or data are displayed.

<!-- Source: src/Valt.UI/Views/Main/Tabs/Reports/ReportsView.axaml lines 40-74 + FixedPriceConfigViewModel.cs -->
## Simulate a Custom BTC Price

At the top of the **Summary** section, the **BTC Price Simulation** bar shows the current BTC price and the simulation controls.

### How to use

1. Click **Simulate**.
2. In the **Custom BTC Price** modal, enter a price in your main currency.
3. Click **Simulate** again.
4. A **SIMULATION** badge appears. The **Wealth**, **Your Stack**, **Simulated Prices**, **Leverage Positions**, and **BTC Loans** panels recalculate with the simulated price.
5. Click **Reset** to return to the live BTC price.

### Validation

- The price field is required.
- The value must be a valid decimal.
- The value must be non-negative.
- The error messages are *Price is required* and *Price must be non-negative.*

!!! note "What is not affected"
    The custom price does not change historical data. **Your all-time high**, **Statistics**, **Indicators**, **Wealth Overview**, **Monthly Totals**, and **By Categories** keep using live or historical data.

### Relationship with the Simulated Prices panel

The Fixed Price Bar is a global override of the live BTC price. The **Simulated Prices** panel is a separate list of up to 6 scenarios (percentage of the current price or fixed USD price). When the custom price is active, the **Simulated Prices** panel still shows the configured scenarios, but the baseline price becomes the custom price, not the live price. The configuration is opened by the panel's gear icon, in the **Simulated Prices Configuration** modal. Each line can be **Percentage** or **Fixed Price**, with a minimum percentage of 5%.

<!-- Source: src/Valt.UI/Views/Main/Tabs/Reports/ReportsView.axaml lines 76-159 + Panels/*.cs + language.resx -->
## Summary Dashboards

The **Summary** section displays up to eight panels. Each panel shows a title, icon, and rows of label-value pairs. The **Leverage Positions** and **BTC Loans** panels only appear when you have the corresponding data.

!!! info "Conditional visibility"
    The **Leverage Positions** panel only appears when you have at least one visible leveraged position included in net worth. The **BTC Loans** panel only appears when you have at least one active BTC-backed loan.

### Wealth

Title: **Wealth**

| Label | Value |
|--------|-------|
| **Total (as BTC)** | Total wealth represented in BTC |
| **Total (as Fiat)** | Total wealth in main fiat currency |
| **BTC** | BTC stack in BTC |
| **Fiat** | Non-BTC wealth in main fiat currency |
| **Total (in USD)** | Total wealth in USD (only when main currency is not USD) |
| **My Assets** | External assets value in main fiat currency |
| **BTC Spot %** | Percentage of total wealth held as BTC spot |

!!! tip "Tip about the first field"
    This is your total wealth represented in bitcoin as a unit of account.

### Your All-Time High

Title: **Your all-time high**

| Label | Value |
|--------|-------|
| **All-time high** | Highest value your wealth has reached |
| **Date** | Date the all-time high occurred |
| **Current difference** | Percentage decline from the all-time high |
| **Max drawdown** | Maximum drawdown percentage, when available |
| **Max drawdown date** | Date of maximum drawdown, when available |
| **BTC price to hit ATH** | BTC price needed to reach the all-time high again, when positive |

### Your Stack

Title: **Your Stack**

| Label | Value |
|--------|-------|
| **Current stack** | Current BTC stack |
| **% of total supply** | Stack as a percentage of the 21,000,000 BTC supply |
| **Global ranking** | Estimated maximum number of people who can have the same stack |
| **Maximum stack** | Largest BTC stack ever recorded, when available |
| **Max stack date** | Date of maximum stack, when available |
| **Decline from max** | Percentage decline from maximum stack, when available |

!!! tip "Tip about Global ranking"
    Maximum number of people who can have the same stack as you.

### Statistics

Title: **Statistics**

| Label | Value |
|--------|-------|
| **Median expenses (12mo)** | Median monthly expenses over the last 12 months |
| **Median expenses (prev 12mo)** | Median monthly expenses over the previous 12 months, when available |
| **YoY evolution** | Year-over-year change in median fiat expenses, when available |
| **Median sats (12mo)** | Median monthly expenses in satoshis, when available |
| **Median sats (prev 12mo)** | Previous period median in satoshis, when available |
| **Sats YoY evolution** | Year-over-year change in median sat-denominated expenses, when available |
| **Wealth coverage** | How many months the current wealth covers expenses |

!!! tip "Tip about Wealth coverage"
    How long you can sustain yourself with your current wealth without new income.

The panel has a gear icon that opens the configuration to exclude categories from the median expense calculation.

### Indicators

Title: **Indicators**

| Label | Value |
|--------|-------|
| **Mayer Multiple** | Mayer Multiple of the BTC market |
| **Rainbow Chart** | Current zone in the rainbow chart |
| **Fear & Greed** | Crypto market fear and greed index |
| **BTC Dominance** | BTC dominance percentage in the crypto market |

Indicators may appear stale if the data has not been updated recently.

### Simulated Prices

Title: **Simulated Prices**

Each row shows a configured scenario: the simulated BTC price and the projected total wealth in your main fiat currency. The panel has a gear icon that opens the configuration of up to 6 lines, each one either a **Percentage** or a **Fixed Price**.

### Leverage Positions

Title: **Leverage Positions**

| Label | Value |
|--------|-------|
| **Leveraged Stack** | BTC spot plus effective BTC exposure from leveraged positions |
| **Leverage Exposure** | Net BTC exposure from leveraged positions (positive for long, negative for short) |
| **Leverage %** | Percentage of leveraged stack coming from leverage |
| **Active Positions** | Number of active leveraged positions |
| **Current result** | Total P&L in main fiat currency |
| **Current result (BTC)** | Total P&L in BTC |
| **BTC price to hit ATH** | BTC price needed to reach ATH with the leveraged stack, when available |

### BTC Loans

Title: **BTC Loans**

| Label | Value |
|--------|-------|
| **Active loans** | Number of active loans |
| **Total debt** | Total debt in main fiat currency |
| **Total debt (BTC)** | Total debt in BTC |
| **Total borrowed** | Total principal borrowed in main fiat currency |
| **Avg LTV** | Debt-weighted average LTV |
| **Avg APR** | Debt-weighted average APR |
| **Total collateral** | Total collateral in BTC |
| **Collateral (fiat)** | Total collateral in main fiat currency |
| **% of stack pledged** | Collateral as a percentage of total BTC stack |
| **Free BTC** | BTC stack not pledged as collateral |
| **Loan health** | Count of healthy / warning / risk loans |
| **Highest LTV** | Highest LTV among all loans |
| **Closest to liq.** | Smallest LTV gap to liquidation |
| **Worst-case liq. price** | Highest BTC price at which any loan would still be at risk |
| **Accrued interest** | Total accrued interest in main fiat currency |
| **Fees paid** | Total fees paid in main fiat currency |
| **Avg loan age** | Average loan age in days |
| **Next repayment** | Next repayment date and days until then, when available |

<!-- Source: src/Valt.UI/Views/Main/Tabs/Reports/ReportsView.axaml lines 163-219 + language.resx -->
## Wealth Overview

The **Wealth Overview** section shows a line chart of wealth over time.

### Controls

- **Period selector**: **Daily**, **Weekly**, **Monthly**, or **Yearly**.
- **Max elements**: choose between **12**, **18**, or **24** data points on the chart.

### Chart

The line chart shows three series:

- **Total Wealth** — total accumulated value.
- **Bitcoin** — wealth denominated in BTC.
- **Fiat** — wealth in main fiat currency.

!!! note "Assets not included"
    *doesn't include Assets* — the chart does not include the value of external assets registered in the **Assets** tab.

<!-- Source: src/Valt.UI/Views/Main/Tabs/Reports/ReportsView.axaml lines 221-377 + language.resx -->
## Monthly Totals

The **Monthly Totals** section combines a line chart and a detailed month-by-month table.

### Controls

- **Date selector**: choose **Year** or **All**.

### Line chart

Shows fiat and BTC wealth trends over the selected period.

### Data table

| Column | Description |
|--------|-------------|
| **Date** | Month/year of the row |
| **Bitcoin** | Total in BTC |
| **% from previous month** | Percentage change from previous month (BTC) |
| **% from previous year** | Percentage change from previous year (BTC) |
| **Total wealth** | Total wealth in main fiat currency |
| **% from previous month** | Percentage change from previous month (fiat) |
| **% from previous year** | Percentage change from previous year (fiat) |
| **Total Income** | Total income in fiat (including conversions) |
| **Total Expenses** | Total expenses in fiat (including conversions) |
| **Income (Fiat)** | Income in fiat |
| **Expenses (Fiat)** | Expenses in fiat |
| **BTC Purchased** | BTC purchased in the month |
| **BTC Sold** | BTC sold in the month |
| **BTC Income** | Income in BTC |
| **BTC Expenses** | Expenses in BTC |

!!! note "Notes"
    *latest totals are calculated based on yesterday amounts*  
    *doesn't include Assets*

<!-- Source: src/Valt.UI/Views/Main/Tabs/Reports/ReportsView.axaml lines 379-526 + language.resx -->
## By Categories

The **By categories** section shows two horizontal bar charts: one for **Expenses** and one for **Income**.

### Controls

- **Date selector**: choose **Month**, **Year**, or **All**.
- **Filters**: left panel with multi-selection of **Accounts** and **Categories**.
- **Gear icon**: saves the current filter as default or loads the saved default filter.

### Charts

- **Expenses** — horizontal bars with the highest expense categories.
- **Income** — horizontal bars with the highest income categories.

Use the filters to include or exclude accounts and categories, and to focus on specific transaction groups.

<!-- Source: ReportsView.axaml + ReportsViewModel.cs + CsvExportService.cs -->
## Export

!!! note "No report export"
    The **Reports** tab does not have an export feature. To export your transaction data, use **Export Transactions...** from the main menu. You can also export average-price lines from the **Average Prices** tab.

<!-- Source: ReportsView.axaml + language.resx -->
## Usage Tips 💡

### Monthly review

Do a monthly review of your reports:

1. Check the **Summary** panels.
2. Analyze the **Wealth Overview**.
3. Look at **Monthly Totals** and compare with previous months.
4. Use **By Categories** to identify deviations in spending and income.

### Use price simulation for planning

Test different BTC prices to see how your wealth, stack, and leveraged positions react. This helps plan upside and downside scenarios without changing real data.

### View in satoshis

Observing everything in satoshis gives a different perspective:

- Expenses seem larger (opportunity cost).
- Motivation to save increases.
- Long-term vision strengthens.

### Secure Mode

When **Secure Mode** is enabled, all data on the Reports tab is hidden. Leave Secure Mode to view the charts and panels.

## Next Steps

- [Basic Concepts](../guia/conceitos-basicos.md) - Understand Valt's philosophy
- [Transactions](transacoes.md) - Improve data quality
- [Categories](categorias.md) - Better organize your spending
