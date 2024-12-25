## Usando o Console para Depuração em JavaScript
O console é uma ferramenta poderosa que permite aos desenvolvedores depurar e registrar informações importantes durante o desenvolvimento de aplicações JavaScript. Vamos explorar as principais funções que o console oferece:

### Log Padrão
```javascript
console.log("Isso é um log...")
```
- O método `console.log()` é usado para registrar mensagens comuns.
- Ele é frequentemente usado para depurar seu código, exibindo informações relevantes no console do navegador.

### Mensagens de Erro e Aviso
```javascript
console.error("Isso é uma mensagem de erro!")
console.warn("Isso é uma mensagem de aviso!")
```
- Use `console.error()` para registrar mensagens de erro.
- Use `console.warn()` para registrar mensagens de aviso.
- Isso ajuda a identificar problemas e alertas no código.

### Mensagens Informativas
```javascript
console.info("Isso é uma informação")
```
- O `console.info()` é usado para registrar mensagens informativas que não são necessariamente de depuração.

### Exibir Dados em Tabela
```javascript
var vetor = [25, 20, 45, 50]
console.table(vetor)
```
- O `console.table()` exibe o conteúdo de arrays ou objetos em formato de tabela.
- Isso facilita a visualização dos dados estruturados.

### Contagem de Tempo
```javascript
console.time("label")
// ... código a ser medido ...
console.timeEnd("label")
```
- `console.time()` inicia um contador com uma etiqueta específica.
- `console.timeEnd()` encerra o contador e exibe o tempo decorrido.
- Isso é útil para medir o tempo de execução de partes do código.

### Exibir Propriedades do Objeto
```javascript
var obj = {
    nome: "Eu mesmo",
    idade: 35,
    cpf: "004.742.879.12",
    cargo: "Técnico"
}
console.dir(obj)
```
- O `console.dir()` exibe uma lista de propriedades de um objeto.

### Asserts
```javascript
console.assert(afirmação, mensagem)
```
- O `console.assert()` grava uma mensagem de erro no console se a afirmação for falsa.
- Se a afirmação for verdadeira, nada acontece.

### Contador
```javascript
console.count("etiqueta")
```
- `console.count()` registra o número de vezes que essa chamada específica foi chamada com a etiqueta especificada.

### Grupos no Console
```javascript
console.log("Nível externo");
console.group("Grupo 1");
console.log("Nível 2");
console.group("Grupo 2");
console.log("Nível 3");
console.groupEnd();
console.log("De volta ao Nível 2");
console.groupEnd();
console.log("De volta ao Nível externo");
```
- `console.group()` cria um novo grupo de mensagens no console, recuando as mensagens subsequentes.
- `console.groupEnd()` encerra o grupo.
- Isso ajuda a organizar e estruturar a saída no console.

### Rastreamento de Pilha
```javascript
function funcao1() {
    funcao2();
}

function funcao2() {
    funcao3();
}

function funcao3() {
    console.trace();
}

funcao1();
```
- `console.trace()` gera um rastreamento de pilha, mostrando a sequência de chamadas de funções.
- Isso é útil para depurar e entender como o código é executado.

### Limpar o Console
```javascript
console.clear()
```
- `console.clear()` é usado para limpar o console, removendo mensagens anteriores.

Essas são algumas das funcionalidades mais comuns do console no JavaScript, e elas são essenciais para depurar, rastrear problemas e entender o fluxo de execução do código.