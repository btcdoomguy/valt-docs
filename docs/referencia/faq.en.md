# FAQ - Frequently Asked Questions ❓

Answers to the most common questions about Valt.

## General 📋

### What is Valt?

Valt is a free and open-source desktop app for personal financial management, developed especially for those who use Bitcoin as a unit of account. It allows you to control accounts, transactions, fixed expenses, and calculate the average acquisition price of Bitcoin.

### Is Valt free?

Yes, Valt is 100% free and open-source. You can use all features at no cost.

### Where is my data stored?

Your data is stored **locally** on your computer, in a `.valt` file protected by password. There is no cloud sync or data sent to external servers.

### What operating system does Valt work on?

Valt is cross-platform and works on:
- Windows 10/11
- Linux (Ubuntu, Fedora, etc.)
- macOS 11+

### Does Valt need internet?

Internet is needed to fetch Bitcoin and fiat currency quotes. However, you can use the app offline to record transactions - quotes will be fetched when there's a connection.

## Installation and Setup 🔧

### How do I install Valt?

1. Visit [Releases on GitHub](https://github.com/btcdoomguy/valt/releases)
2. Download the version for your operating system
3. Run the installer or extract the file
4. Run the executable

See the complete guide at [Installation](../guia/instalacao.md).

### I forgot my password. How do I recover it?

Unfortunately, **it's not possible to recover the password**. The file is encrypted and without the password there's no access to the data. That's why you should keep your password in a safe place.

### How do I backup my data?

1. Close Valt
2. Copy the `.valt` file to a safe location
3. Do this regularly

The file can be stored in the cloud (Google Drive, Dropbox) because it's encrypted.

### Can I use Valt on more than one computer?

Yes, but data doesn't sync automatically. You would need to:
1. Copy the `.valt` file to the other computer
2. Open with the same password
3. Manually manage which version is more up to date

## Accounts and Transactions 💱

### What's the difference between fiat account and Bitcoin account?

- **Fiat Account**: For traditional currencies (Dollar, Euro, etc.)
- **Bitcoin Account**: For storing balance in satoshis/BTC

### Can I have multiple accounts?

Yes, you can create as many accounts as you need. We recommend one account for each bank, exchange, or wallet.

### How do I record a Bitcoin purchase?

1. Click **New Transaction**
2. Select **Fiat to Bitcoin**
3. Fill in: source fiat account, amount paid, destination Bitcoin account, quantity received
4. Save

### What is the Sats column that appears on the main screen?

It's a feature that automatically calculates how much a fiat transaction represented in satoshis on the date it occurred. This allows you to see the opportunity cost of each expense. The system also displays a dynamic column called "Current Sats Price", which shows the fiat value of that expense today (the value it represented in bitcoin vs. the current price).

### My balance is wrong. What do I do?

1. Check if all transactions were recorded
2. Verify there are no duplicate transactions
3. Check the account's initial balance
4. Compare with the real statement from the bank/wallet
5. In the settings screen, advanced > Clear the account balance cache

## Average Price 📊

### What is average price?

It's the average acquisition cost of your bitcoins, calculated considering all purchases you've made.

### Which calculation method should I use?

- **Brazilian Rule**: If you declare taxes in Brazil
- **FIFO**: If you follow tax rules from other countries or prefer this method

### Does Valt's average price replace an accountant?

No. Valt is an assistance tool. For tax declaration, always consult an accountant.

### Do I need to record transactions in two places?

The Average Price module is separate from normal transactions. You can record in both for complete control, or use only one of them.

## Reports 📈

### Why are my reports empty?

Check:
1. If there are transactions recorded in the selected period
2. If the period filter is correct
3. If transactions have categories assigned (for category report)

### Can I export reports?

The export feature is in development.

### What does "Wealth Coverage" mean?

It's how many months your current wealth would sustain your expenses, based on the median of monthly expenses.

## Security and Privacy 🔒

### Is my data sent to any server?

No. Your data stays only on your computer. The only external connections are to fetch Bitcoin and currency quotes.

### Is the .valt file secure?

Yes, it's encrypted with your password. Without the password, it's impossible to access the data.

### Can I trust the code?

Valt is open-source. You can audit the code on [GitHub](https://github.com/btcdoomguy/valt).

## Common Problems 🛠️

### The app won't open

Try:
1. Check if there's another Valt process running
2. Reinstall the application
3. Check execution permissions (Linux/Mac)

### Quotes aren't updating

Check:
1. Your internet connection
2. If there's a firewall blocking the app
3. Wait a few minutes - updates are periodic

### Transaction disappeared

1. Check the period filter
2. Check the account filter
3. Use search to find the transaction

### Error opening database

Possible causes:
1. Incorrect password
2. Corrupted file
3. Incompatible version file

If the file is corrupted, restore a backup.

## Support 🆘

### Where do I report a bug?

Open an issue on [GitHub](https://github.com/btcdoomguy/valt/issues) describing:
1. What you were doing
2. What happened
3. What should have happened
4. Valt version and operating system

### How do I suggest a new feature?

Open an issue on [GitHub](https://github.com/btcdoomguy/valt/issues) with the "enhancement" tag describing your suggestion.

### Can I contribute to the code?

Yes! Valt is open-source. See the repository on [GitHub](https://github.com/btcdoomguy/valt) for more information on how to contribute.

## Other Questions 💡

### Does Valt work for controlling specific address balances in my wallet?

NO! Valt is a tool for managing Bitcoin balances, but it doesn't do direct UTXO management nor has connection to nodes.

### Does Valt work with Lightning Network?

You can create Bitcoin accounts to represent Lightning balances, but there's no direct integration with Lightning nodes.

### Can I import data from other apps?

Currently there's no automatic import feature. You need to record transactions manually.

### Does Valt have a mobile version?

No, Valt is exclusively desktop. A mobile version may be considered in the future.

### How often should I record transactions?

We recommend recording at least weekly to not accumulate. Ideally, record as soon as the transaction occurs.
