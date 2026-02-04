# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a MkDocs documentation site for **Valt**, an open-source desktop personal finance application designed for Bitcoin users. The documentation is written in Brazilian Portuguese.

## Common Commands

```bash
# Serve documentation locally with hot-reload (default: http://127.0.0.1:8000)
mkdocs serve

# Build static site to /site directory
mkdocs build

# Deploy to GitHub Pages
mkdocs gh-deploy
```

**Prerequisites:** MkDocs with Material theme (`pip install mkdocs mkdocs-material`)

## Architecture

- **mkdocs.yml**: Site configuration including theme settings (Material, slate/default schemes, orange/amber palette), navigation structure, and markdown extensions
- **docs/**: Markdown documentation files organized by section:
  - `index.md` - Homepage
  - `guia/` - User guides (installation, getting started, basic concepts)
  - `funcionalidades/` - Feature documentation (accounts, transactions, categories, fixed expenses, average price, reports)
  - `referencia/` - Reference material (FAQ, supported currencies)

## Key Context

- All content is in Brazilian Portuguese (pt-BR) and English (en-US)
- The Material theme uses a dark (slate) / light toggle with orange primary color
- Navigation uses tabs, sections, and expandable items
- Enabled markdown extensions: admonition, details, superfences, tabbed content, keyboard keys, tables, TOC with permalinks
