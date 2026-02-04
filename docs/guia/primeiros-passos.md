# Primeiros Passos 🚀

Este guia vai ajudá-lo a configurar o Valt e começar a gerenciar suas finanças em poucos minutos.

## Visão Geral da Interface 🖥️

Ao abrir o Valt, você verá três abas principais na parte superior:

1. **Transações** - Onde você gerencia contas e lança transações
2. **Relatórios** - Gráficos e análises dos seus dados
3. **Preço Médio** - Cálculo de custo de aquisição de Bitcoin

## Passo 1: Criar Suas Contas 🏦

Antes de lançar transações, você precisa criar as contas que representam onde seu dinheiro está.

### Criando uma Conta em Moeda Fiat

1. Na aba **Transações**, localize a seção de contas
2. Clique no botão **+** para adicionar uma nova conta
3. Selecione **Conta Fiat**
4. Preencha os campos:
   - **Nome**: Ex: "Nubank", "Itaú", "Carteira"
   - **Moeda**: Selecione a moeda (Real, Dólar, Euro, etc.)
   - **Saldo Inicial**: O valor atual na conta (opcional)
   - **Ícone**: Escolha um ícone para identificar a conta
5. Clique em **Salvar**

### Criando uma Conta Bitcoin ₿

1. Clique no botão **+** para adicionar uma nova conta
2. Selecione **Conta Bitcoin**
3. Preencha os campos:
   - **Nome**: Ex: "Ledger", "Bitfinex", "Cold Wallet"
   - **Saldo Inicial**: O valor em satoshis ou BTC (opcional)
   - **Ícone**: Escolha um ícone
4. Clique em **Salvar**

!!! tip "Quantas contas criar?"
    Crie uma conta para cada lugar onde você mantém dinheiro: bancos, corretoras, carteiras Bitcoin, dinheiro em espécie, etc. Isso ajuda a ter uma visão completa do seu patrimônio.

## Passo 2: Configurar Categorias 🏷️

O Valt já vem com categorias padrão, mas você pode personalizá-las.

1. Acesse o menu de configurações
2. Clique em **Gerenciar Categorias**
3. Aqui você pode:
   - Adicionar novas categorias
   - Editar categorias existentes
   - Criar subcategorias (categorias dentro de categorias)
   - Escolher ícones e cores

Exemplos de categorias úteis:

- **Receitas**: Salário, Freelance, Investimentos
- **Despesas**: Alimentação, Transporte, Moradia, Lazer
- **Transferências**: Entre contas

## Passo 3: Lançar Sua Primeira Transação 📝

Agora vamos registrar uma transação.

### Lançando uma Despesa

1. Na aba **Transações**, clique no botão de **Nova Transação**
2. Selecione o tipo **Despesa em Fiat**
3. Preencha:
   - **Data**: Quando ocorreu a despesa
   - **Conta**: De qual conta saiu o dinheiro
   - **Valor**: Quanto foi gasto
   - **Categoria**: Onde se encaixa essa despesa
   - **Descrição**: (Opcional) Detalhes sobre a transação
4. Clique em **Salvar**

### Lançando uma Compra de Bitcoin

1. Clique em **Nova Transação**
2. Selecione o tipo **Fiat para Bitcoin**
3. Preencha:
   - **Data**: Quando comprou
   - **Conta Fiat**: De onde saiu o dinheiro
   - **Conta Bitcoin**: Para onde foram os bitcoins
   - **Valor Fiat**: Quanto pagou em reais/dólares
   - **Valor Bitcoin**: Quantos satoshis/BTC recebeu
4. Clique em **Salvar**

!!! info "Valor em Satoshis"
    O Valt busca automaticamente a cotação do Bitcoin na data da transação. Se você lançar uma despesa em reais, o sistema calculará automaticamente quanto isso representava em satoshis naquele dia.

## Passo 4: Explorar os Relatórios 📊

Com algumas transações lançadas, vá para a aba **Relatórios** para visualizar:

### Totais Mensais
Veja suas receitas e despesas mês a mês em um gráfico de barras.

### Gastos por Categoria
Entenda para onde está indo seu dinheiro com um gráfico de pizza mostrando a distribuição por categoria.

### All-Time High
Acompanhe o pico do seu patrimônio em termos de Bitcoin.

### Estatísticas
Veja métricas como mediana de gastos e cobertura de patrimônio.

## Passo 5: Configurar Despesas Fixas (Opcional) 🔄

Se você tem gastos recorrentes, configure-os para facilitar o lançamento:

1. Na aba **Transações**, acesse **Despesas Fixas**
2. Clique em **Adicionar Despesa Fixa**
3. Preencha:
   - **Nome**: Ex: "Netflix", "Aluguel", "Academia"
   - **Valor**: Quanto paga
   - **Frequência**: Mensal, Semanal, Quinzenal ou Anual
   - **Conta**: De qual conta é debitado
   - **Categoria**: Como categorizar
4. Clique em **Salvar**

Com despesas fixas configuradas, você pode lançar rapidamente esses gastos recorrentes.

## Próximos Passos

Agora que você conhece o básico, explore:

- [Conceitos Básicos](conceitos-basicos.md) - Entenda melhor como o Valt funciona
- [Transações](../funcionalidades/transacoes.md) - Todos os tipos de transações disponíveis
- [Preço Médio](../funcionalidades/preco-medio.md) - Configure o cálculo de custo de aquisição

## Dicas Finais 💡

1. **Seja consistente**: Lance suas transações regularmente para ter dados precisos
2. **Use categorias**: Uma boa categorização facilita a análise posterior
3. **Faça backup**: Copie periodicamente seu arquivo `.valt` para um local seguro
4. **Explore os relatórios**: Os gráficos revelam padrões que você não perceberia olhando transações individuais
