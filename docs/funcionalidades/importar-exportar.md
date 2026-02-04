# Importar e Exportar 📥📤

O Valt permite importar e exportar suas transações em formato CSV, facilitando a migração de dados, backups e integração com planilhas.

## Visão Geral

| Funcionalidade | Descrição |
|----------------|-----------|
| **Importar** | Carrega transações de um arquivo CSV através de um assistente guiado |
| **Exportar** | Salva todas as transações em um arquivo CSV |

Ambas as funcionalidades usam o mesmo formato de CSV, permitindo que você exporte dados do Valt e importe novamente sem perda de informação.

## Importar Transações 📥

### Acessando o Assistente

1. No menu principal, clique em **Importar Transações**
2. O assistente de importação será aberto

### Passo 1: Seleção do Arquivo

Nesta etapa você seleciona o arquivo CSV para importar.

**Opções disponíveis:**

- **Selecionar Arquivo**: Escolha um arquivo CSV do seu computador
- **Baixar Template**: Baixa um modelo de CSV com exemplos de todos os tipos de transação

Após selecionar o arquivo, o Valt irá validar o conteúdo e mostrar:

- ✅ Quantidade de linhas válidas
- ❌ Quantidade de erros de parsing (se houver)

!!! tip "Template de Exemplo"
    Se é sua primeira vez importando, baixe o template primeiro. Ele contém exemplos de todos os tipos de transação suportados.

!!! warning "Erros de Parsing"
    Se houver erros, você pode expandir a lista para ver os detalhes. Corrija os erros no arquivo CSV e selecione novamente.

### Passo 2: Mapeamento de Contas

O Valt detecta automaticamente as contas do arquivo CSV e as mapeia para contas existentes ou novas.

**Detecção automática:**

- Contas com `[btc]` são detectadas como contas Bitcoin
- Contas com código de moeda (ex: `[USD]`, `[BRL]`) são detectadas como contas fiat

**Resumo exibido:**

| Informação | Descrição |
|------------|-----------|
| **Contas novas** | Serão criadas durante a importação |
| **Contas existentes** | Já existem no Valt e serão reutilizadas |

!!! info "Correspondência Automática"
    O Valt tenta corresponder nomes de contas do CSV com contas existentes (ignorando maiúsculas/minúsculas). Se encontrar uma correspondência, a conta existente será usada.

### Passo 3: Prévia de Categorias

Similar ao mapeamento de contas, o Valt mostra as categorias encontradas no CSV.

**Resumo exibido:**

| Informação | Descrição |
|------------|-----------|
| **Categorias novas** | Serão criadas durante a importação |
| **Categorias existentes** | Já existem no Valt e serão reutilizadas |

### Passo 4: Resumo

Antes de executar a importação, você verá um resumo completo:

- Total de transações a importar
- Total de contas (novas destacadas)
- Total de categorias (novas destacadas)

Revise os números e clique em **Importar** para continuar.

### Passo 5: Progresso

Durante a importação você verá:

- Barra de progresso animada
- Ação atual sendo executada
- Contador de transações importadas

Ao finalizar, uma mensagem de sucesso será exibida e você pode fechar o assistente.

## Formato do Arquivo CSV 📄

### Colunas Obrigatórias

| Coluna | Formato | Descrição |
|--------|---------|-----------|
| `date` | YYYY-MM-DD | Data da transação |
| `description` | Texto | Descrição da transação |
| `amount` | Número | Valor (negativo = saída, positivo = entrada) |
| `account` | Texto [MOEDA] | Conta de origem com moeda entre colchetes |
| `category` | Texto | Nome da categoria |

### Colunas Opcionais

| Coluna | Formato | Descrição |
|--------|---------|-----------|
| `to_account` | Texto [MOEDA] | Conta de destino (para transferências) |
| `to_amount` | Número | Valor na conta de destino (para trocas) |

### Formato de Nome de Conta

O nome da conta deve incluir o tipo de moeda entre colchetes:

| Tipo | Formato | Exemplo |
|------|---------|---------|
| **Fiat** | `Nome [MOEDA]` | `Nubank [BRL]`, `Chase [USD]` |
| **Bitcoin** | `Nome [btc]` | `Ledger [btc]`, `Binance [btc]` |

### Formato de Valores

| Tipo | Formato | Exemplo |
|------|---------|---------|
| **Fiat** | 2 casas decimais | `150.00`, `-35.50` |
| **Bitcoin** | 8 casas decimais | `0.00100000`, `-0.05000000` |

## Exemplos de Transações 📝

### Despesa Fiat

```csv
date,description,amount,account,to_account,to_amount,category
2024-01-15,Supermercado,-150.00,Nubank [BRL],,,"Alimentação"
```

### Receita Fiat

```csv
date,description,amount,account,to_account,to_amount,category
2024-01-16,Salário,5000.00,Itaú [BRL],,,"Salário"
```

### Receita Bitcoin

```csv
date,description,amount,account,to_account,to_amount,category
2024-01-21,Mining,0.00100000,Ledger [btc],,,"Receita"
```

### Transferência Fiat para Fiat

```csv
date,description,amount,account,to_account,to_amount,category
2024-01-19,TED entre bancos,-1000.00,Nubank [BRL],Itaú [BRL],1000.00,"Transferência"
```

### Transferência Bitcoin para Bitcoin

```csv
date,description,amount,account,to_account,to_amount,category
2024-01-20,Consolidação,-0.05000000,Binance [btc],Ledger [btc],0.05000000,"Transferência"
```

### Compra de Bitcoin (Fiat para Bitcoin)

```csv
date,description,amount,account,to_account,to_amount,category
2024-01-17,Compra de BTC,-500.00,Nubank [BRL],Ledger [btc],0.00850000,"Investimento"
```

### Venda de Bitcoin (Bitcoin para Fiat)

```csv
date,description,amount,account,to_account,to_amount,category
2024-01-18,Venda de BTC,-0.01000000,Ledger [btc],Nubank [BRL],450.00,"Trading"
```

## Exportar Transações 📤

### Como Exportar

1. No menu principal, clique em **Exportar Transações**
2. Escolha o local e nome do arquivo
3. Clique em **Salvar**

O arquivo será salvo com todas as suas transações.

### O Que É Exportado

O arquivo CSV exportado contém:

1. **Saldos Iniciais**: Para cada conta com saldo inicial, uma linha especial com categoria `InitialValue`
2. **Todas as Transações**: Ordenadas por data, no formato compatível com importação

### Exemplo de Arquivo Exportado

```csv
date,description,amount,account,to_account,to_amount,category
2024-01-01,InitialValue,5000.00,Nubank [BRL],,,"InitialValue"
2024-01-01,InitialValue,0.05000000,Ledger [btc],,,"InitialValue"
2024-01-15,Supermercado,-150.00,Nubank [BRL],,,"Alimentação"
2024-01-16,Salário,5000.00,Itaú [BRL],,,"Salário"
```

!!! info "Categoria InitialValue"
    A categoria `InitialValue` é reservada pelo sistema. Ao importar, linhas com essa categoria definem o saldo inicial da conta em vez de criar uma transação.

## Casos de Uso 💡

### Backup dos Dados

1. Exporte suas transações periodicamente
2. Guarde o arquivo CSV em local seguro
3. Em caso de necessidade, importe o arquivo de volta

### Migração entre Computadores

1. No computador antigo, exporte as transações
2. No computador novo, instale o Valt
3. Importe o arquivo CSV

### Integração com Planilhas

O formato CSV permite:

- Abrir no Excel ou Google Sheets
- Fazer análises personalizadas
- Criar gráficos customizados
- Editar em massa e reimportar

### Importar de Outros Apps

Se você tem dados em outro aplicativo financeiro:

1. Exporte do app original para CSV
2. Ajuste as colunas para o formato do Valt
3. Importe no Valt

## Boas Práticas ✨

### Antes de Importar

- Faça um backup exportando os dados atuais
- Teste com poucas transações primeiro
- Verifique se as datas estão no formato correto (YYYY-MM-DD)
- Confirme que os valores Bitcoin têm 8 casas decimais

### Nomes de Conta

- Use nomes consistentes com as contas existentes
- Sempre inclua a moeda entre colchetes
- Para Bitcoin, sempre use `[btc]` em minúsculas

### Categorias

- Use nomes de categorias existentes quando possível
- Evite criar categorias duplicadas com grafias diferentes

## Solução de Problemas 🔧

### Erro "Data inválida"

**Causa**: A data não está no formato YYYY-MM-DD

**Solução**: Use o formato ano-mês-dia (ex: `2024-01-15`)

### Erro "Conta não reconhecida"

**Causa**: O nome da conta não tem o código de moeda entre colchetes

**Solução**: Adicione `[BRL]`, `[USD]`, `[btc]`, etc. ao final do nome

### Erro "Valor inválido"

**Causa**: O valor contém caracteres inválidos ou formatação incorreta

**Solução**: Use apenas números e ponto decimal (ex: `150.00`, não `R$ 150,00`)

### Transações duplicadas após importar

**Causa**: Você importou o mesmo arquivo mais de uma vez

**Solução**: O Valt não detecta duplicatas automaticamente. Exclua as transações duplicadas manualmente ou restaure um backup anterior.

## Próximos Passos

- [Transações](transacoes.md) - Gerencie suas transações manualmente
- [Contas](contas.md) - Organize suas contas
- [Relatórios](relatorios.md) - Analise suas finanças
