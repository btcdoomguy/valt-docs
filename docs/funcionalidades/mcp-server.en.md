# MCP Server 🤖

Valt includes a built-in MCP (Model Context Protocol) server that enables natural language interaction with your finances through AI models. With over 45 tools available, you can query data, create transactions, manage accounts, and more - all through conversations with your favorite AI.

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
2. Go to **Settings** > **Advanced**
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

Valt's MCP server exposes over 45 tools organized by category.

### Accounts (AccountTools)

| Tool | Description |
|------|-------------|
| `GetAccounts` | Lists all accounts |
| `CreateAccount` | Creates a new account |
| `EditAccount` | Edits an existing account |
| `DeleteAccount` | Removes an account |
| `GetAccountBalance` | Gets an account's balance |
| `GetAccountHistory` | Account balance history |

### Transactions (TransactionTools)

| Tool | Description |
|------|-------------|
| `GetTransactions` | Lists transactions with filters |
| `AddFiatExpense` | Adds a fiat expense |
| `AddFiatIncome` | Adds fiat income |
| `AddBitcoinExpense` | Adds a Bitcoin expense |
| `AddBitcoinIncome` | Adds Bitcoin income |
| `AddFiatToFiatTransfer` | Transfer between fiat accounts |
| `AddBitcoinToBitcoinTransfer` | Transfer between wallets |
| `AddBitcoinPurchase` | Bitcoin purchase |

### Categories (CategoryTools)

| Tool | Description |
|------|-------------|
| `GetCategories` | Lists all categories |
| `CreateCategory` | Creates a new category |
| `EditCategory` | Edits a category |
| `DeleteCategory` | Removes a category |

### Fixed Expenses (FixedExpenseTools)

| Tool | Description |
|------|-------------|
| `GetFixedExpenses` | Lists fixed expenses |
| `CreateFixedExpense` | Creates a fixed expense |
| `EditFixedExpense` | Edits a fixed expense |
| `DeleteFixedExpense` | Removes a fixed expense |
| `GetFixedExpenseHistory` | Payment history |

### Goals (GoalTools)

| Tool | Description |
|------|-------------|
| `GetGoals` | Lists all goals |
| `CreateStackBitcoinGoal` | Stack Bitcoin goal |
| `CreateDCAGoal` | DCA goal |
| `CreateFiatIncomeGoal` | Fiat income goal |
| `CreateBitcoinIncomeGoal` | Bitcoin income goal |
| `CreateSpendingLimitGoal` | Spending limit goal |
| `CreateReduceCategoryGoal` | Reduce category goal |
| `CreateHodlBitcoinGoal` | HODL goal |

### Average Price (AvgPriceTools)

| Tool | Description |
|------|-------------|
| `GetAvgPriceProfiles` | Lists average price profiles |
| `CreateAvgPriceProfile` | Creates a profile |
| `EditAvgPriceProfile` | Edits a profile |
| `DeleteAvgPriceProfile` | Removes a profile |
| `GetAvgPriceLines` | Lists lines from a profile |
| `AddAvgPriceBuyLine` | Adds a purchase |
| `AddAvgPriceSellLine` | Adds a sale |
| `AddAvgPriceTransferInLine` | Adds an incoming transfer |
| `AddAvgPriceTransferOutLine` | Adds an outgoing transfer |
| `EditAvgPriceLine` | Edits a line |
| `DeleteAvgPriceLine` | Removes a line |

### Reports (ReportTools)

| Tool | Description |
|------|-------------|
| `GetMonthlyTotals` | Monthly totals by category |
| `GetWealthOverview` | Wealth overview |
| `GetWealthHistory` | Wealth evolution history |
| `GetCategoryStatistics` | Statistics by category |
| `GetIncomeVsExpenses` | Income vs expenses comparison |
| `GetTopExpenseCategories` | Top spending categories |

### Currencies (CurrencyTools)

| Tool | Description |
|------|-------------|
| `GetSupportedCurrencies` | Lists supported currencies |
| `GetExchangeRate` | Current exchange rate |
| `GetHistoricalPrice` | Historical price |
| `ConvertCurrency` | Converts values between currencies |

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
