# Guia Rápido do npm - Node Package Manager

O **npm (Node Package Manager)** é uma ferramenta essencial no ecossistema do Node.js, permitindo a fácil gestão de dependências e pacotes em projetos. Abaixo estão algumas dicas úteis para começar:

## Verificando se o npm está instalado
Para garantir que o npm está instalado, você pode verificar sua versão com o seguinte comando:

```bash
npm -v
```

Isso retornará a versão do npm instalada, se estiver disponível.

## Configurando o Projeto como um Projeto Node
Para iniciar um novo projeto Node, você pode criar o arquivo `package.json`, que contém informações sobre o projeto, como nome, versão, dependências, etc. O sistema fará algumas perguntas para configurar as variáveis. Use o comando:

```bash
npm init
```

Se desejar inicializar as variáveis com valores padrão sem fazer perguntas, você pode usar o seguinte comando:

```bash
npm init -y
```

## Instalando o pacote Express
O Express é um popular framework web para Node.js. Para instalá-lo em seu projeto, utilize o seguinte comando, especificando a versão desejada (neste exemplo, a versão 4.16.3):

```bash
npm install express@4.16.3 --save-exact
```

Lembrando que a opção `--save-exact` fixa a versão no arquivo `package.json`.

## Instalando o nodemon globalmente
O nodemon é uma ferramenta que ajuda a desenvolver aplicativos baseados em Node.js reiniciando automaticamente o servidor quando detecta mudanças no código. Instale-o globalmente com:

```bash
npm i nodemon -g
```

## Baixando todas as dependências do projeto
Para baixar todas as dependências listadas no arquivo `package.json`, utilize o seguinte comando:

```bash
npm install
```

Você pode abreviar este comando para:

```bash
npm i
```

Ao compartilhar o projeto, você pode omitir a pasta `node_modules`. Ao instalar o projeto em outro sistema operacional, basta executar `npm install` para baixar as dependências e manter a compatibilidade.

## Obtendo o caminho do npm
Para obter o caminho onde o npm está instalado, você pode usar o seguinte comando:

```bash
npm config get prefix
```

Essas dicas básicas devem ajudar a começar com o npm e a gerenciar suas dependências de forma eficiente.