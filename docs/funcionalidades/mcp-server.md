# Servidor MCP 🤖

O Valt inclui um servidor MCP (Model Context Protocol) integrado que permite a interação com suas finanças usando linguagem natural através de modelos de IA. Com mais de 80 ferramentas disponíveis, você pode consultar dados, criar transações, gerenciar contas e muito mais - tudo através de conversas com sua IA favorita.

## O Que é MCP 🔗

O **Model Context Protocol (MCP)** é um protocolo aberto criado pela Anthropic que padroniza a comunicação entre aplicações e modelos de linguagem (LLMs). Em vez de cada aplicativo criar sua própria integração com cada IA, o MCP fornece uma interface universal.

### Benefícios

| Benefício | Descrição |
|-----------|-----------|
| **Segurança** | Dados ficam no seu computador, a IA acessa apenas o que você permite |
| **Padronização** | Um único protocolo funciona com múltiplos LLMs |
| **Otimizado para IA** | Ferramentas são descritas de forma que a IA entende como usar |

!!! info "Saiba Mais"
    Para informações técnicas detalhadas sobre o protocolo, visite a [documentação oficial do MCP](https://modelcontextprotocol.io/).

## Habilitando o Servidor ⚙️

### Ativando o Recurso

1. Abra o Valt
2. Acesse **[Configurações](../guia/configuracoes.md)** > **Avançado**
3. Ative a opção **"Enable MCP Server feature"**
4. Clique em **Salvar**

### Ligando o Servidor

Após habilitar o recurso nas configurações:

1. Na tela principal, localize o botão de MCP no canto superior direito
2. Clique para ligar o servidor MCP

| Opção | Descrição | Padrão |
|-------|-----------|--------|
| **Recurso MCP** | Habilita/desabilita a funcionalidade MCP | Desligado |
| **Porta** | Porta onde o servidor escuta conexões | 5200 |

!!! warning "Segurança"
    O servidor MCP escuta apenas em `localhost` por padrão, ou seja, apenas aplicativos no seu próprio computador podem acessá-lo. Não exponha o servidor à internet sem medidas de segurança adicionais.

## Conectando com LLMs 🔌

### Claude Desktop

O Claude Desktop da Anthropic oferece suporte nativo ao MCP.

**Localização do arquivo de configuração:**

| Sistema | Caminho |
|---------|---------|
| Windows | `%APPDATA%\Claude\claude_desktop_config.json` |
| macOS | `~/Library/Application Support/Claude/claude_desktop_config.json` |
| Linux | `~/.config/claude/claude_desktop_config.json` |

**Configuração usando mcp-remote:**

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

!!! tip "Verificando a Conexão"
    Após configurar, reinicie o Claude Desktop. Você verá um ícone de martelo (🔨) indicando que ferramentas MCP estão disponíveis. Clique nele para ver as ferramentas do Valt.

### Ollama

O Ollama é uma solução de código aberto para rodar LLMs localmente.

**Pré-requisitos:**

- Ollama instalado ([ollama.ai](https://ollama.ai))
- Um modelo com suporte a function calling (ex: `llama3.1`, `mistral`, `qwen2.5`)

#### Via Open WebUI

Se você usa o Open WebUI com Ollama:

1. Acesse **Settings** > **Tools**
2. Adicione uma nova ferramenta MCP
3. URL do servidor: `http://localhost:5200/mcp`

#### Via CLI

Para uso via linha de comando, você pode usar bibliotecas como `mcp-client` ou integrar diretamente via API.

### ChatGPT

O ChatGPT pode se conectar ao servidor MCP através de Custom GPTs (requer ChatGPT Plus).

**Configuração:**

1. Crie um Custom GPT em [chat.openai.com/gpts/editor](https://chat.openai.com/gpts/editor)
2. Na seção **Actions**, clique em **Create new action**
3. Para "Authentication", selecione **None**
4. Em "Schema", importe a especificação OpenAPI do Valt MCP

!!! warning "Acesso Externo"
    O ChatGPT roda nos servidores da OpenAI, então não consegue acessar seu `localhost` diretamente. Você precisaria expor seu servidor via túnel (ex: ngrok), o que **não é recomendado** por questões de segurança.

### Outros LLMs

Qualquer aplicação que suporte MCP pode se conectar ao servidor do Valt.

| Aplicação | Tipo | Conexão |
|-----------|------|---------|
| **Cline** | Extensão VS Code | Configuração em `settings.json` |
| **Continue** | Extensão VS Code | Arquivo `config.json` |
| **Cursor** | IDE | Configuração MCP nativa |
| **LangChain** | Framework | Cliente MCP Python/JS |
| **LlamaIndex** | Framework | Integração MCP |
| **Claude Code** | CLI | Suporte nativo via arquivo `.mcp.json` |

**Endpoint de conexão:**

```
http://localhost:5200/mcp
```

## Ferramentas Disponíveis 🛠️

O servidor MCP do Valt expõe mais de 80 ferramentas organizadas por categoria.

### Contas (AccountTools)

<!-- Source: src/Valt.Infra/Mcp/Tools/Budget/AccountTools.cs -->
| Ferramenta | Descrição |
|------------|-----------|
| `GetAccounts` | Lista todas as contas com seus saldos atuais |
| `GetAccount` | Obtém uma conta pelo seu ID |
| `GetAccountGroups` | Lista todos os grupos de contas |
| `CreateFiatAccount` | Cria uma conta em moeda fiat (ex.: conta bancária, cartão de crédito) |
| `CreateBtcAccount` | Cria uma conta Bitcoin (ex.: cold storage, wallet em exchange) |
| `EditAccount` | Edita as propriedades de uma conta existente |
| `DeleteAccount` | Remove uma conta (falha se ela tiver transações) |

### Transações (TransactionTools)

<!-- Source: src/Valt.Infra/Mcp/Tools/Budget/TransactionTools.cs -->
| Ferramenta | Descrição |
|------------|-----------|
| `GetTransactions` | Lista transações com filtros opcionais por data, conta, categoria ou termo de busca |
| `AddFiatExpense` | Adiciona despesa em fiat |
| `AddFiatIncome` | Adiciona receita em fiat |
| `AddFiatToFiatTransfer` | Transferência entre contas fiat |
| `AddBitcoinExpense` | Adiciona despesa em Bitcoin |
| `AddBitcoinIncome` | Adiciona receita em Bitcoin |
| `AddBitcoinPurchase` | Compra de Bitcoin (fiat sai, sats entram) |
| `DeleteTransaction` | Remove uma transação |

### Categorias (CategoryTools)

| Ferramenta | Descrição |
|------------|-----------|
| `GetCategories` | Lista todas as categorias |
| `CreateCategory` | Cria uma nova categoria |
| `EditCategory` | Edita uma categoria |
| `DeleteCategory` | Remove uma categoria |

### Despesas Fixas (FixedExpenseTools)

<!-- Source: src/Valt.Infra/Mcp/Tools/Budget/FixedExpenseTools.cs -->
| Ferramenta | Descrição |
|------------|-----------|
| `GetFixedExpenses` | Lista todas as despesas fixas/recorrentes |
| `GetFixedExpense` | Obtém uma despesa fixa pelo seu ID |
| `CreateMonthlyFixedExpense` | Cria uma despesa fixa mensal com valor constante |
| `CreateMonthlyVariableExpense` | Cria uma despesa fixa mensal com faixa de valor variável (mínimo–máximo) |
| `EditFixedExpense` | Edita nome, categoria e status de uma despesa fixa |
| `DeleteFixedExpense` | Remove uma despesa fixa (as transações perdem a associação) |

### Metas (GoalTools)

<!-- Source: src/Valt.Infra/Mcp/Tools/GoalTools.cs -->
| Ferramenta | Descrição |
|------------|-----------|
| `GetGoals` | Lista todas as metas, com filtro opcional por data |
| `GetGoal` | Obtém uma meta pelo seu ID |
| `CreateStackBitcoinGoal` | Meta de acumular um valor alvo em Bitcoin (sats) |
| `CreateSpendingLimitGoal` | Meta de limitar os gastos em fiat a um valor máximo |
| `CreateDcaGoal` | Meta de DCA: realizar um número alvo de compras de Bitcoin |
| `CreateIncomeFiatGoal` | Meta de alcançar uma renda alvo em fiat |
| `CreateIncomeBtcGoal` | Meta de alcançar uma renda alvo em Bitcoin (sats) |
| `CreateReduceExpenseCategoryGoal` | Meta de limitar gastos em uma categoria específica |
| `CreateBitcoinHodlGoal` | Meta de limitar vendas de Bitcoin (HODL) |
| `CreateSaveFiatGoal` | Meta de poupar um valor alvo em fiat (receitas menos despesas) |
| `CreateSavingsRateGoal` | Meta de poupar um percentual alvo da renda |
| `CreateNetWorthBtcGoal` | Meta de alcançar um patrimônio líquido alvo em bitcoin (sats) |
| `DeleteGoal` | Remove uma meta |

### Preço Médio (AvgPriceTools)

<!-- Source: src/Valt.Infra/Mcp/Tools/AvgPriceTools.cs -->
| Ferramenta | Descrição |
|------------|-----------|
| `GetProfiles` | Lista todos os perfis de preço médio/custo de aquisição |
| `GetProfile` | Obtém um perfil pelo seu ID |
| `GetProfileLines` | Lista as linhas de compra/venda/setup de um perfil |
| `CreateBrazilianRuleProfile` | Cria um perfil com cálculo pela Regra Brasileira (média ponderada) |
| `CreateFifoProfile` | Cria um perfil com cálculo FIFO (First-In-First-Out) |
| `EditProfile` | Edita um perfil de preço médio |
| `DeleteProfile` | Remove um perfil e todas as suas linhas |
| `AddBuyLine` | Adiciona uma linha de compra (aquisição) a um perfil |
| `AddSellLine` | Adiciona uma linha de venda (alienação) a um perfil |
| `AddSetupLine` | Adiciona uma linha de setup (posição inicial) a um perfil |
| `EditLine` | Edita uma linha existente de um perfil |
| `DeleteLine` | Remove uma linha de um perfil |

### Relatórios (ReportTools)

<!-- Source: src/Valt.Infra/Mcp/Tools/ReportTools.cs -->
| Ferramenta | Descrição |
|------------|-----------|
| `GetMonthlyTotals` | Totais mensais de receitas, despesas e transações em bitcoin em um período |
| `GetWealthOverview` | Visão geral do patrimônio em fiat e BTC por período (diário, semanal, mensal, anual) |
| `GetExpensesByCategory` | Despesas por categoria em um período |
| `GetIncomeByCategory` | Receitas por categoria em um período |
| `GetAllTimeHigh` | Máxima histórica do patrimônio, com data e declínio atual em percentual |
| `GetMaxBtcStack` | Maior stack de BTC já acumulado, com data e declínio desde o pico |
| `GetStatistics` | Estatísticas financeiras: mediana de despesas mensais e cobertura do patrimônio em meses |

### Moedas (CurrencyTools)

<!-- Source: src/Valt.Infra/Mcp/Tools/CurrencyTools.cs -->
| Ferramenta | Descrição |
|------------|-----------|
| `GetAvailableCurrencies` | Lista as moedas fiat disponíveis e as atualmente em uso |
| `GetMainCurrency` | Retorna a moeda fiat principal configurada no aplicativo |
| `ConvertCurrency` | Converte valores entre moedas (USD, BRL, BTC, SATS etc.), usando cotações ao vivo quando disponíveis |
| `GetHistoricalPrice` | Preço histórico do BTC (em USD) ou de moedas fiat (relativo ao USD) em uma data |

### Ativos (AssetTools)

<!-- Source: src/Valt.Infra/Mcp/Tools/AssetTools.cs -->
Ferramentas para gerenciar **ativos** — investimentos externos rastreados separadamente das contas (ações, ETFs, criptomoedas, imóveis, posições alavancadas, empréstimos BTC e mais).

#### Operações de Ativos

| Ferramenta | Descrição |
|------------|-----------|
| `GetAssets` | Lista todos os ativos rastreados |
| `GetVisibleAssets` | Lista apenas os ativos visíveis |
| `GetAsset` | Obtém um ativo pelo seu ID |
| `GetAssetsSummary` | Resumo dos ativos com totais na moeda principal e em sats, incluindo ativos vs passivos |
| `CreateBasicAsset` | Cria um ativo básico (ação, ETF, cripto, commodity ou personalizado) |
| `CreateRealEstateAsset` | Cria um ativo imobiliário |
| `CreateLeveragedPosition` | Cria uma posição alavancada (futuros, perpétuos, margem) |
| `UpdateAssetPrice` | Atualiza o preço atual de um ativo |
| `UpdateAssetQuantity` | Atualiza a quantidade de um ativo básico |
| `ToggleAssetVisibility` | Alterna a visibilidade de um ativo |
| `ToggleAssetNetWorthInclusion` | Alterna a inclusão do ativo no cálculo de patrimônio líquido |
| `DeleteAsset` | Remove um ativo |

#### Empréstimos BTC

| Ferramenta | Descrição |
|------------|-----------|
| `CreateBtcLoan` | Cria um empréstimo com garantia em BTC, com LTV, saúde e juros; suporta APR diário ou dívida total fixa (estilo HodlHodl) |
| `CreateBtcLending` | Cria uma posição de empréstimo BTC/fiat (credor), com acompanhamento de juros |
| `RepayLoan` | Marca um empréstimo BTC ou posição de credor como quitado |

#### Grupos de Ativos

| Ferramenta | Descrição |
|------------|-----------|
| `GetAssetGroups` | Lista todos os grupos de ativos |
| `CreateAssetGroup` | Cria um grupo de ativos |
| `UpdateAssetGroup` | Atualiza o nome e a descrição de um grupo |
| `DeleteAssetGroup` | Remove um grupo; os ativos do grupo ficam sem grupo |
| `MoveAssetToGroup` | Move um ativo para um grupo |
| `RemoveAssetFromGroup` | Remove um ativo do seu grupo |

#### Linha do Tempo do Estado do Empréstimo

Cada empréstimo com garantia em BTC mantém uma linha do tempo de **snapshots** de estado; os cálculos atuais sempre usam o snapshot mais recente.

| Ferramenta | Descrição |
|------------|-----------|
| `AddLoanStateUpdate` | Adiciona um novo snapshot de estado a um empréstimo com garantia em BTC |
| `DeleteLoanStateUpdate` | Remove um snapshot de estado pela data efetiva |
| `GetLoanStateTimeline` | Retorna a linha do tempo cronológica completa de snapshots do empréstimo |
| `GetLatestLoanState` | Retorna o estado mais recente registrado do empréstimo |

**Parâmetros de `AddLoanStateUpdate`:**

| Parâmetro | Descrição |
|-----------|-----------|
| `assetId` | O ID do ativo |
| `effectiveDate` | Data efetiva (yyyy-MM-dd) |
| `totalBorrowed` | Principal tomado ainda devido na data do snapshot |
| `interestAccruedUntilDate` | Juros acumulados até a data do snapshot |
| `collateralSats` | Colateral em BTC, em satoshis |
| `apr` | APR como decimal (ex.: 0,12 para 12%) |
| `fees` | Taxas pagas |
| `note` | Observação (opcional) |

**Parâmetros de `DeleteLoanStateUpdate`:**

| Parâmetro | Descrição |
|-----------|-----------|
| `assetId` | O ID do ativo |
| `effectiveDate` | Data efetiva do snapshot a remover (yyyy-MM-dd) |

**Parâmetros de `GetLoanStateTimeline` e `GetLatestLoanState`:**

| Parâmetro | Descrição |
|-----------|-----------|
| `assetId` | O ID do ativo |

#### Ativos Vendidos

Marcar um ativo como vendido oculta o ativo da lista ativa e o move para o histórico, preservando o estado de visibilidade anterior para eventual restauração.

| Ferramenta | Descrição |
|------------|-----------|
| `MarkAssetAsSold` | Marca um ativo como vendido na data informada (padrão: hoje) |
| `UndoAssetSale` | Reverte uma venda e restaura o ativo à lista ativa |
| `ListSoldAssets` | Lista todos os ativos marcados como vendidos |

**Parâmetros de `MarkAssetAsSold`:**

| Parâmetro | Descrição |
|-----------|-----------|
| `assetId` | O ID do ativo a marcar como vendido |
| `dateSold` | Data da venda em yyyy-MM-dd (opcional, padrão: hoje) |

**Parâmetros de `UndoAssetSale`:**

| Parâmetro | Descrição |
|-----------|-----------|
| `assetId` | O ID do ativo vendido a restaurar |

`ListSoldAssets` não recebe parâmetros.

### Indicadores (IndicatorTools)

<!-- Source: src/Valt.Infra/Mcp/Tools/IndicatorTools.cs -->
Indicadores macro do Bitcoin, atualizados em segundo plano e servidos a partir de cache.

| Ferramenta | Descrição |
|------------|-----------|
| `GetBitcoinIndicators` | Retorna os indicadores macro atuais do Bitcoin: Mayer Multiple, Rainbow Chart, Fear & Greed Index e dominância do BTC |

## Casos de Uso 💡

### Consultando Dados

O servidor MCP permite que você faça perguntas em linguagem natural:

**Exemplos de perguntas:**

- "Qual meu patrimônio total em Bitcoin?"
- "Quanto gastei com alimentação este mês?"
- "Quais são minhas despesas fixas?"
- "Como está o progresso das minhas metas?"
- "Qual foi meu preço médio de compra de Bitcoin?"

**Exemplo de conversa:**

```
Você: Qual foi meu gasto total em dezembro?

IA: Vou verificar suas transações de dezembro...

Segundo os dados do Valt, em dezembro você teve:
- Total de despesas: R$ 4.523,45
- Maiores categorias:
  1. Alimentação: R$ 1.200,00
  2. Transporte: R$ 650,00
  3. Lazer: R$ 480,00
```

### Importação em Lote 📥

Uma das funcionalidades mais poderosas é a capacidade de importar transações usando linguagem natural. Você fornece um arquivo e descreve o formato - a IA entende e faz a importação.

#### Como Funciona

1. Você fornece um arquivo (extrato bancário, planilha, CSV)
2. Descreve o formato e o que cada coluna representa
3. A IA analisa, categoriza e importa as transações

#### Exemplo 1: Extrato Bancário em PDF

```
Você: [Anexa extrato do Nubank em PDF]
Preciso importar este extrato. É da minha conta Nubank em BRL.
As despesas são negativas e receitas positivas.

IA: Entendi! Vou analisar o extrato e importar as transações.

Encontrei 47 transações no período de 01/12 a 31/12:
- 35 despesas
- 8 receitas
- 4 transferências

Vou categorizar automaticamente baseado nas descrições:
- "SUPERMERCADO" → Alimentação
- "UBER" → Transporte
- "NETFLIX" → Assinaturas

Posso prosseguir com a importação?
```

#### Exemplo 2: CSV com Layout Personalizado

```
Você: Tenho este CSV do meu controle pessoal:

data;valor;tipo;obs
15/01;150,00;S;Mercado
16/01;5000,00;E;Salário
17/01;50,00;S;Uber

"S" significa saída, "E" significa entrada.
A conta é "Itaú [BRL]".

IA: Entendi o formato:
- Separador: ponto-e-vírgula
- Data: DD/MM (vou assumir o ano atual)
- Valor: formato brasileiro com vírgula
- S = despesa, E = receita

Vou importar 3 transações para a conta Itaú:
1. 15/01 - Mercado: -R$ 150,00 (Alimentação)
2. 16/01 - Salário: +R$ 5.000,00 (Salário)
3. 17/01 - Uber: -R$ 50,00 (Transporte)

Confirma?
```

#### Exemplo 3: Histórico de Exchange para Preço Médio

```
Você: [Anexa CSV da Binance]
Esse é meu histórico de trades da Binance.
Preciso adicionar ao perfil de preço médio "Bitcoin Principal".

IA: Analisando o histórico da Binance...

Encontrei 23 operações de BTC/BRL:
- 18 compras totalizando 0.15 BTC
- 5 vendas totalizando 0.02 BTC

Vou adicionar ao perfil "Bitcoin Principal":
- Preço médio atual do perfil: R$ 245.000
- Após importação: R$ 238.500 (média ponderada)

Posso adicionar as operações?
```

!!! tip "Dica de Importação"
    Quanto mais contexto você fornecer sobre o formato do arquivo, melhor será o resultado. Informe a moeda, o significado das colunas e qualquer padrão especial.

## Exemplos Práticos 📝

### Criando uma Meta via Conversa

```
Você: Quero criar uma meta para acumular 500 mil sats até o final do mês.

IA: Vou criar uma meta de "Acumular Bitcoin" para você:
- Tipo: Acumular Bitcoin
- Período: Mensal
- Mês: Janeiro/2025
- Alvo: 500.000 satoshis

Meta criada! Você pode acompanhar o progresso na aba Transações.
Atualmente você tem 125.000 sats acumulados este mês (25% do objetivo).
```

### Análise Financeira Completa

```
Você: Faça uma análise completa das minhas finanças deste mês.

IA: Analisando suas finanças de janeiro/2025...

📊 **RESUMO DO MÊS**

💰 **Patrimônio Total**: R$ 45.230,00
- Fiat: R$ 12.500,00 (28%)
- Bitcoin: 0.085 BTC ≈ R$ 32.730,00 (72%)

📈 **Receitas**: R$ 8.500,00
- Salário: R$ 7.000,00
- Freelance: R$ 1.500,00

📉 **Despesas**: R$ 5.890,00
- Alimentação: R$ 1.200,00 (20%)
- Moradia: R$ 1.800,00 (31%)
- Transporte: R$ 450,00 (8%)
- Lazer: R$ 640,00 (11%)
- Outros: R$ 1.800,00 (30%)

💾 **Sobra**: R$ 2.610,00 (31% da renda)

₿ **Bitcoin**
- Compras no mês: 0.015 BTC
- Preço médio de compra: R$ 378.000
- DCA realizado: 3 de 4 compras (75%)

🎯 **Metas**
- Acumular 1M sats: 65% ✓
- Limite gastos R$ 6.000: 98% ⚠️
```

## Solução de Problemas 🔧

### Servidor não inicia

**Sintoma**: O Valt não consegue iniciar o servidor MCP.

**Causas possíveis**:

1. **Porta em uso**: Outra aplicação está usando a porta 5200
   - **Solução**: Altere a porta nas configurações do Valt

2. **Firewall bloqueando**: O firewall está impedindo conexões locais
   - **Solução**: Adicione uma exceção para o Valt no firewall

### LLM não consegue conectar

**Sintoma**: O Claude Desktop ou outro LLM não encontra o servidor.

**Verificações**:

1. Confirme que o recurso MCP está habilitado em Configurações > Avançado e que o servidor está ligado na tela principal
2. Verifique se a URL está correta: `http://localhost:5200/mcp`
3. Teste acessando a URL no navegador (deve retornar dados de conexão)
4. Reinicie tanto o Valt quanto o aplicativo LLM

### Ferramentas não aparecem

**Sintoma**: O LLM conecta mas não mostra as ferramentas do Valt.

**Soluções**:

1. Reinicie o aplicativo LLM completamente
2. Verifique os logs do Valt para erros
3. Confirme que a configuração MCP está correta

### Dados não atualizam na interface

**Sintoma**: Transações criadas via MCP não aparecem na interface do Valt.

**Solução**: Atualize a visualização no Valt (navegue para outra aba e volte, ou reinicie o aplicativo). As transações são salvas imediatamente, mas a interface pode precisar de um refresh.

## Próximos Passos

- [Transações](transacoes.md) - Entenda os tipos de transações
- [Importar e Exportar](importar-exportar.md) - Importação tradicional via CSV
- [Relatórios](relatorios.md) - Análise visual das finanças
- [Preço Médio](preco-medio.md) - Controle seu custo de aquisição de Bitcoin
- [Ativos](ativos.md) - Investimentos externos, empréstimos BTC e histórico de ativos vendidos
