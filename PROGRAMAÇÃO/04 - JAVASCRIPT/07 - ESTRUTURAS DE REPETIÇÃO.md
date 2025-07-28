As estruturas de repetição, também conhecidas como loops, são usadas para executar um bloco de código repetidamente com base em uma condição ou um número predefinido de iterações.

Loops (ou laços) servem para repetir um bloco de código várias vezes. Eles são úteis, por exemplo, para:

- Listar todos os itens de um array.
- Mover um personagem em um jogo repetidamente.

## Sumário
- [[#While ]]
- [[#Do-While ]]
- [[#For]]
- [[#ForEach]]
- [[#For in]]
- [[#For of]]

## For

O loop `for` é usado quando você sabe exatamente quantas vezes deseja repetir uma operação. Ele possui três partes: a inicialização, a condição e a iteração.

### Sintaxe básica

```js
for (inicialização; condição; incremento/decremento) {
	// código que será repetido
}
```

1. Inicialização    
    - Acontece **antes** do loop começar.
    - Normalmente define uma **variável de contagem** (como `let i = 0`).

2. Condição
    - É **checada antes de cada repetição**.
    - Se for verdadeira, o código dentro do loop executa.
    - Se for falsa, o loop termina.

3. Incremento/Decremento
    - Executado **após cada repetição**.
    - Atualiza a variável de contagem (ex: `i++` significa `i = i + 1`).

### Exemplo

```javascript
for (let i = 0; i < 5; i++) {
  console.log(i);
}
```

**Explicação passo a passo:**

1. `i` começa em 0.
2. Verifica: `i < 5` → verdadeiro.
3. Executa: `console.log(i)` → imprime 0.
4. Incrementa: `i` vira 1.
5. Verifica de novo: `i < 5` → verdadeiro.
6. Repete o processo...

Isso continua até que `i` chegue a 5. Como `5 < 5` é falso, o loop para.

### Cuidado: Loop Infinito
Se a condição **nunca for falsa**, o loop **nunca para**. Isso é chamado de **loop infinito** e pode travar seu programa:

```javascript
for (let i = 0; i >= 0; i++) {
  console.log(i); // nunca vai parar
}
```

### Loops Aninhados
É possível colocar um loop dentro de outro: Isso é útil, por exemplo, para percorrer **matrizes** (listas dentro de listas).

```javascript
for (let i = 0; i < 3; i++) {
  for (let j = 0; j < 2; j++) {
    console.log(`i: ${i}, j: ${j}`);
  }
}
```



## For of 

O `for of` é um loop projetado especificamente para iterar sobre elementos em objetos iteráveis, fornecendo acesso direto ao valor de cada elemento, como:

- Arrays    
- Strings    
- Objetos iteráveis (como `Map`, `Set`, etc.)

### Sintaxe básica
A **variável** representa o valor atual a cada repetição.
O **iterável** é o que está sendo percorrido (array, string, etc.).

```javascript
for (variável of iterável) {
  // bloco de código
}
```

### Exemplo com array
A cada volta, `num` recebe o próximo número do array.

```javascript
const numeros = [2, 4, 6, 8, 10];

for (const num of numeros) {
  console.log(num);
}
```

### Exemplo com string
A cada repetição, `letra` recebe um caractere da string.

```javascript
const palavra = 'JavaScript';

for (let letra of palavra) {
  console.log(letra);
}
```

### `let` vs `const`
Você pode declarar a variável do loop com `let` ou `const`.

- Use `const` se **não for modificar o valor** da variável dentro do loop.
- Use `let` se **precisar alterar** esse valor.

```javascript
for (const num of [1, 2, 3]) {
  num = num + 1; // ❌ ERRO, pois `num` é constante
}
```

### Exemplo com array de objetos
Em cada iteração, `pessoa` representa um objeto do array.

```javascript
const pessoas = [
  { nome: 'Ana', idade: 28 },
  { nome: 'Bruno', idade: 35 },
];

for (const pessoa of pessoas) {
  console.log(`${pessoa.nome} tem ${pessoa.idade} anos`);
}
```

## While:
O loop `while` é usado quando a quantidade de repetições não é conhecida antecipadamente. O bloco de código é executado enquanto a condição especificada for verdadeira. No seu exemplo, a condição é `contador < 10`.

```javascript
var contador = 10;
console.log("Antes do While");

while (contador < 10) {
    contador++;
    console.log("while " + contador);
}

console.log("Depois do While");
```

Observe que, no seu exemplo, a condição inicial já é falsa, portanto o bloco de código dentro do `while` não será executado.

## Do-While:
O loop `do-while` é semelhante ao `while`, mas garante que o bloco de código seja executado pelo menos uma vez, mesmo que a condição seja falsa. A avaliação da condição ocorre após a primeira execução do bloco.

```javascript
var contador = 10;
console.log("Antes do do-While");

do {
    contador++;
    console.log("do-while " + contador);
} while (contador < 10);

console.log("Depois do do-While");
```

No exemplo, o bloco dentro do `do-while` é executado uma vez antes de verificar a condição. Se a condição fosse verdadeira, o bloco seria executado novamente, mas no seu caso, a condição é falsa desde o início.



## ForEach:
O `forEach` é um método disponível em todos os objetos do tipo array em JavaScript. Sua finalidade é percorrer cada elemento de um array e aplicar uma função de retorno de chamada a cada um deles. Isso permite que você realize ações específicas em cada elemento do array sem a necessidade de criar um loop manualmente.

A sintaxe básica do `forEach` é a seguinte:

```javascript
array.forEach(function(element, index, array) {
    // Código a ser executado para cada elemento
});
```

- `array`: É o array que você deseja percorrer.
- `element`: Representa o elemento atual do array em cada iteração.
- `index`: É o índice (posição) do elemento atual no array.
- `array`: É o próprio array que está sendo percorrido.

Aqui está um exemplo de uso do `forEach`:

```javascript
const frutas = ['maçã', 'banana', 'laranja', 'morango'];

frutas.forEach(function(fruta, index) {
    console.log(`A fruta no índice ${index} é ${fruta}`);
});
```

Neste exemplo, o `forEach` percorre o array `frutas`, e a função de retorno de chamada é executada para cada elemento. Ela imprime uma mensagem informando a fruta e o índice correspondente no array.

## For in:
O `for in` é um tipo de loop utilizado para percorrer as propriedades de um objeto. Ele não é projetado para iterar diretamente sobre os valores dos elementos em um array, embora possa ser usado dessa maneira. Em vez disso, ele se destina principalmente para objetos, onde você deseja acessar as chaves (nomes) das propriedades do objeto.

A sintaxe básica do `for in` é a seguinte:

```javascript
for (const key in objeto) {
    // Código a ser executado para cada propriedade do objeto
}
```

- `objeto`: O objeto cujas propriedades você deseja percorrer.
- `key`: Representa o nome da propriedade do objeto a ser acessada em cada iteração.

Aqui está um exemplo de uso do `for in` com um objeto:

```javascript
const pessoa = {
    nome: "João",
    idade: 30,
    profissao: "Engenheiro"
};

for (const propriedade in pessoa) {
    console.log(`A propriedade ${propriedade} tem o valor ${pessoa[propriedade]}`);
}

//A propriedade nome tem o valor João
//A propriedade idade tem o valor 30
//A propriedade profissao tem o valor Engenheiro
```

Neste exemplo, o `for in` percorre as propriedades do objeto `pessoa`, permitindo o acesso às chaves (nome das propriedades) e seus valores.

## For of
O `for of` é um loop projetado especificamente para iterar sobre elementos em objetos iteráveis, fornecendo acesso direto ao valor de cada elemento. Ele é mais adequado para situações em que você deseja acessar os valores de um objeto iterável em vez de se preocupar com os índices ou chaves das propriedades, como é comum no `for in`.

A sintaxe básica do `for of` é a seguinte:

```javascript
for (const elemento of objetoIteravel) {
    // Código a ser executado para cada elemento do objetoIteravel
}
```

- `objetoIteravel`: O objeto que você deseja percorrer, como um array, string, conjunto, mapa, etc.
- `elemento`: Representa o valor do elemento atual em cada iteração.

Aqui está um exemplo de uso do `for of` com um array:

```javascript
const frutas = ['maçã', 'banana', 'laranja', 'morango'];

for (const fruta of frutas) {
    console.log(`Uma fruta: ${fruta}`);
}

//Uma fruta: maçã
//Uma fruta: banana
//Uma fruta: laranja
//Uma fruta: morango
```

Neste exemplo, o `for of` percorre o array `frutas` e permite o acesso direto aos valores de cada elemento, tornando o código mais simples e legível.