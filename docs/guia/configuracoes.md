# Configurações ⚙️

O Valt é configurado pela janela **Configurações**, acessível pelo menu ☰ no canto
superior esquerdo da tela principal. As opções ficam organizadas em três abas:
**Geral**, **Moedas** e **Avançado**. Clique em **OK** para salvar.

## Geral

<!-- Source: src/Valt.UI/Views/Main/Modals/Settings/SettingsView.axaml + language.pt-BR.resx -->
| Opção | Descrição |
|-------|-----------|
| **Moeda fiat principal** | Moeda usada nos totais e relatórios (padrão: USD) |
| **Idioma e formato** | Idioma da interface e formato de datas/números; a lista mostra todas as culturas do sistema, com Português, Español e English fixados no topo. O Valt é traduzido em Português, English e Español *(requer reinicialização)* |
| **Exibir contas ocultas** | Mostra contas marcadas como ocultas nas listas |
| **Tema** | 13 temas de base escura: Default, Ocean, Midnight Galaxy, Golden Hour, Arctic Frost, Forest Canopy, Crimson Ember, Monochrome, Rose Quartz, Sunset Blaze, Mocha Brew, Copper Forge e Pepe |
| **Tamanho da Fonte** | Pequeno, Médio ou Grande |

## Moedas

<!-- Source: SettingsView.axaml (Currencies tab) + Settings.FiatCurrencies.* resx -->
Marque as moedas fiat que você usa. **USD está inclusa por padrão** e moedas em uso
não podem ser removidas. Ao adicionar novas moedas, o Valt baixa o histórico de
preços delas (com confirmação).

## Avançado

### Servidor MCP (Assistente IA)

Ative o **Servidor MCP (Assistente IA)** e configure a **Porta do Servidor MCP** (1024–65535, padrão: 5200) para
conectar assistentes de IA. Detalhes completos em [Servidor MCP](../funcionalidades/mcp-server.md).

!!! warning "Segurança"
    O servidor MCP escuta apenas em `localhost` por padrão, ou seja, apenas aplicativos no seu próprio computador podem acessá-lo. Não exponha o servidor à internet sem medidas de segurança adicionais.

### Manutenção

| Botão | Quando usar |
|-------|-------------|
| **Limpar o cache de saldo de conta** | Se os saldos exibidos parecerem errados (veja o [FAQ](../referencia/faq.md)) |
| **Reprocessar o cache de nomes de transações** | Se a busca por transações não encontrar itens existentes |
| **Alterar senha do banco de dados** | Para trocar a senha do seu arquivo `.valt` |

## Seu Arquivo de Dados

Seus dados ficam em um arquivo `.valt` criptografado, cujo local você escolhe ao
criá-lo — veja [Instalação](../guia/instalacao.md). Faça backups copiando o arquivo
para um local seguro.

## Próximos Passos

- [Primeiros Passos](primeiros-passos.md) - Configure contas e categorias
- [FAQ](../referencia/faq.md) - Perguntas frequentes
- [Servidor MCP](../funcionalidades/mcp-server.md) - Conecte sua IA
