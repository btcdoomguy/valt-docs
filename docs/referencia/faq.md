# FAQ - Perguntas Frequentes ❓

Respostas para as dúvidas mais comuns sobre o Valt.

## Geral 📋

### O que é o Valt?

O Valt é um aplicativo desktop gratuito e open-source para gestão financeira pessoal, desenvolvido especialmente para quem usa Bitcoin como unidade de conta. Ele permite controlar contas, transações, despesas fixas e calcular o preço médio de aquisição de Bitcoin.

### O Valt é gratuito?

Sim, o Valt é 100% gratuito e open-source. Você pode usar todas as funcionalidades sem custo.

### Onde meus dados são armazenados?

Seus dados são armazenados **localmente** no seu computador, em um arquivo `.valt` protegido por senha. Não há sincronização em nuvem nem envio de dados para servidores externos.

### O Valt funciona em qual sistema operacional?

O Valt é multiplataforma e funciona em:
- Windows 10/11
- Linux (Ubuntu, Fedora, etc.)
- macOS 11+

### O Valt precisa de internet?

Precisa de internet para buscar cotações de Bitcoin e moedas fiat. Porém, você pode usar o app offline para lançar transações - as cotações serão buscadas quando houver conexão.

## Instalação e Configuração 🔧

### Como instalo o Valt?

1. Acesse [Releases no GitHub](https://github.com/vmabellini/valt/releases)
2. Baixe a versão para seu sistema operacional
3. Execute o instalador ou extraia o arquivo
4. Rode o executável

Veja o guia completo em [Instalação](../guia/instalacao.md).

### Esqueci minha senha. Como recupero?

Infelizmente, **não é possível recuperar a senha**. O arquivo é criptografado e sem a senha não há acesso aos dados. Por isso, guarde sua senha em local seguro.

### Como faço backup dos meus dados?

1. Feche o Valt
2. Copie o arquivo `.valt` para um local seguro
3. Faça isso regularmente

O arquivo pode ser armazenado em nuvem (Google Drive, Dropbox) pois está criptografado.

### Posso usar o Valt em mais de um computador?

Sim, mas os dados não sincronizam automaticamente. Você precisaria:
1. Copiar o arquivo `.valt` para o outro computador
2. Abrir com a mesma senha
3. Gerenciar manualmente qual versão está mais atualizada

## Contas e Transações 💱

### Qual a diferença entre conta fiat e conta Bitcoin?

- **Conta Fiat**: Para moedas tradicionais (Real, Dólar, Euro, etc.)
- **Conta Bitcoin**: Para armazenar saldo em satoshis/BTC

### Posso ter múltiplas contas?

Sim, você pode criar quantas contas precisar. Recomendamos uma conta para cada banco, corretora ou wallet.

### Como lanço uma compra de Bitcoin?

1. Clique em **Nova Transação**
2. Selecione **Fiat para Bitcoin**
3. Preencha: conta fiat de origem, valor pago, conta Bitcoin de destino, quantidade recebida
4. Salve

### O que é a coluna Sats que aparece na tela principal?

É um recurso que calcula automaticamente quanto uma transação em moeda fiat representava em satoshis na data em que ocorreu. Isso permite ver o custo de oportunidade de cada gasto. O sistema também exibe uma coluna dinâmica chamada "Preço Atual dos Sats", que mostra o valor em fiat daquela despesa nos dias de hoje (o valor que representava em bitcoin vs a cotação atual).

### Meu saldo está errado. O que faço?

1. Verifique se todas as transações foram lançadas
2. Confira se não há transações duplicadas
3. Verifique o saldo inicial da conta
4. Compare com o extrato real do banco/wallet
5. Na tela de configurações, avançado > Limpar o cache do saldo em conta

## Preço Médio 📊

### O que é preço médio?

É o custo médio de aquisição dos seus bitcoins, calculado considerando todas as compras que você fez.

### Qual método de cálculo devo usar?

- **Regra Brasileira**: Se você declara IR no Brasil
- **FIFO**: Se segue regras fiscais de outros países ou prefere esse método

### O preço médio do Valt substitui um contador?

Não. O Valt é uma ferramenta de auxílio. Para declaração de IR, consulte sempre um contador.

### Preciso lançar as transações em dois lugares?

O módulo de Preço Médio é separado das transações normais. Você pode lançar em ambos para ter controle completo, ou usar apenas um deles.

## Relatórios 📈

### Por que meus relatórios estão vazios?

Verifique:
1. Se há transações lançadas no período selecionado
2. Se o filtro de período está correto
3. Se as transações têm categorias atribuídas (para relatório por categoria)

### Posso exportar os relatórios?

A funcionalidade de exportação está em desenvolvimento.

### O que significa "Cobertura do Patrimônio"?

É quantos meses seu patrimônio atual sustentaria seus gastos, baseado na mediana de despesas mensais.

## Segurança e Privacidade 🔒

### Meus dados são enviados para algum servidor?

Não. Seus dados ficam apenas no seu computador. As únicas conexões externas são para buscar cotações de Bitcoin e moedas.

### O arquivo .valt é seguro?

Sim, ele é criptografado com sua senha. Sem a senha, é impossível acessar os dados.

### Posso confiar no código?

O Valt é open-source. Você pode auditar o código no [GitHub](https://github.com/vmabellini/valt).

## Problemas Comuns 🛠️

### O app não abre

Tente:
1. Verificar se há outro processo do Valt rodando
2. Reinstalar o aplicativo
3. Verificar permissões de execução (Linux/Mac)

### Cotações não estão atualizando

Verifique:
1. Sua conexão com internet
2. Se há firewall bloqueando o app
3. Aguarde alguns minutos - as atualizações são periódicas

### Transação sumiu

1. Verifique o filtro de período
2. Verifique o filtro de conta
3. Use a busca para encontrar a transação

### Erro ao abrir banco de dados

Possíveis causas:
1. Senha incorreta
2. Arquivo corrompido
3. Arquivo de versão incompatível

Se o arquivo estiver corrompido, restaure um backup.

## Suporte 🆘

### Onde reporto um bug?

Abra uma issue no [GitHub](https://github.com/vmabellini/valt/issues) descrevendo:
1. O que você estava fazendo
2. O que aconteceu
3. O que deveria ter acontecido
4. Versão do Valt e sistema operacional

### Como sugiro uma nova funcionalidade?

Abra uma issue no [GitHub](https://github.com/vmabellini/valt/issues) com a tag "enhancement" descrevendo sua sugestão.

### Posso contribuir com o código?

Sim! O Valt é open-source. Veja o repositório no [GitHub](https://github.com/vmabellini/valt) para mais informações sobre como contribuir.

## Outras Perguntas 💡

### O Valt serve para controlar saldo de endereços específicos da minha wallet?

NÃO! O Valt é uma ferramenta para gerenciar saldos em Bitcoin, mas não faz gestão direta de UTXOs nem tem conexão com nodes.

### O Valt funciona com Lightning Network?

Você pode criar contas Bitcoin para representar saldos em Lightning, mas não há integração direta com nodes Lightning.

### Posso importar dados de outros apps?

Atualmente não há funcionalidade de importação automática. Você precisa lançar as transações manualmente.

### O Valt tem versão mobile?

Não, o Valt é exclusivamente desktop. Uma versão mobile pode ser considerada no futuro.

### Com que frequência devo lançar transações?

Recomendamos lançar pelo menos semanalmente para não acumular. O ideal é lançar assim que a transação ocorre.
