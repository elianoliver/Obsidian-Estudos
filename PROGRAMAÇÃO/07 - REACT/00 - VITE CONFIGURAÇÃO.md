## **Por que usar o Vite?**

Criar um projeto React envolve várias configurações (como Babel, Webpack, etc.). O **Vite** simplifica isso: ele configura **tudo automaticamente**, de forma rápida e moderna.

```ad-info
Vite (que significa "rápido" em francês) é uma **ferramenta de build** que acelera o desenvolvimento de aplicações web como React, Vue, Svelte ou até projetos com JavaScript puro.

```

## Criando um Projeto React com Vite

1. **Abra o terminal** (Command Prompt, PowerShell ou Terminal do macOS).
    
2. Digite o seguinte comando:

```bash
npm create vite@latest my-react-app -- --template react
```

Isso cria um novo projeto chamado `my-react-app` usando o **template oficial do React** com Vite.

## Estrutura Inicial do Projeto

Depois de criado, você verá arquivos e pastas como:

- `src/`: código-fonte (ex: `App.jsx`)
- `public/`: arquivos públicos (como imagens)
- `package.json`: configurações do projeto e suas dependências
- `vite.config.js`: configurações do Vite

Vite só gera o **essencial** para começar — sem inchaço.

## Instalando as dependências

```bash
cd my-react-app
npm install
```

- `cd my-react-app` entra na pasta do projeto.
- `npm install` instala **todas as bibliotecas necessárias**, como `react`, `react-dom`, etc.
    
Essas bibliotecas são armazenadas na pasta `node_modules/`.

## Executando o projeto

Com tudo instalado, rode o projeto com:

```bash
npm run dev
```

- Isso inicia o **servidor de desenvolvimento local**.
- Abra seu navegador e acesse: [http://localhost:5173](http://localhost:5173/)
- Você verá o **template inicial do React** criado pelo Vite.
    
Para parar o servidor, use `CTRL + C` no terminal.

## Modificando o projeto

Abra a pasta `src/` e edite o arquivo `App.jsx` — é ali que você começa a **criar sua interface**. Ao salvar, o navegador **atualiza automaticamente** com as novas mudanças (sem precisar recarregar a página manualmente).

## Conclusão

Vite é uma ferramenta moderna e eficiente para **iniciar projetos React rapidamente**. Ele cuida das configurações, permite um carregamento mais rápido e te deixa livre para focar naquilo que importa: **criar sua aplicação**.