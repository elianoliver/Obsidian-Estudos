
## SUMÁRIO
- [[#Servidor Web Simples Puxando Uma Página Index.html]]
- [[#Servidor Web e Escrevendo em um Arquivo com Node.js]]

## Servidor Web Simples Puxando Uma Página Index.html

Neste tutorial, exploraremos a criação de um servidor web utilizando Node.js. Nosso objetivo é disponibilizar uma página HTML para os usuários, e para isso, iremos utilizar o módulo `fs` (file system) para ler o conteúdo de um arquivo chamado 'index.html'. Quando os usuários acessarem o servidor por meio de um navegador, a página 'index.html' será carregada dinamicamente e exibida como resposta. Vamos analisar cada etapa do código, desde a configuração do servidor até a resposta com a página HTML, permitindo assim a compreensão detalhada desse processo.

#### Passo 1: Importação de Módulos e Definição da Porta

```javascript
const http = require('http');
const fs = require('fs');
const port = process.env.PORT || 3000;
```

Começamos importando dois módulos essenciais: `http` e `fs` (file system). O módulo `http` nos permite criar um servidor web, enquanto o `fs` é usado para ler arquivos do sistema de arquivos. A variável `port` é configurada com base na variável de ambiente `PORT`, que determina a porta do servidor. Se a variável de ambiente não estiver definida, a porta padrão 3000 é usada.

#### Passo 2: Criação do Servidor HTTP

```javascript
const server = http.createServer((req, res) => {
	
    fs.readFile('./src/index.html', (err, data) => {
		
        if (err) {
            console.error(err);
            res.writeHead(500, { 'Content-Type': 'text/plain' });
            res.end('Internal Server Error');
        } else {
            res.writeHead(200, { 'Content-Type': 'text/html' });
            res.write(data);
            res.end();
        }
    });
});
```

Aqui, criamos um servidor HTTP usando o método `createServer` do módulo `http`. A função de retorno de chamada é acionada quando uma solicitação HTTP é recebida pelo servidor. Utilizamos `fs.readFile` para ler o arquivo './src/index.html' do sistema de arquivos. Se ocorrer um erro na leitura (por exemplo, se o arquivo não for encontrado), o servidor responde com um código de status 500 (Internal Server Error) e uma mensagem de erro. Se a leitura for bem-sucedida, o servidor responde com o conteúdo HTML do arquivo.

#### Passo 3: Inicialização do Servidor

```javascript
server.listen(port, () => {
    console.log(`Server running on port http://localhost:${port}`);
});
```

Iniciamos o servidor chamando o método `listen` no objeto `server`, fazendo com que ele escute na porta especificada pela variável `port`. Uma mensagem é exibida no console para indicar que o servidor está em execução na porta escolhida.

Este código demonstra a criação de um servidor web básico em Node.js que pode servir um arquivo HTML quando acessado em um navegador. A porta do servidor pode ser configurada por meio de uma variável de ambiente, tornando-o flexível e personalizável.


## Servidor Web e Escrevendo em um Arquivo com Node.js

Neste tutorial, exploraremos a criação de um servidor web com Node.js e a realização de operações de escrita em arquivos em resposta a solicitações HTTP. O ponto focal deste código reside no uso do método `fs.appendFile`, que faz parte do módulo `fs` (file system) do Node.js. 

O `appendFile` permite acrescentar conteúdo a um arquivo existente ou criar um novo arquivo, caso o arquivo especificado não exista. Isso torna possível atualizar arquivos com dados dinâmicos e personalizados a partir do servidor. Vamos analisar cada etapa do código para compreender como o servidor é configurado para adicionar conteúdo ao arquivo 'teste.txt' e oferecer um entendimento mais aprofundado das propriedades e funcionalidades do método `appendFile`.

#### Passo 1: Importação de Módulos e Configuração da Porta

```javascript
const http = require('http');
const fs = require('fs');
const port = process.env.PORT || 3000;
```

Iniciamos importando os módulos essenciais, `http` e `fs` (file system), necessários para criar um servidor web e realizar operações de escrita em arquivos. A variável `port` é configurada com base na variável de ambiente `PORT`. Caso essa variável não esteja definida, a porta padrão 3000 será usada.

#### Passo 2: Criação do Servidor HTTP e Escrita no Arquivo

```javascript
const server = http.createServer((req, res) => {
    fs.appendFile('./src/teste.txt', 'Curso de Node - CFB Cursos', (err) => {
        if (err) throw err;
        console.log('Arquivo Criado!');
    });
});
```

Neste passo, criamos um servidor HTTP utilizando o método `createServer` do módulo `http`. A função de retorno de chamada é executada sempre que uma solicitação HTTP é recebida pelo servidor. Dentro dessa função, utilizamos o método `fs.appendFile` para adicionar o texto 'Curso de Node - CFB Cursos' ao arquivo 'teste.txt'. Se ocorrer algum erro durante a operação de escrita, um erro é lançado e o programa é encerrado. Caso a operação seja bem-sucedida, a mensagem 'Arquivo Criado!' é registrada no console.

#### Passo 3: Inicialização do Servidor

```javascript
server.listen(port, () => {
    console.log(`Server running on port http://localhost:${port}`);
});
```

Finalizamos iniciando o servidor através do método `listen` no objeto `server`, que o configura para escutar na porta especificada pela variável `port`. Uma mensagem é exibida no console para indicar que o servidor está em execução na porta determinada.

Resumidamente, este código demonstra como criar um servidor web em Node.js e realizar operações de escrita em um arquivo. Quando o servidor é acessado, ele adiciona o texto 'Curso de Node - CFB Cursos' ao arquivo 'teste.txt'. A porta do servidor pode ser personalizada através de uma variável de ambiente. Este exemplo ilustra como realizar operações de escrita em arquivos a partir de um servidor Node.js em resposta a solicitações HTTP.

