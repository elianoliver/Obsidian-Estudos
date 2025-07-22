Funções são blocos de código em JavaScript (e em muitas outras linguagens de programação) que realizam tarefas específicas ou executam ações quando chamadas. Elas são usadas para agrupar um conjunto de instruções relacionadas em um único nome, tornando o código mais organizado, reutilizável e modular.

## Sumário

- [[#Função Nomeada]]
- [[#Funções Anônimas]]
- [[#Arrow Function]]
- [[#Funções Auto-Executáveis]]

## Função Nomeada

Uma função nomeada é uma função JavaScript que recebe um nome específico no momento da sua declaração. Esse nome é utilizado para referenciar e chamar a função em qualquer parte do código. Funções nomeadas são declaradas com a palavra-chave `function`, seguida pelo nome da função, parênteses para parâmetros e um bloco de código.

A sintaxe básica de uma função nomeada é a seguinte:

```javascript
function nomeDaFuncao(parametro1, parametro2) {
    // Bloco de código da função
    // Pode conter várias instruções
    return resultado;
}
```

- `nomeDaFuncao`: É o nome dado à função e é usado para chamá-la posteriormente.
- `parametro1`, `parametro2`: São os parâmetros da função, que representam valores que podem ser passados para a função.
- `bloco de código`: Contém as instruções que definem o comportamento da função.
- `resultado`: É o valor opcional retornado pela função.

Aqui está um exemplo simples de uma função nomeada que calcula a soma de dois números:

```javascript
function somarNumeros(numero1, numero2) {
    return numero1 + numero2;
}

const resultado = somarNumeros(5, 3); // Chama a função e armazena o resultado
console.log(resultado); // Exibe o resultado (8) no console
```

Neste exemplo, a função `somarNumeros` é declarada com um nome específico e pode ser chamada em qualquer lugar do código, facilitando a reutilização.

## Funções Anônimas

Funções anônimas são aquelas que não são declaradas com um nome específico no momento da criação. Em vez disso, elas são atribuídas a uma variável ou passadas como argumentos para outras funções. Essa capacidade de tratar funções como valores de primeira classe é uma característica fundamental do JavaScript.

A sintaxe básica de uma função anônima é a seguinte:

```javascript
const nomeDaVariavel = function(parametro1, parametro2) {
    // Bloco de código da função
    // Pode conter várias instruções
    return resultado;
};
```

- `var nomeDaVariavel`: É a variável à qual a função anônima é atribuída. A variável pode ser usada para chamar a função posteriormente.
- `parametro1`, `parametro2`: São os parâmetros da função, assim como nas funções nomeadas.
- `bloco de código`: Contém as instruções que definem o comportamento da função anônima.
- `resultado`: É o valor opcional retornado pela função.

Aqui está um exemplo simples de uma função anônima atribuída a uma variável:

```javascript
const somar = function(numero1, numero2) {
    return numero1 + numero2;
};

const resultado = somar(5, 3); // Chama a função e armazena o resultado
console.log(resultado); // Exibe o resultado (8) no console
```

Neste exemplo, a função anônima é atribuída à variável `somar`, que pode ser usada para chamar a função, semelhante a uma função nomeada.

## Arrow Function

Arrow functions são uma forma mais concisa de declarar funções em JavaScript, introduzidas no ES6. Elas utilizam a sintaxe `=>` (seta), o que as torna mais enxutas e legíveis, especialmente em funções curtas.

### Sintaxe básica

```javascript
const nomeDaFuncao = (parametro1, parametro2) => {
    // Instruções
    return resultado;
};
```

### Regras e variações

Se a função **recebe apenas um parâmetro**, os parênteses () são **opcionais**
```javascript
const cumprimentar = nome => console.log("Olá, " + nome);
cumprimentar("elian")
```

Se a função **não recebe nenhum parâmetro**, os parênteses () são **obrigatórios**

```javascript
const ola = () => console.log("Olá!");
ola()
```

Se a função possui **apenas uma linha de código** e **retorna um valor**, é possível **omitir as chaves e a palavra-chave `return`** — o retorno será **implícito**:

```javascript
const somar = (a, b) => console.log(a + b);
somar(1,2)
```

⚠️ Importante: se você usar chaves `{ }`, **precisa** usar o `return` para retornar um valor explicitamente. Caso contrário, a função retorna `undefined`.

```javascript
const somar = (a, b) => { // retorno explícito
	return console.log(a + b)
}; 
somar(1,2)

//Mas o seguinte causaria erro de sintaxe:
const somar2 = (a, b) => return console.log(a + b)
somar2(1,2)

```

### Quando usar?

Arrow functions são ideais para funções curtas, callbacks e expressões simples. No entanto, como elas não têm seu próprio `this`, `arguments`, ou `super`, é importante avaliar se são adequadas ao contexto, principalmente em métodos de objetos ou classes.
## Funções Auto-Executáveis
Funções auto-executáveis são funções que são definidas e executadas imediatamente após a sua criação. Elas são geralmente usadas para encapsular um bloco de código em um escopo isolado, evitando que suas variáveis e funções interfiram no escopo global do programa. O uso de parênteses () no final da declaração da função é o que torna a função autoexecutável.

A sintaxe básica de uma função autoexecutável é a seguinte:

```javascript
(function() {
    // Bloco de código da função autoexecutável
})();
```

Os parênteses externos em volta da função e os parênteses finais `()` na última linha da declaração são responsáveis por chamar a função imediatamente após a sua criação.

Aqui está um exemplo de uma função autoexecutável que cria um escopo isolado para evitar a poluição "do escopo global:

```javascript
(function() {
	var contador = 0;
	
	function incrementar() {
		contador++;
	}
	
	incrementar();
		console.log(contador); // Exibe 1
})();

console.log(typeof contador); // Exibe "undefined"
```

Neste exemplo, a função auto-executável encapsula a variável `contador` e a função `incrementar`, evitando que elas poluam o escopo global.