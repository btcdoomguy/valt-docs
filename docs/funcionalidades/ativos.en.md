# Assets 📊

The Assets module lets you register external investments and wealth items in Valt to get a broader view of your total wealth. It is **completely optional** and separate from the accounts and transactions system.

## Overview

The Assets module was designed for those who want to see their complete wealth in one place. You can register stocks, ETFs, cryptocurrencies, real estate, commodities, leveraged positions, and custom assets.

!!! info "What the module is NOT"
    The Assets module **is not a real-time price tracker**. It serves to register what you own and have a consolidated view of your wealth. Price updates can be done manually or through configurable sources, but there is no continuous monitoring of market movements.

## Asset Types 📋

Valt supports 7 asset types:

| Type | Description | Example |
|------|-------------|---------|
| **Stocks** | Shares of publicly listed companies | AAPL, MSFT, GOOGL |
| **ETFs** | Exchange-traded index funds | VOO, QQQ, SPY |
| **Cryptocurrencies** | Digital currencies beyond Bitcoin | ETH, SOL, ADA |
| **Real Estate** | Properties and real estate assets | Apartment, land |
| **Commodities** | Raw materials and precious metals | Gold, silver |
| **Leveraged Positions** | Operations with leverage | Futures, margin |
| **Custom** | Any other type of asset | Vehicles, art, collections |

## Creating an Asset ➕

### Basic Asset

For stocks, ETFs, cryptocurrencies, commodities, and custom assets:

1. Go to the **Assets** tab
2. Click the **+** button to add a new asset
3. Select the asset type
4. Fill in the fields:

| Field | Description |
|-------|-------------|
| **Name** | Asset identifier (e.g., "AAPL", "Ethereum") |
| **Type** | Asset type (Stock, ETF, Crypto, etc.) |
| **Quantity** | How many units you own |
| **Purchase Price** | Average acquisition price per unit |
| **Currency** | Reference currency for the asset |
| **Price Source** | How the price will be updated (Manual, Yahoo Finance, Live Price) |
| **Icon** | Visual icon for identification |
| **Color** | Color associated with the asset |

5. Click **Save**

### Real Estate 🏠

Real estate assets have additional fields to capture income information:

1. Select the **Real Estate** type
2. Fill in the basic fields (name, value, currency)
3. Fill in the additional fields:

| Field | Description |
|-------|-------------|
| **Property Value** | Estimated market value |
| **Rental Income** | Monthly rental income received (if applicable) |
| **Currency** | Reference currency |

4. Click **Save**

!!! tip "Tip"
    Even if the property is not rented out, register it to have a complete view of your wealth.

### Leveraged Position ⚡

Leveraged positions include specific fields for risk management:

1. Select the **Leveraged Position** type
2. Fill in the basic fields
3. Fill in the additional fields:

| Field | Description |
|-------|-------------|
| **Entry Price** | Price at the time the position was opened |
| **Leverage** | Leverage multiplier (e.g., 2x, 5x, 10x) |
| **Liquidation Price** | Price at which the position is automatically liquidated |
| **Currency** | Reference currency |

4. Click **Save**

!!! warning "Attention"
    Leveraged positions involve high risk. Use the liquidation field to keep track of your risk limits.

## Price Sources 💰

Valt offers three ways to keep your asset prices updated:

### Manual

You set the price directly. Ideal for:

- Real estate (estimated market value)
- Custom assets
- Any asset you prefer to update yourself

### Yahoo Finance

Valt queries Yahoo Finance to get the price. Ideal for:

- Publicly listed stocks
- ETFs
- Some indexes and commodities

!!! tip "Tip"
    To use Yahoo Finance, enter the asset ticker exactly as it appears on Yahoo Finance (e.g., "AAPL" for Apple, "PETR4.SA" for Petrobras on B3).

### Live Price

Real-time price updates via API. Ideal for:

- Cryptocurrencies
- Assets with prices available through public APIs

## Managing Assets ⚙️

### Editing an Asset

1. Click on the asset you want to edit
2. Click the edit icon (pencil)
3. Modify the desired fields
4. Click **Save**

### Toggling Visibility

If you don't want to see an asset in the main list anymore:

1. Edit the asset
2. Uncheck the **Visible** option
3. Save

The asset will be hidden but remains registered.

### Include/Exclude from Net Worth

You can choose whether an asset should be counted in the net worth calculation:

1. Edit the asset
2. Check or uncheck the **Include in Net Worth** option
3. Save

!!! info "When to exclude from net worth"
    It can be useful to exclude assets you consider illiquid or that you don't want to count in the total, such as a personal-use property or a high-risk leveraged position.

### Reordering Assets

You can reorder assets using the right-click menu and the Move Up or Move Down options, or hold Ctrl and use the keyboard arrows. The order is saved automatically.

### Deleting an Asset

To delete an asset:

1. Edit the asset
2. Click **Delete**
3. Confirm the deletion

## Selling an Asset 💸

When you sell an asset fully or partially:

1. Click on the asset you want to sell
2. Select the **Sell** option
3. Fill in the fields:

| Field | Description |
|-------|-------------|
| **Quantity** | How many units you are selling |
| **Sell Price** | Price per unit at sale |
| **Date** | Date of the operation |

4. Click **Confirm**

Valt will automatically calculate the profit or loss of the operation based on the registered purchase price.

## Wealth and Net Worth 💎

### How Assets Integrate into Wealth

Assets marked as "Include in Net Worth" are added to Valt's total wealth, which includes:

- Balance of all accounts (fiat and Bitcoin)
- Value of all assets included in net worth

### Multi-Currency Conversion

If you own assets in currencies different from your main currency, Valt automatically converts them to your main currency using available exchange rates.

### Profit/Loss Indication

Valt uses colors to indicate the performance of your assets:

- **Green** 🟢: The asset is profitable (current price > purchase price)
- **Red** 🔴: The asset is at a loss (current price < purchase price)

This allows a quick visual analysis of your portfolio performance.

!!! warning "Important"
    The Assets module **does not track daily price fluctuations**. It offers a wealth view based on manual records or periodic updates via configured price sources. Don't expect home broker functionality — the goal is to have a **panoramic view of your wealth**.

## Best Practices ✨

### Keep Prices Updated

Periodically update the price of assets with manual source. For assets using Yahoo Finance or Live Price, Valt will do this for you.

### Organize by Type

Group your assets by type for easier visualization. Use icons and colors to quickly differentiate each one.

### Use the Net Worth Toggle Wisely

Include in net worth only the assets that make sense for your financial analysis. Highly illiquid or speculative assets may distort your wealth view.

### Record Purchase Price Correctly

The purchase price is the basis for profit/loss calculation. Make sure to register the correct value for accurate analysis.

### Does Not Replace Account Management

The Assets module complements, but does not replace, the accounts and transactions system. Continue using accounts to manage your day-to-day cash flow.

## Next Steps

- [Accounts](contas.md) - Managing your fiat and Bitcoin accounts
- [Average Price](preco-medio.md) - Calculating your Bitcoin acquisition cost
- [Reports](relatorios.md) - Complete wealth analysis
