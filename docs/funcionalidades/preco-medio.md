# Preço Médio 📊

O módulo de Preço Médio (ou Custo Médio de Aquisição) é uma ferramenta essencial para quem investe em Bitcoin e precisa calcular quanto pagou, em média, pelos seus bitcoins.

## Por Que Calcular o Preço Médio 🎯

### Controle Pessoal

Saber seu preço médio permite:

- Entender se você está no lucro ou prejuízo
- Avaliar o momento de comprar mais
- Tomar decisões informadas sobre vendas

### Declaração de Imposto de Renda (Brasil)

No Brasil, para declarar ganho de capital na venda de Bitcoin, você precisa:

1. Conhecer o custo de aquisição (preço médio)
2. Calcular o ganho: Valor de Venda - Custo de Aquisição
3. Pagar imposto sobre o ganho (se aplicável)

!!! warning "Importante"
    Vendas acima de R$ 35.000 por mês podem estar sujeitas a imposto sobre ganho de capital. Consulte um contador para orientação específica.

## Métodos de Cálculo 🧮

O Valt oferece dois métodos de cálculo:

### 🇧🇷 Regra Brasileira

**Como funciona**:

1. A cada compra, o preço médio é recalculado
2. Fórmula: `(Estoque Anterior × Preço Médio Anterior + Nova Compra) ÷ Novo Estoque Total`
3. Vendas não alteram o preço médio, apenas reduzem o estoque

**Exemplo**:

| Data | Operação | Qtd BTC | Valor R$ | Estoque | Preço Médio |
|------|----------|---------|----------|---------|-------------|
| Jan | Compra | 0.1 | 5.000 | 0.1 | 50.000 |
| Fev | Compra | 0.2 | 8.000 | 0.3 | 43.333 |
| Mar | Venda | -0.05 | 3.000 | 0.25 | 43.333 |
| Abr | Compra | 0.1 | 6.000 | 0.35 | 45.714 |

### 🌎 FIFO (First In, First Out)

Método internacional onde as primeiras unidades compradas são consideradas as primeiras vendidas.

**Como funciona**:

1. Cada compra mantém seu preço individual
2. Ao vender, usa-se o preço das compras mais antigas primeiro
3. Útil para quem segue regras fiscais de outros países

**Exemplo**:

| Data | Operação | Qtd BTC | Valor R$ | Lotes Disponíveis |
|------|----------|---------|----------|-------------------|
| Jan | Compra | 0.1 | 5.000 | [0.1 @ 50k] |
| Fev | Compra | 0.2 | 8.000 | [0.1 @ 50k, 0.2 @ 40k] |
| Mar | Venda | -0.15 | - | [0.15 @ 40k] |

Na venda de Mar, foram usados:
- 0.1 BTC da compra de Jan (custo: R$ 5.000)
- 0.05 BTC da compra de Fev (custo: R$ 2.000)

## Criando um Perfil de Preço Médio

O Valt permite criar múltiplos perfis de preço médio (ex: um para cada corretora ou um consolidado).

### Passo a Passo

1. Vá para a aba **Preço Médio**
2. Clique em **Novo Perfil** ou **Gerenciar Perfis**
3. Preencha:

| Campo | Descrição |
|-------|-----------|
| **Nome** | Identificação do perfil (ex: "Binance", "Consolidado") |
| **Método** | Regra Brasileira ou FIFO |
| **Moeda** | Moeda de referência (geralmente BRL) |

4. Clique em **Criar**

## Adicionando Linhas

Cada operação de compra ou venda é uma "linha" no perfil.

### Tipos de Linha

| Tipo | Uso |
|------|-----|
| **Compra** | Aquisição de Bitcoin |
| **Venda** | Venda de Bitcoin |
| **Setup** | Configuração inicial (saldo anterior) |

### Lançando uma Compra

1. No perfil, clique em **Adicionar Linha**
2. Selecione **Compra**
3. Preencha:

| Campo | Descrição |
|-------|-----------|
| **Data** | Quando comprou |
| **Quantidade** | Quantos BTC (ou sats) |
| **Valor** | Quanto pagou em R$ |
| **Comentário** | (Opcional) Observações |

4. Clique em **Salvar**

### Lançando uma Venda

1. Clique em **Adicionar Linha**
2. Selecione **Venda**
3. Preencha:

| Campo | Descrição |
|-------|-----------|
| **Data** | Quando vendeu |
| **Quantidade** | Quantos BTC vendeu |
| **Valor** | Quanto recebeu em R$ |
| **Comentário** | (Opcional) Observações |

4. Clique em **Salvar**

### Setup Inicial

Se você já tinha Bitcoin antes de começar a usar o Valt:

1. Clique em **Adicionar Linha**
2. Selecione **Setup**
3. Preencha:
   - **Data**: Data de referência
   - **Quantidade**: Quanto você tinha
   - **Valor**: Custo total de aquisição (se souber)
4. Clique em **Salvar**

## Visualizando os Cálculos

Após adicionar linhas, o Valt mostra:

### Resumo do Perfil

- **Estoque atual**: Quantos BTC você tem
- **Custo total**: Quanto pagou no total
- **Preço médio**: Custo por BTC

### Tabela de Operações

Todas as linhas com:
- Data
- Tipo (Compra/Venda/Setup)
- Quantidade
- Valor
- Preço médio após operação
- Estoque após operação

### Ganho/Perda em Vendas

Para cada venda, o Valt calcula:
- Custo de aquisição (usando preço médio)
- Valor de venda
- Ganho ou perda

## Integração com Transações

!!! tip "Dica"
    O módulo de Preço Médio é **separado** das transações normais. Isso permite mais flexibilidade, mas requer que você mantenha os dois sincronizados se quiser.

### Por Que São Separados

- Transações = fluxo de caixa (de onde vem e para onde vai o dinheiro)
- Preço Médio = controle fiscal (custo de aquisição)

Você pode ter transações de compra de BTC e também lançar no perfil de preço médio, mas são registros independentes.

## Exportação para IR 📄

O Valt pode gerar relatórios úteis para a declaração de IR:

- Lista de operações do ano
- Preço médio atual
- Ganhos/perdas em vendas

!!! note "Nota"
    O Valt é uma ferramenta de auxílio. A responsabilidade pela declaração correta é sua. Consulte um contador se tiver dúvidas.

## Múltiplos Perfis

Você pode criar vários perfis para diferentes finalidades:

### Por Corretora

- Perfil "Binance"
- Perfil "Mercado Bitcoin"
- Perfil "P2P"

### Por Carteira

- Perfil "Trading"
- Perfil "Hold de longo prazo"

### Consolidado

- Um único perfil com todas as operações

## Boas Práticas ✨

### Mantenha Atualizado

Lance suas compras e vendas assim que ocorrerem. É mais fácil do que tentar reconstruir o histórico depois.

### Guarde Comprovantes

Mantenha notas fiscais, comprovantes de transferência e extratos. Eles podem ser necessários em caso de fiscalização.

### Confira os Cálculos

Periodicamente, verifique se o estoque no Valt bate com o que você realmente tem nas wallets.

### Separe Trading de Hold

Se você faz trading e também hold de longo prazo, considere perfis separados para facilitar a análise.

## Cenários Comuns 📋

### Começando do Zero

1. Crie um perfil com o método desejado
2. Lance cada compra como uma linha
3. O preço médio é calculado automaticamente

### Migrando de Outro Sistema

1. Crie um perfil
2. Use uma linha de **Setup** com seu saldo e custo atual
3. Continue lançando novas operações normalmente

### Consolidando Várias Corretoras

1. Crie um perfil "Consolidado"
2. Lance todas as operações de todas as corretoras
3. O Valt calcula o preço médio geral

## Próximos Passos

- [Transações](transacoes.md) - Lançando compras e vendas
- [Relatórios](relatorios.md) - Análises do patrimônio
- [FAQ](../referencia/faq.md) - Perguntas frequentes
