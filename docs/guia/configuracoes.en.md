# Settings ⚙️

Valt is configured through the **Settings** window, accessible from the ☰ menu in the
top-left corner of the main screen. The options are organized into three tabs:
**General**, **Currencies**, and **Advanced**. Click **OK** to save.

## General

<!-- Source: src/Valt.UI/Views/Main/Modals/Settings/SettingsView.axaml + language.resx -->
| Option | Description |
|--------|-------------|
| **Main fiat currency** | Currency used in totals and reports (default: USD) |
| **Language and display format** | Interface language and date/number format; the list shows all system cultures, with Portuguese, Spanish and English pinned at the top. Valt is translated into Portuguese, Spanish and English *(requires restart)* |
| **Show hidden accounts** | Shows accounts marked as hidden in the lists |
| **Theme** | 13 dark-base themes: Default, Ocean, Midnight Galaxy, Golden Hour, Arctic Frost, Forest Canopy, Crimson Ember, Monochrome, Rose Quartz, Sunset Blaze, Mocha Brew, Copper Forge and Pepe |
| **Font Size** | Small, Medium or Large |

## Currencies

<!-- Source: SettingsView.axaml (Currencies tab) + Settings.FiatCurrencies.* resx -->
Check the fiat currencies you use. **USD is always included** and currencies in use
cannot be removed. When adding new currencies, Valt downloads their price history
(with confirmation).

## Advanced

### MCP Server (AI Assistant)

Enable the **MCP Server (AI Assistant)** and set the **MCP Server Port** (1024–65535, default: 5200) to connect
AI assistants. Full details in [MCP Server](../funcionalidades/mcp-server.md).

!!! warning "Security"
    The MCP server listens only on `localhost` by default, meaning only applications on your own computer can access it. Do not expose the server to the internet without additional security measures.

### Maintenance

| Button | When to use |
|-------------|-------------|
| **Clear account totals cache** | If displayed balances look wrong (see the [FAQ](../referencia/faq.md)) |
| **Clear transaction term cache** | If the transaction search does not find existing items |
| **Change database password** | To change the password of your `.valt` file |

## Your Data File

Your data lives in an encrypted `.valt` file whose location you choose when creating
it — see [Installation](../guia/instalacao.md). Back it up by copying the file to a
safe location.

## Next Steps

- [Getting Started](primeiros-passos.md) - Set up accounts and categories
- [FAQ](../referencia/faq.md) - Frequently asked questions
- [MCP Server](../funcionalidades/mcp-server.md) - Connect your AI
