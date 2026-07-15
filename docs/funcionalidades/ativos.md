# Ativos 📊

O módulo de Ativos permite que você registre investimentos e bens externos ao Valt para ter uma visão mais ampla do seu patrimônio total. Ele é **completamente opcional** e separado do sistema de contas e transações.

## Visão Geral

<!-- Source: src/Valt.Core/Modules/Assets/AssetTypes.cs + language.pt-BR.resx -->
O módulo de Ativos foi criado para quem deseja enxergar seu patrimônio completo em um só lugar. Você pode cadastrar ações, ETFs, criptomoedas, imóveis, commodities, posições alavancadas, ativos personalizados, empréstimos BTC e posições de empréstimo BTC (credor).

!!! info "O que o módulo NÃO é"
    O módulo de Ativos **não é um rastreador de preços em tempo real**. Ele serve para registrar o que você possui e ter uma visão consolidada do seu patrimônio. A atualização de preços pode ser feita manualmente ou por fontes configuráveis, mas não há monitoramento contínuo de variações de mercado.

## Tipos de Ativo 📋

O Valt suporta 9 tipos de ativo:

| Tipo | Descrição | Exemplo |
|------|-----------|---------|
| **Ação** | Ações de empresas listadas em bolsa | PETR4, VALE3, AAPL |
| **ETF** | Fundos de índice negociados em bolsa | IVVB11, BOVA11, VOO |
| **Criptomoeda** | Moedas digitais além do Bitcoin | ETH, SOL, ADA |
| **Imóvel** | Propriedades e bens imobiliários | Apartamento, terreno |
| **Commodity** | Matérias-primas e metais preciosos | Ouro, prata |
| **Posição Alavancada** | Operações com alavancagem | Futuros, margem |
| **Personalizado** | Qualquer outro tipo de ativo | Veículos, arte, coleções |
| **Empréstimo BTC** | Empréstimo com colateral em BTC | Tomar fiat com garantia em BTC |
| **Empréstimo BTC (Credor)** | Posição de empréstimo BTC/fiat | Emprestar BTC ou fiat |

## Criando um Ativo ➕

### Ativo Básico

Para ações, ETFs, criptomoedas, commodities e ativos personalizados:

1. Vá para a aba **Ativos**
2. Clique no botão **+** para adicionar um novo ativo
3. Selecione o tipo de ativo
4. Preencha os campos:

| Campo | Descrição |
|-------|-----------|
| **Nome** | Identificação do ativo (ex: "PETR4", "Ethereum") |
| **Tipo** | Tipo do ativo (Ação, ETF, Cripto, etc.) |
| **Quantidade** | Quantas unidades você possui |
| **Preço de Compra** | Preço médio de aquisição por unidade |
| **Moeda** | Moeda de referência do ativo |
| **Fonte de Preço** | Como o preço será atualizado (Manual, Yahoo Finance, Live Price) |
| **Ícone** | Ícone visual para identificação |
| **Cor** | Cor associada ao ativo |

5. Clique em **Salvar**

### Imóvel 🏠

Imóveis possuem campos adicionais para capturar informações de renda:

1. Selecione o tipo **Imóvel**
2. Preencha os campos básicos (nome, valor, moeda)
3. Preencha os campos adicionais:

| Campo | Descrição |
|-------|-----------|
| **Valor do Imóvel** | Valor estimado de mercado |
| **Renda de Aluguel** | Valor mensal de aluguel recebido (se aplicável) |
| **Moeda** | Moeda de referência |

4. Clique em **Salvar**

!!! tip "Dica"
    Mesmo que o imóvel não esteja alugado, registre-o para ter uma visão completa do seu patrimônio.

### Posição Alavancada ⚡

Posições alavancadas incluem campos específicos para controle de risco:

1. Selecione o tipo **Posição Alavancada**
2. Preencha os campos básicos
3. Preencha os campos adicionais:

| Campo | Descrição |
|-------|-----------|
| **Preço de Entrada** | Preço no momento da abertura da posição |
| **Alavancagem** | Multiplicador de alavancagem (ex: 2x, 5x, 10x) |
| **Preço de Liquidação** | Preço no qual a posição é liquidada automaticamente |
| **Moeda** | Moeda de referência |

4. Clique em **Salvar**

!!! warning "Atenção"
    Posições alavancadas envolvem alto risco. Use o campo de liquidação para manter o controle dos seus limites de risco.

## Fontes de Preço 💰

O Valt oferece três formas de manter o preço dos seus ativos atualizado:

### Manual

Você define o preço diretamente. Ideal para:

- Imóveis (valor de mercado estimado)
- Ativos personalizados
- Qualquer ativo que você prefira atualizar por conta própria

### Yahoo Finance

O Valt consulta o Yahoo Finance para obter o preço. Ideal para:

- Ações listadas em bolsa
- ETFs
- Alguns índices e commodities

!!! tip "Dica"
    Para usar o Yahoo Finance, insira o ticker do ativo exatamente como aparece no Yahoo Finance (ex: "PETR4.SA" para Petrobras na B3).

### Live Price

Atualização de preço em tempo real via API. Ideal para:

- Criptomoedas
- Ativos com preços disponíveis em APIs públicas

## Gerenciando Ativos ⚙️

### Editando um Ativo

1. Clique no ativo que deseja editar
2. Clique no ícone de edição (lápis)
3. Modifique os campos desejados
4. Clique em **Salvar**

### Alternando Visibilidade

Se você não quer mais ver um ativo na lista principal:

1. Edite o ativo
2. Desmarque a opção **Visível**
3. Salve

O ativo será ocultado, mas permanece cadastrado.

### Incluir/Excluir do Patrimônio Líquido

Você pode escolher se um ativo deve ser contabilizado no cálculo do patrimônio líquido:

1. Edite o ativo
2. Marque ou desmarque a opção **Incluir no Patrimônio Líquido**
3. Salve

!!! info "Quando excluir do patrimônio"
    Pode ser útil excluir ativos que você considera ilíquidos ou que não deseja contabilizar no total, como um imóvel de uso pessoal ou uma posição alavancada de alto risco.

### Ordenando Ativos

Você pode reordenar os ativos usando o botão direito do mouse e as opções Mover pra Cima ou Mover pra Baixo, ou segure Ctrl e utilize as setas do teclado. A ordem é salva automaticamente.

### Excluindo um Ativo

Para excluir um ativo:

1. Edite o ativo
2. Clique em **Excluir**
3. Confirme a exclusão

## Vendendo um Ativo 💸

Quando você vende total ou parcialmente um ativo:

1. Clique no ativo que deseja vender
2. Selecione a opção **Vender**
3. Preencha os campos:

| Campo | Descrição |
|-------|-----------|
| **Quantidade** | Quantas unidades está vendendo |
| **Preço de Venda** | Preço por unidade na venda |
| **Data** | Data da operação |

4. Clique em **Confirmar**

O Valt calculará automaticamente o lucro ou prejuízo da operação com base no preço de compra registrado.

## Patrimônio e Valor Líquido 💎

### Como os Ativos Integram ao Patrimônio

Os ativos marcados como "Incluir no Patrimônio Líquido" são somados ao patrimônio total do Valt, que inclui:

- Saldo de todas as contas (fiat e Bitcoin)
- Valor de todos os ativos incluídos no patrimônio

### Conversão Multi-Moeda

Se você possui ativos em moedas diferentes da sua moeda principal, o Valt converte automaticamente para a moeda principal usando as taxas de câmbio disponíveis.

### Indicação de Lucro/Prejuízo

O Valt usa cores para indicar a performance dos seus ativos:

- **Verde** 🟢: O ativo está com lucro (preço atual > preço de compra)
- **Vermelho** 🔴: O ativo está com prejuízo (preço atual < preço de compra)

Isso permite uma análise visual rápida do desempenho da sua carteira.

!!! warning "Importante"
    O módulo de Ativos **não rastreia variações diárias de preço**. Ele oferece uma visão de patrimônio baseada em registros manuais ou atualizações periódicas via fontes de preço configuradas. Não espere funcionalidade de um home broker — o objetivo é ter uma **visão panorâmica do seu patrimônio**.

## Boas Práticas ✨

### Mantenha os Preços Atualizados

Atualize periodicamente o preço dos ativos com fonte manual. Para ativos com Yahoo Finance ou Live Price, o Valt fará isso por você.

### Organize por Tipo

Agrupe seus ativos por tipo para facilitar a visualização. Use ícones e cores para diferenciar rapidamente cada um.

### Use o Toggle de Patrimônio com Critério

Inclua no patrimônio líquido apenas os ativos que fazem sentido para sua análise financeira. Ativos muito ilíquidos ou especulativos podem distorcer sua visão de patrimônio.

### Registre o Preço de Compra Corretamente

O preço de compra é a base para o cálculo de lucro/prejuízo. Certifique-se de registrar o valor correto para ter análises precisas.

### Não Substitui o Controle de Contas

O módulo de Ativos complementa, mas não substitui, o sistema de contas e transações. Continue usando as contas para controlar seu fluxo de caixa do dia a dia.

## Próximos Passos

- [Contas](contas.md) - Gerenciando suas contas fiat e Bitcoin
- [Preço Médio](preco-medio.md) - Calculando seu custo de aquisição de Bitcoin
- [Relatórios](relatorios.md) - Análises completas do seu patrimônio
