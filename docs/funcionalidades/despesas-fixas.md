# Despesas Fixas

As despesas fixas são gastos recorrentes que você pode configurar uma vez e lançar rapidamente todos os meses. Essa funcionalidade economiza tempo e ajuda no planejamento financeiro.

## O Que São Despesas Fixas

Despesas fixas são gastos que ocorrem regularmente em intervalos previsíveis:

- **Moradia**: Aluguel, condomínio, IPTU
- **Serviços**: Luz, água, gás, internet, telefone
- **Assinaturas**: Netflix, Spotify, Amazon Prime, academia
- **Financiamentos**: Parcelas de carro, empréstimos
- **Seguros**: Saúde, carro, vida

## Por Que Usar

### Lançamento Rápido

Em vez de preencher todos os campos de uma transação, você pode lançar uma despesa fixa com poucos cliques.

### Controle de Gastos Recorrentes

Veja facilmente quanto você gasta com compromissos fixos por mês.

### Histórico de Valores

O Valt mantém um histórico de quanto você pagava em cada período, útil para acompanhar aumentos de preço.

### Planejamento

Saiba antecipadamente quanto precisará para cobrir suas despesas fixas.

## Criando uma Despesa Fixa

1. Na aba **Transações**, acesse a seção de **Despesas Fixas**
2. Clique em **Adicionar Despesa Fixa**
3. Preencha os campos:

| Campo | Descrição |
|-------|-----------|
| **Nome** | Identificação (ex: "Netflix", "Aluguel") |
| **Valor** | Quanto você paga |
| **Frequência** | Com que periodicidade ocorre |
| **Conta** | De qual conta é debitado (opcional) |
| **Moeda** | Se não vincular conta, qual moeda |
| **Categoria** | Como categorizar |
| **Ícone** | Ícone visual |

4. Clique em **Salvar**

## Frequências Disponíveis

| Frequência | Descrição | Exemplo |
|------------|-----------|---------|
| **Mensal** | Uma vez por mês | Aluguel, Netflix |
| **Semanal** | Uma vez por semana | Faxineira |
| **Quinzenal** | A cada duas semanas | Alguns seguros |
| **Anual** | Uma vez por ano | IPVA, seguro anual |

## Vinculando a uma Conta

Você pode vincular uma despesa fixa a uma conta específica:

### Com Conta Vinculada

- Ao lançar, a conta já vem preenchida
- Mais rápido para despesas que sempre saem da mesma conta
- Exemplo: Netflix sempre debita do cartão Nubank

### Sem Conta Vinculada

- Ao lançar, você escolhe a conta
- Útil para despesas que podem ser pagas de diferentes formas
- Exemplo: Conta de luz pode ser paga via PIX de qualquer banco

## Histórico de Valores (Ranges)

Uma funcionalidade poderosa é o histórico de valores. Quando o valor de uma despesa muda, você pode manter um registro:

### Exemplo: Aluguel

```
Jan/2023 - Jun/2023: R$ 1.500
Jul/2023 - Dez/2023: R$ 1.600
Jan/2024 - atual:    R$ 1.700
```

### Como Funciona

1. Edite a despesa fixa
2. Vá para **Histórico de Valores**
3. Adicione um novo período com o novo valor
4. O período anterior é automaticamente fechado

### Benefícios

- Veja como seus gastos fixos evoluíram
- Compare quanto pagava antes vs. agora
- Identifique aumentos excessivos

## Lançando uma Despesa Fixa

Quando chegar a hora de pagar uma despesa fixa:

1. Na seção de **Despesas Fixas** na tela principal, localize a despesa e clique duas vezes ou aperte Enter
2. A tela de adicionar transação será aberta com os dados pré-preenchidos. Edite o que for necessário e pronto. Aquela transação estará vinculada à sua despesa fixa.

## Gerenciando Despesas Fixas

### Editando

1. Clique na despesa fixa
2. Clique em **Editar**
3. Modifique os campos necessários
4. Salve

### Excluindo

1. Clique na despesa fixa
2. Clique em **Excluir**
3. Confirme

!!! note "Nota"
    Excluir uma despesa fixa não remove as transações já lançadas.

### Pausando

Se você quiser temporariamente parar de ver uma despesa fixa (ex: cancelou Netflix):

1. Edite a despesa
2. Marque como **Inativa**
3. Salve

Ela não aparecerá na lista principal, mas o histórico é mantido.

## Relatório de Despesas Fixas

O Valt pode gerar um resumo das suas despesas fixas:

- Total mensal de compromissos
- Quanto representa do seu orçamento
- Projeção anual

Isso ajuda a responder: "Quanto preciso por mês só para cobrir despesas fixas?"

## Boas Práticas

### Categorização

- Categorize suas despesas fixas adequadamente
- Isso permite análises como "quanto gasto com assinaturas?"

### Revisão Periódica

- A cada 3-6 meses, revise suas despesas fixas
- Identifique assinaturas que não usa mais
- Negocie valores quando possível

### Atualização de Valores

- Quando um valor muda (reajuste de aluguel, aumento de internet), atualize no Valt
- Use o histórico de valores para manter o registro

### Datas de Vencimento

Use o campo de descrição para anotar a data de vencimento:
- "Netflix - vence dia 15"
- "Aluguel - vence dia 10"

O Valt pede uma data inicial para iniciar a exibição da despesa fixa na tela principal. Dependendo da frequência selecionada, essa data serve como base para calcular as próximas ocorrências. Por exemplo, colocar a data inicial numa sexta-feira em uma despesa fixa semanal fará com que o sistema calcule todos os futuros lançamentos para sextas-feiras.

## Exemplos de Configuração

### Netflix

- **Nome**: Netflix
- **Valor**: R$ 55,90
- **Frequência**: Mensal
- **Conta**: Cartão Nubank
- **Categoria**: Lazer > Streaming

### Aluguel

- **Nome**: Aluguel
- **Valor**: R$ 2.500
- **Frequência**: Mensal
- **Conta**: Itaú
- **Categoria**: Moradia > Aluguel

### IPVA

- **Nome**: IPVA
- **Valor**: R$ 1.200
- **Frequência**: Anual
- **Conta**: (não vinculada)
- **Categoria**: Transporte > Impostos

### Faxineira

- **Nome**: Faxina
- **Valor**: R$ 200
- **Frequência**: Quinzenal
- **Conta**: (não vinculada)
- **Categoria**: Moradia > Serviços

## Próximos Passos

- [Transações](transacoes.md) - Como funcionam as transações
- [Categorias](categorias.md) - Organizando despesas
- [Relatórios](relatorios.md) - Analisando gastos
