# Instalação 📥

O Valt está disponível para Windows, Linux e macOS. Escolha abaixo o método de instalação para o seu sistema operacional.

## Requisitos do Sistema 📋

- **Sistema Operacional**: Windows 10/11, Linux (Ubuntu 20.04+, Fedora 35+, etc.) ou macOS 11+
- **Memória RAM**: 4 GB (mínimo), 8 GB (recomendado)
- **Espaço em disco**: 100 MB para instalação + espaço para seus dados
- **Conexão com internet**: Necessária para buscar cotações de Bitcoin e moedas fiat

## Download ⬇️

Acesse a página de [Releases no GitHub](https://github.com/btcdoomguy/valt/releases) e baixe a versão mais recente para o seu sistema operacional.

### 🪟 Windows

1. Baixe o arquivo `Valt-Windows-vXXXX.zip` (onde XXXX é a versão mais recente)
2. Extraia para uma pasta de sua preferência
3. Execute o arquivo `Valt.exe`

### 🐧 Linux

1. Baixe o arquivo `Valt-Linux-vXXXX.zip` (onde XXXX é a versão mais recente)
2. Extraia para uma pasta de sua preferência
3. Execute o arquivo `Valt`

!!! tip "Dica para Linux"
    Você pode criar um atalho no menu de aplicativos criando um arquivo `.desktop` na pasta `~/.local/share/applications/`.

### 🍎 macOS

1. Baixe o arquivo `Valt-MacOs-experimental-vXXXX.zip` (onde XXXX é a versão mais recente)
2. Abra o arquivo DMG
3. Arraste o Valt para a pasta Aplicativos
4. Na primeira execução, pode ser necessário permitir a execução em **Preferências do Sistema > Segurança e Privacidade**

!!! warning "Sobre o MacOS"
    O funcionamento do Valt é compatível com macOS porém não é oficialmente suportado. Alguns problemas de layout e funcionamento podem ocorrer.

## Primeira Execução 🎬

Ao executar o Valt pela primeira vez, você verá a tela de seleção inicial com duas opções:

1. **Criar novo banco de dados** - Para começar do zero
2. **Abrir banco de dados existente** - Se você já tem um arquivo de dados do Valt

### Criando um Novo Banco de Dados

1. Clique em **Criar novo banco de dados**
2. Escolha um local para salvar o arquivo `.valt`
3. Defina uma **senha forte** para proteger seus dados
4. Confirme a senha
5. Clique em **Criar**

!!! warning "Importante sobre a senha"
    Guarde sua senha em um local seguro. Se você esquecê-la, **não será possível recuperar** seus dados. Não existe opção de "esqueci minha senha".

### Abrindo um Banco de Dados Existente

1. Clique em **Abrir banco de dados existente**
2. Navegue até o arquivo `.valt`
3. Digite a senha
4. Clique em **Abrir**

## Atualizações 🔄

O Valt verifica automaticamente se há novas versões disponíveis. Quando uma atualização estiver disponível, você verá um indicador na interface.

Para atualizar manualmente:

1. Acesse a página de [Releases no GitHub](https://github.com/btcdoomguy/valt/releases)
2. Baixe a versão mais recente
3. Execute a nova versão e delete a anterior
4. Seus dados são preservados no arquivo `.valt`

## Backup 💾

Seus dados estão no arquivo `.valt` que você criou. Para fazer backup:

1. Feche o Valt
2. Copie o arquivo `.valt` para um local seguro (HD externo, nuvem, etc.)
3. Faça isso regularmente!

!!! tip "Dica de Backup"
    O arquivo `.valt` é um banco de dados SQLite criptografado. Você pode mantê-lo em serviços de nuvem como Google Drive ou Dropbox, pois ele está protegido por senha.

## Próximos Passos ➡️

Agora que o Valt está instalado, vá para [Primeiros Passos](primeiros-passos.md) para configurar suas contas e começar a usar.
