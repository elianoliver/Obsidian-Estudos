Funções são blocos de código em JavaScript (e em muitas outras linguagens de programação) que realizam tarefas específicas ou executam ações quando chamadas. Elas são usadas para agrupar um conjunto de instruções relacionadas em um único nome, tornando o código mais organizado, reutilizável e modular.

## Sumário
- [[#Função Nomeada]]
- 

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
var nomeDaVariavel = function(parametro1, parametro2) {
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
var somar = function(numero1, numero2) {
    return numero1 + numero2;
};

var resultado = somar(5, 3); // Chama a função e armazena o resultado
console.log(resultado); // Exibe o resultado (8) no console
```

Neste exemplo, a função anônima é atribuída à variável `somar`, que pode ser usada para chamar a função, semelhante a uma função nomeada.

## Arrow Function
Arrow functions são uma forma alternativa de definir funções em JavaScript. Elas são chamadas "arrow functions" devido à sintaxe que utiliza uma seta => para definir a função. As arrow functions são geralmente mais curtas e mais legíveis do que as funções tradicionais, o que as torna populares entre os desenvolvedores.

A sintaxe básica de uma arrow function é a seguinte:

```javascript
const nomeDaFuncao = (parametro1, parametro2) => {
    // Bloco de código da função
    // Pode conter várias instruções
    return resultado;
};
```

- `nomeDaFuncao`: É uma constante ou variável à qual a função de seta é atribuída. Como as arrow functions geralmente são usadas como funções anônimas, essa variável não precisa ser uma constante e pode ser qualquer nome de variável válido.
- `parametro1`, `parametro2`: São os parâmetros da função, semelhantes às funções tradicionais.
- `bloco de código`: Contém as instruções que definem o comportamento da função.
- `resultado`: É o valor opcional retornado pela função.

Aqui está um exemplo simples de uma arrow function que calcula a soma de dois números:

```javascript
const somar = (numero1, numero2) => numero1 + numero2;

const resultado = somar(5, 3); // Chama a função e armazena o resultado
console.log(resultado); // Exibe o resultado (8) no console
```

Neste exemplo, a arrow function `somar` é uma forma mais concisa de declarar a função e é usada da mesma maneira que uma função tradicional.

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