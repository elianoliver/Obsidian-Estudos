Neste guia, vamos explorar um exemplo prático de como criar um servidor web simples usando Node.js e o módulo `http`. Este servidor irá responder a diferentes rotas com mensagens HTML personalizadas. Vamos analisar o código passo a passo para entender como ele configura o servidor, lida com solicitações e respostas, e roteia as solicitações para exibir conteúdo específico com base na URL acessada. Este exemplo oferece uma visão básica de como criar um servidor web em Node.js e como direcionar diferentes rotas para fornecer conteúdo personalizado aos clientes.

## SUMÁRIO
- [[#Entendendo um Servidor Web Simples com Node.js]]
- [[#Entendendo um Servidor Web com Análise de Parâmetros de Consulta em Node.js]]
## Entendendo um Servidor Web Simples com Node.js
Neste exemplo, vamos analisar um código que cria um servidor web simples em Node.js usando o módulo `http`. O servidor responde a diferentes rotas com mensagens HTML diferentes.

```javascript
const http = require('http');
const porta = 3000;
const host = 'localhost';

const servidor = http.createServer((req, res) => {
    res.writeHead(200, {'Content-Type': 'text/html'});

    if (req.url === '/') {
        res.write('<h1>Página principal</h1>');
    } else if (req.url === '/contato') {
        res.write('<h1>Contato</h1>');
    } else if (req.url === '/sobre') {
        res.write('<h1>Sobre</h1>');
    }
    res.end();
});

servidor.listen(porta, host, () => {
    console.log(`Servidor rodando em http://${host}:${porta}`);
});
```

Vamos explicar passo a passo como esse código funciona:

#### Passo 1: Importação de Módulos e Configuração de Variáveis

```javascript
const http = require('http');
const porta = 3000;
const host = 'localhost';
```

- Importamos o módulo `http` que nos permite criar servidores web.
- Definimos as variáveis `porta` e `host` para especificar a porta e o host em que o servidor será executado.

#### Passo 2: Criação do Servidor

```javascript
const servidor = http.createServer((req, res) => {
    // ...
});
```

- Criamos um servidor HTTP usando o método `createServer`. Ele recebe uma função de retorno de chamada que será executada para cada solicitação que o servidor recebe. Esta função de retorno de chamada possui os parâmetros `req` (a solicitação) e `res` (a resposta).

#### Passo 3: Configuração da Resposta e Roteamento

```javascript
res.writeHead(200, {'Content-Type': 'text/html'});

if (req.url === '/') {
    res.write('<h1>Página principal</h1>');
} else if (req.url === '/contato') {
    res.write('<h1>Contato</h1>');
} else if (req.url === '/sobre') {
    res.write('<h1>Sobre</h1>');
}
res.end();
```

- Configuramos a resposta HTTP com `res.writeHead`. Definimos o código de status 200 (indicando sucesso) e o cabeçalho `Content-Type` como `'text/html'`, indicando que o corpo da resposta contém HTML.
- Verificamos a URL da solicitação `req.url` para determinar qual rota foi acessada. Com base na URL, escrevemos mensagens HTML diferentes no corpo da resposta usando `res.write`. A resposta é encerrada com `res.end()`.

#### Passo 4: Inicialização do Servidor

```javascript
servidor.listen(porta, host, () => {
    console.log(`Servidor rodando em http://${host}:${porta}`);
});
```

- Iniciamos o servidor chamando o método `listen` no objeto `servidor`. O servidor escutará na porta e host especificados.
- Quando o servidor estiver ouvindo, a função de retorno de chamada será executada, e uma mensagem será impressa no console, informando que o servidor está rodando.

Resumindo, este código cria um servidor web que responde a diferentes rotas com mensagens HTML correspondentes. Por exemplo, ao acessar "http://localhost:3000/", você verá a mensagem "Página principal", e ao acessar "http://localhost:3000/contato", verá "Contato". O servidor pode ser configurado para responder a diferentes rotas e fornecer conteúdo personalizado conforme necessário.

## Entendendo um Servidor Web com Análise de Parâmetros de Consulta em Node.js
Neste exemplo, exploramos um código que demonstra a criação de um servidor web em Node.js que tem a capacidade de analisar e processar os parâmetros de consulta presentes em uma URL de solicitação. 
A diferença fundamental entre este método e o método anterior, que não utiliza parâmetros na URL, é a capacidade de receber dados dinâmicos e específicos do cliente por meio de parâmetros de consulta. Isso possibilita a criação de aplicativos web interativos, onde as informações podem ser transmitidas e processadas de acordo com a URL acessada. Vamos agora detalhar passo a passo como esse servidor funciona e como ele processa os parâmetros da consulta, proporcionando uma experiência mais personalizada para o usuário.

Neste exemplo, exploraremos um código que cria um servidor web simples em Node.js usando os módulos `http` e `url`. Esse servidor é capaz de analisar os parâmetros da consulta (query parameters) de uma URL e exibi-los em uma resposta HTML.

```javascript
const http = require('http');
const url = require('url');
const porta = 3001;
const host = 'localhost';
  
const servidor = http.createServer((req, res) => {

    res.writeHead(200, {'Content-Type': 'text/html ;charset=utf-8'});

    // Escreve uma dica para o usuário
    res.write(`<p>Modifique a URL para http://${host}:${porta}<b>/?nome=elian&sobrenome=oliveira</b><p><br/>`);

    // Escreve a URL da solicitação na resposta
    res.write("URL da soliscitação: " + req.url);

    // Analisa os parâmetros da consulta e os escreve na resposta
    const p = url.parse(req.url, true).query;
    res.write('<br/>Nome: ' + p.nome);
    res.write('<br/>Sobrenome: ' + p.sobrenome);
  
    // Finaliza a resposta
    res.end();
});

servidor.listen(porta, host, () => {
    console.log(`Servidor rodando em http://${host}:${porta}`);
});
```

Aqui está uma explicação passo a passo do funcionamento do código:

#### Passo 1: Importação de Módulos e Configuração de Variáveis

```javascript
const http = require('http');
const url = require('url');
const porta = 3000;
const host = 'localhost';
```

- Começamos importando os módulos `http` e `url` que são necessários para criar o servidor web e analisar URLs.
- Em seguida, configuramos as variáveis `porta` e `host` para definir onde o servidor será executado.

#### Passo 2: Criação do Servidor

```javascript
const servidor = http.createServer((req, res) => {
    res.writeHead(200, {'Content-Type': 'text/html ;charset=utf-8'});
```

- Criamos o servidor web utilizando o método `createServer` do módulo `http`. Passamos uma função de retorno de chamada que será executada sempre que o servidor receber uma solicitação HTTP. Esta função recebe `req` (a solicitação) e `res` (a resposta).

- Configuramos a resposta com um código de status HTTP 200 (OK) e um cabeçalho `'Content-Type'` definido como `'text/html'`, indicando que a resposta conterá conteúdo HTML. Além disso, setamos o `charset=utf-8`, para que seja possível reconhecer caracteres como ç e ã.

#### Passo 3: Análise da URL e Resposta

```javascript
// Escreve a URL da solicitação na resposta
res.write("URL da soliscitação: " + req.url);  

// Analisa os parâmetros da consulta e os escreve na resposta
const p = url.parse(req.url, true).query;
res.write('<br/>Nome: ' + p.nome);
res.write('<br/>Sobrenome: ' + p.sobrenome);
```

- A URL da solicitação é escrita na resposta usando `res.write(req.url)`. Isso permite ver a URL na resposta. Por exemplo, se a URL for "/?nome=elian&sobrenome=oliveira", o código anterior exibirá exatamente essa URL na resposta.

- A função `url.parse(req.url, true)` é usada para analisar a URL da solicitação `req.url`. O segundo argumento, `true`, indica que os parâmetros da consulta (query parameters) da URL devem ser analisados como objetos. Isso é importante porque, por padrão, eles são tratados como uma string. A análise como objeto torna mais fácil acessar os parâmetros individualmente.

- Os parâmetros da consulta analisados são armazenados em `p`. O objeto `p` agora contém os parâmetros da consulta da URL como propriedades acessíveis. No exemplo dado, `p.nome` conterá "elian" e `p.sobrenome` conterá "oliveira".

- Finalmente, os valores dos parâmetros `nome` e `sobrenome` são escritos na resposta HTML. As linhas `<br/>` são usadas para adicionar quebras de linha, criando uma apresentação mais legível na resposta.

- O processo é concluído com `res.end()`, indicando que a resposta está completa e pronta para ser enviada ao cliente.

#### Passo 4: Inicialização do Servidor

```javascript
servidor.listen(porta, host, () => {
    console.log(`Servidor rodando em http://${host}:${porta}`);
});
```

- Iniciamos o servidor chamando o método `listen` no objeto `servidor`. O servidor ficará escutando na porta e host especificados.

- Quando o servidor estiver ouvindo, uma mensagem será impressa no console informando que o servidor está rodando.

Em resumo, este código cria um servidor web que analisa os parâmetros da consulta em uma URL de solicitação e os exibe em uma resposta HTML. Ao acessar o servidor e adicionar parâmetros à URL, esses parâmetros são extraídos e exibidos na resposta. Isso demonstra a capacidade do servidor de analisar URLs e processar os dados da consulta.