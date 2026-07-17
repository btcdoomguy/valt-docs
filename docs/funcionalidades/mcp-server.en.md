# MCP Server 🤖

Valt includes a built-in MCP (Model Context Protocol) server that enables natural language interaction with your finances through AI models. With over 80 tools available, you can query data, create transactions, manage accounts, and more - all through conversations with your favorite AI.

## What is MCP 🔗

The **Model Context Protocol (MCP)** is an open protocol created by Anthropic that standardizes communication between applications and language models (LLMs). Instead of each application creating its own integration with each AI, MCP provides a universal interface.

### Benefits

| Benefit | Description |
|---------|-------------|
| **Security** | Data stays on your computer, AI only accesses what you allow |
| **Standardization** | A single protocol works with multiple LLMs |
| **AI-Optimized** | Tools are described in a way that AI understands how to use |

!!! info "Learn More"
    For detailed technical information about the protocol, visit the [official MCP documentation](https://modelcontextprotocol.io/).

## Enabling the Server ⚙️

### Activating the Feature

1. Open Valt
2. Go to **[Settings](../guia/configuracoes.md)** > **Advanced**
3. Enable **"Enable MCP Server feature"**
4. Click **Save**

### Turning On the Server

After enabling the feature in settings:

1. On the main screen, locate the MCP button in the top right corner
2. Click to turn on the MCP server

| Option | Description | Default |
|--------|-------------|---------|
| **MCP Feature** | Enables/disables MCP functionality | Off |
| **Port** | Port where the server listens for connections | 5200 |

!!! warning "Security"
    The MCP server listens only on `localhost` by default, meaning only applications on your own computer can access it. Do not expose the server to the internet without additional security measures.

## Connecting with LLMs 🔌

### Claude Desktop

Anthropic's Claude Desktop offers native MCP support.

**Configuration file location:**

| System | Path |
|--------|------|
| Windows | `%APPDATA%\Claude\claude_desktop_config.json` |
| macOS | `~/Library/Application Support/Claude/claude_desktop_config.json` |
| Linux | `~/.config/claude/claude_desktop_config.json` |

**Configuration using mcp-remote:**

```json
{
  "mcpServers": {
    "valt": {
      "command": "npx",
      "args": [
        "mcp-remote",
        "http://localhost:5200/mcp"
      ]
    }
  }
}
```

!!! tip "Verifying the Connection"
    After configuring, restart Claude Desktop. You'll see a hammer icon (🔨) indicating that MCP tools are available. Click it to see Valt's tools.

### Ollama

Ollama is an open-source solution for running LLMs locally.

**Prerequisites:**

- Ollama installed ([ollama.ai](https://ollama.ai))
- A model with function calling support (e.g., `llama3.1`, `mistral`, `qwen2.5`)

#### Via Open WebUI

If you use Open WebUI with Ollama:

1. Access **Settings** > **Tools**
2. Add a new MCP tool
3. Server URL: `http://localhost:5200/mcp`

#### Via CLI

For command-line usage, you can use libraries like `mcp-client` or integrate directly via API.

### ChatGPT

ChatGPT can connect to the MCP server through Custom GPTs (requires ChatGPT Plus).

**Configuration:**

1. Create a Custom GPT at [chat.openai.com/gpts/editor](https://chat.openai.com/gpts/editor)
2. In the **Actions** section, click **Create new action**
3. For "Authentication", select **None**
4. In "Schema", import Valt MCP's OpenAPI specification

!!! warning "External Access"
    ChatGPT runs on OpenAI's servers, so it cannot access your `localhost` directly. You would need to expose your server via a tunnel (e.g., ngrok), which is **not recommended** for security reasons.

### Other LLMs

Any application that supports MCP can connect to Valt's server.

| Application | Type | Connection |
|-------------|------|------------|
| **Cline** | VS Code Extension | Configuration in `settings.json` |
| **Continue** | VS Code Extension | `config.json` file |
| **Cursor** | IDE | Native MCP configuration |
| **LangChain** | Framework | Python/JS MCP client |
| **LlamaIndex** | Framework | MCP integration |
| **Claude Code** | CLI | Native support via `.mcp.json` file |

**Connection endpoint:**

```
http://localhost:5200/mcp
```

## Available Tools 🛠️

Valt's MCP server exposes over 80 tools organized by category.

### Accounts (AccountTools)

<!-- Source: src/Valt.Infra/Mcp/Tools/Budget/AccountTools.cs -->
| Tool | Description |
|------|-------------|
| `GetAccounts` | Lists all accounts with their current balances |
| `GetAccount` | Gets a single account by its ID |
| `GetAccountGroups` | Lists all account groups |
| `CreateFiatAccount` | Creates a new fiat currency account (e.g., bank account, credit card) |
| `CreateBtcAccount` | Creates a new Bitcoin account (e.g., cold storage, exchange wallet) |
| `EditAccount` | Edits an existing account's properties (all fields are required) |
| `DeleteAccount` | Deletes an account (will fail if it has transactions) |

### Transactions (TransactionTools)

<!-- Source: src/Valt.Infra/Mcp/Tools/Budget/TransactionTools.cs -->
| Tool | Description |
|------|-------------|
| `GetTransactions` | Lists transactions with optional filtering by date, account, category, or search term |
| `AddFiatExpense` | Adds a fiat expense transaction (money leaving a fiat account) |
| `AddFiatIncome` | Adds a fiat income transaction (money entering a fiat account) |
| `AddFiatToFiatTransfer` | Adds a transfer between two fiat accounts |
| `AddBitcoinExpense` | Adds a Bitcoin expense transaction (sats leaving a BTC account) |
| `AddBitcoinIncome` | Adds a Bitcoin income transaction (sats entering a BTC account) |
| `AddBitcoinPurchase` | Adds a Bitcoin purchase (fiat leaves, BTC enters) |
| `DeleteTransaction` | Deletes a transaction |

### Categories (CategoryTools)

| Tool | Description |
|------|-------------|
| `GetCategories` | Lists all categories |
| `CreateCategory` | Creates a new category |
| `EditCategory` | Edits a category |
| `DeleteCategory` | Removes a category |

### Fixed Expenses (FixedExpenseTools)

<!-- Source: src/Valt.Infra/Mcp/Tools/Budget/FixedExpenseTools.cs -->
| Tool | Description |
|------|-------------|
| `GetFixedExpenses` | Gets all fixed/recurring expenses |
| `GetFixedExpense` | Gets a single fixed expense by its ID |
| `CreateMonthlyFixedExpense` | Creates a new monthly fixed expense with a constant amount |
| `CreateMonthlyVariableExpense` | Creates a new monthly fixed expense with a variable amount range |
| `EditFixedExpense` | Edits an existing fixed expense's name, category, and enabled status |
| `DeleteFixedExpense` | Deletes a fixed expense (transactions will lose their association) |

### Goals (GoalTools)

<!-- Source: src/Valt.Infra/Mcp/Tools/GoalTools.cs -->
| Tool | Description |
|------|-------------|
| `GetGoals` | Gets all financial goals, optionally filtered to goals containing a specific date |
| `GetGoal` | Gets a single financial goal by its ID |
| `CreateStackBitcoinGoal` | Creates a goal to stack a target amount of Bitcoin (sats) |
| `CreateSpendingLimitGoal` | Creates a goal to limit fiat spending to a maximum amount |
| `CreateDcaGoal` | Creates a DCA goal to make a target number of Bitcoin purchases |
| `CreateIncomeFiatGoal` | Creates a goal to earn a target amount of fiat income |
| `CreateIncomeBtcGoal` | Creates a goal to earn a target amount of Bitcoin income (sats) |
| `CreateReduceExpenseCategoryGoal` | Creates a goal to limit spending in a specific category |
| `CreateBitcoinHodlGoal` | Creates a goal to limit Bitcoin selling (HODL goal) |
| `CreateSaveFiatGoal` | Creates a goal to save a target fiat amount (income minus expenses) |
| `CreateSavingsRateGoal` | Creates a goal to save a target percentage of income |
| `CreateNetWorthBtcGoal` | Creates a goal to reach a target net worth in bitcoin (sats) |
| `DeleteGoal` | Deletes a financial goal |

### Average Price (AvgPriceTools)

<!-- Source: src/Valt.Infra/Mcp/Tools/AvgPriceTools.cs -->
| Tool | Description |
|------|-------------|
| `GetProfiles` | Gets all average price/cost basis tracking profiles |
| `GetProfile` | Gets a single average price profile by its ID |
| `GetProfileLines` | Gets all buy/sell/setup lines for an average price profile |
| `CreateBrazilianRuleProfile` | Creates a new average price profile using Brazilian Rule calculation (weighted average) |
| `CreateFifoProfile` | Creates a new average price profile using FIFO calculation (First-In-First-Out) |
| `EditProfile` | Edits an average price profile |
| `DeleteProfile` | Deletes an average price profile and all its lines |
| `AddBuyLine` | Adds a buy (acquisition) line to an average price profile |
| `AddSellLine` | Adds a sell (disposal) line to an average price profile |
| `AddSetupLine` | Adds a setup line (initial position) to an average price profile |
| `EditLine` | Edits an existing line in an average price profile |
| `DeleteLine` | Deletes a line from an average price profile |

### Reports (ReportTools)

<!-- Source: src/Valt.Infra/Mcp/Tools/ReportTools.cs -->
| Tool | Description |
|------|-------------|
| `GetMonthlyTotals` | Gets monthly totals report with income, expenses, and bitcoin transactions over a date range |
| `GetWealthOverview` | Gets wealth overview showing fiat and BTC totals over time periods (daily, weekly, monthly, yearly) |
| `GetExpensesByCategory` | Gets expenses breakdown by category for a date range |
| `GetIncomeByCategory` | Gets income breakdown by category for a date range |
| `GetAllTimeHigh` | Gets all-time high wealth data including ATH value, date, and current decline percentage |
| `GetMaxBtcStack` | Gets the maximum BTC stack ever held (lifetime high), the date it occurred, and decline from that peak |
| `GetStatistics` | Gets financial statistics including median monthly expenses and wealth coverage in months |

### Currencies (CurrencyTools)

<!-- Source: src/Valt.Infra/Mcp/Tools/CurrencyTools.cs -->
| Tool | Description |
|------|-------------|
| `GetAvailableCurrencies` | Gets available fiat currencies and currencies currently in use by accounts, fixed expenses, and avg price profiles |
| `GetMainCurrency` | Gets the main fiat currency configured for the application |
| `ConvertCurrency` | Converts an amount between currencies (USD, BRL, BTC, SATS, etc.). Uses live rates when available, falls back to historical rates. |
| `GetHistoricalPrice` | Gets historical price for BTC (in USD) or fiat currencies (relative to USD) at a specific date |

### Assets (AssetTools)

<!-- Source: src/Valt.Infra/Mcp/Tools/AssetTools.cs -->
Tools to manage **assets** — external investments tracked separately from accounts (stocks, ETFs, crypto, real estate, leveraged positions, BTC loans, and more).

#### Asset Operations

| Tool | Description |
|------|-------------|
| `GetAssets` | Lists all tracked assets |
| `GetVisibleAssets` | Lists only visible assets |
| `GetAsset` | Gets a single asset by its ID |
| `GetAssetsSummary` | Asset summary with totals in main currency and sats, including assets vs liabilities breakdown |
| `CreateBasicAsset` | Creates a basic asset (stock, ETF, crypto, commodity, or custom) |
| `CreateRealEstateAsset` | Creates a real estate asset |
| `CreateLeveragedPosition` | Creates a leveraged position (futures, perpetuals, margin) |
| `UpdateAssetPrice` | Updates the current price of an asset |
| `UpdateAssetQuantity` | Updates the quantity of a basic asset |
| `ToggleAssetVisibility` | Toggles the visibility of an asset |
| `ToggleAssetNetWorthInclusion` | Toggles whether the asset is included in the net worth calculation |
| `DeleteAsset` | Removes an asset |

#### BTC Loans

| Tool | Description |
|------|-------------|
| `CreateBtcLoan` | Creates a BTC-collateralized loan (borrowing fiat against BTC collateral); tracks LTV, health status, and accrued interest; supports daily APR or a fixed total debt (HodlHodl-style) |
| `CreateBtcLending` | Creates a lending position (lending fiat/BTC to a borrower or platform); tracks earned interest |
| `RepayLoan` | Marks a BTC loan or lending position as repaid |

#### Asset Groups

| Tool | Description |
|------|-------------|
| `GetAssetGroups` | Lists all asset groups |
| `CreateAssetGroup` | Creates an asset group |
| `UpdateAssetGroup` | Updates an asset group name and description |
| `DeleteAssetGroup` | Removes an asset group; assets in the group become ungrouped |
| `MoveAssetToGroup` | Moves an asset to a group |
| `RemoveAssetFromGroup` | Removes an asset from its group |

#### Loan State Timeline

Each BTC-collateralized loan keeps a timeline of state **snapshots**; current calculations always use the latest snapshot.

| Tool | Description |
|------|-------------|
| `AddLoanStateUpdate` | Adds a new state snapshot to a BTC-collateralized loan |
| `DeleteLoanStateUpdate` | Deletes a state snapshot by its effective date |
| `GetLoanStateTimeline` | Gets the full chronological snapshot timeline of the loan |
| `GetLatestLoanState` | Gets the latest recorded state of the loan |

**Parameters of `AddLoanStateUpdate`:**

| Parameter | Description |
|-----------|-------------|
| `assetId` | The asset ID |
| `effectiveDate` | Effective date (yyyy-MM-dd) |
| `totalBorrowed` | Borrowed principal still owed at the snapshot date |
| `interestAccruedUntilDate` | Interest accrued up to the snapshot date |
| `collateralSats` | BTC collateral in satoshis |
| `apr` | APR as decimal (e.g., 0.12 for 12%) |
| `fees` | Fees paid |
| `note` | Optional note |

**Parameters of `DeleteLoanStateUpdate`:**

| Parameter | Description |
|-----------|-------------|
| `assetId` | The asset ID |
| `effectiveDate` | Effective date of the snapshot to delete (yyyy-MM-dd) |

**Parameters of `GetLoanStateTimeline` and `GetLatestLoanState`:**

| Parameter | Description |
|-----------|-------------|
| `assetId` | The asset ID |

#### Sold Assets

Marking an asset as sold hides the asset from the active list and moves it to the history, preserving the previous visibility state for later restoration.

| Tool | Description |
|------|-------------|
| `MarkAssetAsSold` | Marks an asset as sold on the given date (defaults to today) |
| `UndoAssetSale` | Reverts a previous sale and restores the asset to the active list |
| `ListSoldAssets` | Lists all assets marked as sold |

**Parameters of `MarkAssetAsSold`:**

| Parameter | Description |
|-----------|-------------|
| `assetId` | The ID of the asset to mark as sold |
| `dateSold` | Sale date in yyyy-MM-dd format (optional, defaults to today) |

**Parameters of `UndoAssetSale`:**

| Parameter | Description |
|-----------|-------------|
| `assetId` | The ID of the sold asset to restore |

`ListSoldAssets` takes no parameters.

### Indicators (IndicatorTools)

<!-- Source: src/Valt.Infra/Mcp/Tools/IndicatorTools.cs -->
Bitcoin macro indicators, refreshed in the background and served from cache.

| Tool | Description |
|------|-------------|
| `GetBitcoinIndicators` | Gets current Bitcoin macro indicators: Mayer Multiple, Rainbow Chart, Fear & Greed Index, and Bitcoin Dominance |

## Use Cases 💡

### Querying Data

The MCP server allows you to ask questions in natural language:

**Example questions:**

- "What's my total wealth in Bitcoin?"
- "How much did I spend on food this month?"
- "What are my fixed expenses?"
- "How are my goals progressing?"
- "What was my average Bitcoin purchase price?"

**Example conversation:**

```
You: What was my total spending in December?

AI: Let me check your December transactions...

According to Valt data, in December you had:
- Total expenses: $4,523.45
- Top categories:
  1. Food: $1,200.00
  2. Transportation: $650.00
  3. Entertainment: $480.00
```

### Batch Import 📥

One of the most powerful features is the ability to import transactions using natural language. You provide a file and describe the format - the AI understands and performs the import.

#### How It Works

1. You provide a file (bank statement, spreadsheet, CSV)
2. Describe the format and what each column represents
3. The AI analyzes, categorizes, and imports the transactions

#### Example 1: Bank Statement PDF

```
You: [Attach Chase statement PDF]
I need to import this statement. It's from my Chase account in USD.
Expenses are negative and income is positive.

AI: Got it! I'll analyze the statement and import the transactions.

I found 47 transactions from 12/01 to 12/31:
- 35 expenses
- 8 income entries
- 4 transfers

I'll automatically categorize based on descriptions:
- "GROCERY STORE" → Food
- "UBER" → Transportation
- "NETFLIX" → Subscriptions

Should I proceed with the import?
```

#### Example 2: Custom Layout CSV

```
You: I have this CSV from my personal tracking:

date;amount;type;note
01/15;150.00;O;Grocery
01/16;5000.00;I;Salary
01/17;50.00;O;Uber

"O" means outgoing, "I" means incoming.
The account is "Chase [USD]".

AI: I understand the format:
- Separator: semicolon
- Date: MM/DD (I'll assume current year)
- Amount: standard decimal format
- O = expense, I = income

I'll import 3 transactions to the Chase account:
1. 01/15 - Grocery: -$150.00 (Food)
2. 01/16 - Salary: +$5,000.00 (Salary)
3. 01/17 - Uber: -$50.00 (Transportation)

Confirm?
```

#### Example 3: Exchange History for Average Price

```
You: [Attach Coinbase CSV]
This is my trade history from Coinbase.
I need to add it to the "Main Bitcoin" average price profile.

AI: Analyzing the Coinbase history...

I found 23 BTC/USD operations:
- 18 purchases totaling 0.15 BTC
- 5 sales totaling 0.02 BTC

I'll add to the "Main Bitcoin" profile:
- Current profile average price: $65,000
- After import: $62,500 (weighted average)

Should I add the operations?
```

!!! tip "Import Tip"
    The more context you provide about the file format, the better the result. Include the currency, column meanings, and any special patterns.

## Practical Examples 📝

### Creating a Goal via Conversation

```
You: I want to create a goal to stack 500k sats by the end of the month.

AI: I'll create a "Stack Bitcoin" goal for you:
- Type: Stack Bitcoin
- Period: Monthly
- Month: January/2025
- Target: 500,000 satoshis

Goal created! You can track progress in the Transactions tab.
Currently you have 125,000 sats stacked this month (25% of the goal).
```

### Complete Financial Analysis

```
You: Give me a complete analysis of my finances this month.

AI: Analyzing your finances for January/2025...

📊 **MONTHLY SUMMARY**

💰 **Total Wealth**: $45,230.00
- Fiat: $12,500.00 (28%)
- Bitcoin: 0.085 BTC ≈ $32,730.00 (72%)

📈 **Income**: $8,500.00
- Salary: $7,000.00
- Freelance: $1,500.00

📉 **Expenses**: $5,890.00
- Food: $1,200.00 (20%)
- Housing: $1,800.00 (31%)
- Transportation: $450.00 (8%)
- Entertainment: $640.00 (11%)
- Other: $1,800.00 (30%)

💾 **Savings**: $2,610.00 (31% of income)

₿ **Bitcoin**
- Purchases this month: 0.015 BTC
- Average purchase price: $63,000
- DCA completed: 3 of 4 purchases (75%)

🎯 **Goals**
- Stack 1M sats: 65% ✓
- Spending limit $6,000: 98% ⚠️
```

## Troubleshooting 🔧

### Server doesn't start

**Symptom**: Valt cannot start the MCP server.

**Possible causes**:

1. **Port in use**: Another application is using port 5200
   - **Solution**: Change the port in Valt settings

2. **Firewall blocking**: The firewall is preventing local connections
   - **Solution**: Add an exception for Valt in the firewall

### LLM cannot connect

**Symptom**: Claude Desktop or another LLM cannot find the server.

**Checks**:

1. Confirm the MCP feature is enabled in Settings > Advanced and the server is turned on from the main screen
2. Verify the URL is correct: `http://localhost:5200/mcp`
3. Test by accessing the URL in a browser (should return connection data)
4. Restart both Valt and the LLM application

### Tools don't appear

**Symptom**: The LLM connects but doesn't show Valt's tools.

**Solutions**:

1. Completely restart the LLM application
2. Check Valt logs for errors
3. Confirm the MCP configuration is correct

### Data doesn't update in the interface

**Symptom**: Transactions created via MCP don't appear in Valt's interface.

**Solution**: Refresh the view in Valt (navigate to another tab and back, or restart the application). Transactions are saved immediately, but the interface may need a refresh.

## Next Steps

- [Transactions](transacoes.md) - Understand transaction types
- [Import and Export](importar-exportar.md) - Traditional CSV import
- [Reports](relatorios.md) - Visual financial analysis
- [Average Price](preco-medio.md) - Track your Bitcoin acquisition cost
- [Assets](ativos.md) - External investments, BTC loans, and sold asset history
