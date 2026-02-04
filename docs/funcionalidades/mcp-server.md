# Servidor MCP 🤖

O Valt inclui um servidor MCP (Model Context Protocol) integrado que permite a interação com suas finanças usando linguagem natural através de modelos de IA. Com mais de 45 ferramentas disponíveis, você pode consultar dados, criar transações, gerenciar contas e muito mais - tudo através de conversas com sua IA favorita.

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
2. Acesse **Configurações** > **Avançado**
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

O servidor MCP do Valt expõe mais de 45 ferramentas organizadas por categoria.

### Contas (AccountTools)

| Ferramenta | Descrição |
|------------|-----------|
| `GetAccounts` | Lista todas as contas |
| `CreateAccount` | Cria uma nova conta |
| `EditAccount` | Edita uma conta existente |
| `DeleteAccount` | Remove uma conta |
| `GetAccountBalance` | Obtém o saldo de uma conta |
| `GetAccountHistory` | Histórico de saldo de uma conta |

### Transações (TransactionTools)

| Ferramenta | Descrição |
|------------|-----------|
| `GetTransactions` | Lista transações com filtros |
| `AddFiatExpense` | Adiciona despesa em fiat |
| `AddFiatIncome` | Adiciona receita em fiat |
| `AddBitcoinExpense` | Adiciona despesa em Bitcoin |
| `AddBitcoinIncome` | Adiciona receita em Bitcoin |
| `AddFiatToFiatTransfer` | Transferência entre contas fiat |
| `AddBitcoinToBitcoinTransfer` | Transferência entre wallets |
| `AddBitcoinPurchase` | Compra de Bitcoin |

### Categorias (CategoryTools)

| Ferramenta | Descrição |
|------------|-----------|
| `GetCategories` | Lista todas as categorias |
| `CreateCategory` | Cria uma nova categoria |
| `EditCategory` | Edita uma categoria |
| `DeleteCategory` | Remove uma categoria |

### Despesas Fixas (FixedExpenseTools)

| Ferramenta | Descrição |
|------------|-----------|
| `GetFixedExpenses` | Lista despesas fixas |
| `CreateFixedExpense` | Cria despesa fixa |
| `EditFixedExpense` | Edita despesa fixa |
| `DeleteFixedExpense` | Remove despesa fixa |
| `GetFixedExpenseHistory` | Histórico de pagamentos |

### Metas (GoalTools)

| Ferramenta | Descrição |
|------------|-----------|
| `GetGoals` | Lista todas as metas |
| `CreateStackBitcoinGoal` | Meta de acumular Bitcoin |
| `CreateDCAGoal` | Meta de DCA |
| `CreateFiatIncomeGoal` | Meta de renda em fiat |
| `CreateBitcoinIncomeGoal` | Meta de renda em Bitcoin |
| `CreateSpendingLimitGoal` | Meta de limite de gastos |
| `CreateReduceCategoryGoal` | Meta de reduzir categoria |
| `CreateHodlBitcoinGoal` | Meta HODL |

### Preço Médio (AvgPriceTools)

| Ferramenta | Descrição |
|------------|-----------|
| `GetAvgPriceProfiles` | Lista perfis de preço médio |
| `CreateAvgPriceProfile` | Cria perfil |
| `EditAvgPriceProfile` | Edita perfil |
| `DeleteAvgPriceProfile` | Remove perfil |
| `GetAvgPriceLines` | Lista linhas de um perfil |
| `AddAvgPriceBuyLine` | Adiciona compra |
| `AddAvgPriceSellLine` | Adiciona venda |
| `AddAvgPriceTransferInLine` | Adiciona entrada |
| `AddAvgPriceTransferOutLine` | Adiciona saída |
| `EditAvgPriceLine` | Edita linha |
| `DeleteAvgPriceLine` | Remove linha |

### Relatórios (ReportTools)

| Ferramenta | Descrição |
|------------|-----------|
| `GetMonthlyTotals` | Totais mensais por categoria |
| `GetWealthOverview` | Visão geral do patrimônio |
| `GetWealthHistory` | Histórico de evolução patrimonial |
| `GetCategoryStatistics` | Estatísticas por categoria |
| `GetIncomeVsExpenses` | Comparativo receita x despesa |
| `GetTopExpenseCategories` | Categorias com mais gastos |

### Moedas (CurrencyTools)

| Ferramenta | Descrição |
|------------|-----------|
| `GetSupportedCurrencies` | Lista moedas suportadas |
| `GetExchangeRate` | Taxa de câmbio atual |
| `GetHistoricalPrice` | Preço histórico |
| `ConvertCurrency` | Converte valores entre moedas |

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
