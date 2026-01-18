# Metas 🎯

As metas permitem que você defina objetivos financeiros e acompanhe automaticamente seu progresso. Seja para acumular Bitcoin, controlar gastos ou manter uma rotina de DCA, o Valt calcula seu avanço em tempo real.

## O Que São Metas

Metas são objetivos financeiros com prazo definido que o Valt monitora automaticamente. Você define o que quer alcançar e o sistema acompanha suas transações para calcular o progresso.

## Tipos de Meta Disponíveis

O Valt oferece diferentes tipos de meta para diferentes objetivos:

### Metas de Progresso (Acumulação)

Essas metas começam em 0% e aumentam conforme você avança. Ao atingir 100%, a meta é marcada como **concluída**.

| Tipo | Descrição | Exemplo |
|------|-----------|---------|
| **Acumular Bitcoin** | Juntar uma quantidade de satoshis | "Acumular 1 milhão de sats este mês" |
| **DCA** | Realizar um número de compras de Bitcoin | "Fazer 4 compras de BTC este mês" |
| **Renda em Fiat** | Atingir um valor de receita em moeda fiduciária | "Receber R$ 10.000 este mês" |
| **Renda em Bitcoin** | Receber uma quantidade de satoshis | "Receber 500.000 sats de renda este mês" |

### Metas de Limite (Controle)

Essas metas também começam em 0%, mas aumentam conforme você se aproxima do limite. Ao atingir 100%, a meta é marcada como **falha**.

| Tipo | Descrição | Exemplo |
|------|-----------|---------|
| **Limite de Gastos** | Não ultrapassar um valor de despesas | "Gastar no máximo R$ 3.000 este mês" |
| **Reduzir Categoria** | Limitar gastos em uma categoria específica | "Gastar no máximo R$ 500 em delivery" |
| **HODL Bitcoin** | Limitar a venda de Bitcoin | "Vender no máximo 100.000 sats" |

## Como Funciona o Progresso

### Metas de Acumulação (Barra Verde)

- Progresso começa em **0%**
- Aumenta conforme você faz transações relacionadas
- Ao atingir **100%**, a meta é automaticamente marcada como **Concluída**
- A barra de progresso é verde

**Exemplo - Acumular Bitcoin:**
```
Meta: Acumular 1.000.000 sats
Progresso atual: 250.000 sats acumulados
Barra de progresso: 25% (verde)
```

### Metas de Limite (Barra Vermelha)

- Progresso começa em **0%** (nada gasto = bom)
- Aumenta conforme você gasta/vende
- Ao atingir **100%**, a meta é automaticamente marcada como **Falha**
- A barra de progresso é vermelha
- Metas de limite de gastos podem ultrapassar 100%

**Exemplo - Limite de Gastos:**
```
Meta: Gastar no máximo R$ 2.000
Progresso atual: R$ 1.000 gastos
Barra de progresso: 50% (vermelho)
```

## Períodos Disponíveis

| Período | Descrição |
|---------|-----------|
| **Mensal** | Meta válida para um mês específico |
| **Anual** | Meta válida para um ano inteiro |

## Criando uma Meta

1. Acesse a aba **Transações**
2. Na seção de **Metas**, clique em **Nova Meta**
3. Selecione o **período** (Mensal ou Anual)
4. Escolha o **mês/ano de referência**
5. Selecione o **tipo de meta**
6. Configure os parâmetros específicos do tipo escolhido
7. Clique em **Salvar**

### Configuração por Tipo

#### Acumular Bitcoin
- **Valor alvo**: Quantidade de satoshis que deseja acumular

#### DCA (Dollar Cost Average)
- **Número de compras**: Quantidade de compras de Bitcoin que deseja fazer

#### Renda em Fiat
- **Valor alvo**: Quanto deseja receber
- **Moeda**: Em qual moeda

#### Renda em Bitcoin
- **Valor alvo**: Quantidade de satoshis que deseja receber como renda

#### Limite de Gastos
- **Valor limite**: Quanto pode gastar no máximo
- **Moeda**: Em qual moeda

#### Reduzir Categoria
- **Valor limite**: Quanto pode gastar no máximo
- **Categoria**: Qual categoria deseja controlar

#### HODL Bitcoin
- **Limite de venda**: Máximo de satoshis que pode vender (0 = HODL total)

## Estados da Meta

Uma meta pode estar em três estados:

| Estado | Descrição | Exibição |
|--------|-----------|----------|
| **Em Aberto** | Meta ainda em andamento | Barra de progresso |
| **Concluída** | Meta de acumulação atingiu 100% | Badge "SUCESSO" (verde) |
| **Falha** | Meta de limite atingiu 100% | Badge "FALHA" (vermelho) |

## Gerenciando Metas

### Editando

1. Clique na meta desejada
2. Clique em **Editar**
3. Modifique os parâmetros
4. Salve

!!! note "Nota"
    Ao editar uma meta, o progresso calculado é preservado e será recalculado automaticamente.

### Excluindo

1. Clique na meta desejada
2. Clique em **Excluir**
3. Confirme

### Recalculando

Se uma meta foi marcada como Concluída ou Falha, mas você deseja recalcular:

1. Clique com o botão direito na meta
2. Selecione **Recalcular**
3. A meta volta ao estado "Em Aberto" e o progresso é recalculado

Isso é útil quando você edita transações do passado que afetam a meta.

## Cálculo Automático

O Valt recalcula automaticamente o progresso das suas metas quando:

- Uma nova transação é criada
- Uma transação é editada
- Uma transação é excluída
- Preços de cotação são atualizados (para metas que envolvem conversão de moedas)

!!! info "Metas com Múltiplas Moedas"
    Metas de **Renda em Fiat**, **Limite de Gastos** e **Reduzir Categoria** utilizam dados de cotação para converter transações em diferentes moedas. Essas metas exibem um asterisco (*) indicando que dependem de dados de preço.

## Visualização

As metas são exibidas na aba de Transações e são organizadas na seguinte ordem:

1. Metas mensais em aberto
2. Metas anuais em aberto
3. Metas concluídas
4. Metas com falha

A barra de progresso é animada, mostrando de forma suave a transição quando o progresso muda.

## Exemplos de Uso 💡

### Estratégia de Acumulação

**Meta Mensal de DCA:**
- **Tipo**: DCA
- **Período**: Mensal
- **Alvo**: 4 compras
- **Objetivo**: Garantir que você faça pelo menos uma compra por semana

**Meta Anual de Acumulação:**
- **Tipo**: Acumular Bitcoin
- **Período**: Anual
- **Alvo**: 10.000.000 sats (0.1 BTC)
- **Objetivo**: Acumular um valor significativo ao longo do ano

### Controle de Gastos

**Orçamento Mensal:**
- **Tipo**: Limite de Gastos
- **Período**: Mensal
- **Limite**: R$ 5.000
- **Objetivo**: Não ultrapassar seu orçamento mensal

**Controle de Categoria:**
- **Tipo**: Reduzir Categoria
- **Período**: Mensal
- **Categoria**: Alimentação > Delivery
- **Limite**: R$ 400
- **Objetivo**: Reduzir gastos com delivery

### Preservação de Bitcoin

**HODL Total:**
- **Tipo**: HODL Bitcoin
- **Período**: Anual
- **Limite de venda**: 0 sats
- **Objetivo**: Não vender nenhum Bitcoin durante o ano (qualquer venda marcará a meta como falha)

**HODL Parcial:**
- **Tipo**: HODL Bitcoin
- **Período**: Mensal
- **Limite de venda**: 500.000 sats
- **Objetivo**: Limitar vendas emergenciais

## Boas Práticas ✨

### Defina Metas Realistas

- Comece com metas alcançáveis
- Aumente gradualmente conforme você ganha confiança
- Use o histórico de metas para calibrar suas expectativas

### Combine Diferentes Tipos

- Use metas de acumulação para objetivos de longo prazo
- Use metas de limite para controle do dia a dia
- Crie metas mensais e anuais complementares

### Revise Periodicamente

- No início de cada mês, crie suas metas mensais
- No início do ano, defina metas anuais
- Analise metas passadas para aprender com seu histórico

### Use Categorias a Seu Favor

Para metas do tipo "Reduzir Categoria":
- Crie categorias específicas para gastos que deseja controlar
- Exemplo: Crie "Lazer > Delivery" para monitorar pedidos de comida

## Próximos Passos

- [Transações](transacoes.md) - Como funcionam as transações
- [Categorias](categorias.md) - Organizando despesas
- [Relatórios](relatorios.md) - Analisando gastos
