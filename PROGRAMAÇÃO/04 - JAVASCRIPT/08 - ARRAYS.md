Os arrays são uma estrutura de dados essencial em JavaScript, usados para armazenar coleções de elementos. Eles são versáteis e podem conter vários tipos de dados, incluindo números, strings, objetos e até mesmo outros arrays. Vamos explorar os conceitos-chave relacionados a arrays:

## Sumário
- [[#Declaração de Arrays]]
- [[#Acessando Elementos]]
- [[#Tamanho do Array]]
- [[#Iteração em Arrays]]
- [[#Inserindo Elementos]]
- [[#Removendo Elementos]]
- [[#Construindo uma Fila e uma Pilha]]
- [[#Exibindo o Array]]
- [[#Referência de Arrays]]
- [[#Cópia de Valores]]
- [[#JavaScript Object]]
## Declaração de Arrays

Há várias maneiras de declarar um array em JavaScript:

1. **Array Vazio:**
   Você pode criar um array vazio simplesmente usando colchetes vazios:
   
   ```javascript
   var carro = [];
   ```

2. **Array Pré-inicializado:**
   É possível criar um array com valores iniciais, separados por vírgulas, envolvidos por colchetes:

```javascript
const fruta = ['laranja', 'morango', 'abacate'];
console.log(fruta); // Exibe: ["laranja", "morango", "abacate"]
```

3. **Array usando o Construtor:**
   Você também pode usar o construtor da classe Array para criar arrays:

```javascript
let legumes = new Array('brócolis', 'cenoura', 'alface');
```

## Acessando Elementos

Os elementos de um array são acessados por meio de índices. Os índices são baseados em zero, ou seja, o primeiro elemento está no índice 0, o segundo no índice 1, e assim por diante.

```javascript
const fruta = ['laranja', 'morango', 'abacate'];
var frutaCitrica = fruta[2]; // Acessa o terceiro elemento ("abacate")
```

Você pode atribuir valores a elementos específicos do array da mesma maneira:

```javascript
fruta[3] = "limão";
fruta[4] = "physalis";
// fruta["laranja", "morango", "abacate", "limão", "physalis"]
```

## Tamanho do Array

Você pode obter o tamanho (número de elementos) de um array usando a propriedade `.length`:

```javascript
console.log("Tamanho do Array: " + fruta.length); 
// Exibe o número de elementos no array - 5 elementos
```

Lembre-se de que o tamanho de um array é dinâmico, e você pode adicionar ou remover elementos a qualquer momento.

## Iteração em Arrays

Para percorrer todos os elementos de um array, você pode usar loops, como `for` ou `forEach`. Isso é útil para processar todos os elementos de uma coleção.

```javascript
for (let i = 0; i < fruta.length; i++) {
    console.log(fruta[i]);
}
```

Outra maneira é usar o método `forEach`, que é uma forma mais elegante e legível de percorrer os elementos de um array:

```javascript
fruta.forEach(function(elemento) {
    console.log(elemento);
});
```

Os arrays são fundamentais em JavaScript, e dominar o uso deles é crucial para muitos aspectos do desenvolvimento web e de aplicativos. Eles são usados para armazenar, manipular e acessar dados de forma eficaz, tornando-se uma ferramenta poderosa na caixa de ferramentas de um desenvolvedor JavaScript.

## Inserindo Elementos

Para adicionar um novo elemento ao final de um array, você pode usar o método `push` ou simplesmente atribuir um valor a um índice após o último elemento do array:

  ```javascript
  fruta = []                     // length 0
  fruta[fruta.length] = "melão"; // fruta["melão"]
  fruta.push("Amora");           // fruta["melão", "amora"]
  ```

Para inserir um elemento no início do array, você pode usar o método `unshift`:

  ```javascript
  fruta.unshift("Banana");       // fruta["banana", "melão", "amora"]
  ```

## Removendo Elementos
Para remover o primeiro elemento de um array e retorná-lo, use o método `shift`:

```javascript
var fruta = ["banana", "melão", "amora"]
var fruta3 = fruta.shift();              // banana
console.log("fruta 3 - " + fruta3);      // fruta 3 - banana
// fruta["melão", "amora"]
```

Para remover o último elemento de um array e retorná-lo, use o método `pop`:

```javascript
var fruta = ["banana", "melão", "amora"]
var fruta4 = fruta.pop();                // amora
console.log("fruta 4 - " + fruta4);      // fruta 4 - amora
// fruta["banana", "melão"]
```

Essas operações de inserção e remoção são úteis para construir estruturas de dados como filas (onde o primeiro elemento a entrar é o primeiro a sair) e pilhas (onde o último elemento a entrar é o primeiro a sair).

## Construindo uma Fila e uma Pilha
- **Fila:** Para criar uma fila, você pode usar o método `shift` para remover o primeiro elemento inserido e `push` para adicionar elementos ao final. Dessa forma, o primeiro elemento inserido é o primeiro a ser removido.

- **Pilha:** Para construir uma pilha, use o método `pop` para remover o último elemento inserido e `push` para adicionar elementos ao final. Isso garante que o último elemento inserido seja o primeiro a ser removido, seguindo o conceito de uma pilha.

```javascript
// Construindo uma fila
fruta.push("Primeiro");
fruta.push("Segundo");

var primeiroItem = fruta.shift();
console.log("Fila - Primeiro a entrar, primeiro a sair: " + primeiroItem);

// Construindo uma pilha
fruta.push("Primeiro");
fruta.push("Segundo");

var ultimoItem = fruta.pop();
console.log("Pilha - Último a entrar, primeiro a sair: " + ultimoItem);
```

Os arrays em JavaScript são muito versáteis e oferecem uma série de métodos para manipulação. Com essas operações, é possível construir várias estruturas de dados úteis e realizar tarefas de processamento de dados de forma eficiente.

## Iterando um Array

Iterar um array significa percorrer todos os seus elementos para realizar alguma operação. Existem várias maneiras de fazer isso em JavaScript:

```javascript
for (let index = 0; index < fruta.length; index++) {
    let element = fruta[index];
    console.log(fruta[index]);
    console.log("Fruta[" + index + "] -> " + element);
}
```

Neste exemplo, usamos um loop `for` para percorrer cada elemento do array `fruta`. A variável `index` é usada para acessar os elementos do array. Cada elemento é exibido no console, juntamente com seu índice.

Você também pode usar métodos como `forEach` para iterar sobre um array de forma mais elegante e legível:

```javascript
fruta.forEach(function(elemento) {
    console.log(elemento);
});
```

## Exibindo o Array
Existem diferentes maneiras de exibir um array no console:

- `console.log(fruta)`: Isso exibe o array completo no console.
  
- `console.log(fruta.toString())`: Isso converte o array em uma string e o exibe no console.
  
- `console.table(fruta)`: Isso exibe o array como uma tabela no console, tornando mais fácil de ler quando se trata de arrays mais complexos.

```javascript
console.log(fruta);
console.log(fruta.toString());
console.table(fruta);
```

### Referência de Arrays

Ao atribuir um array a outra variável, você está passando uma referência ao array, não uma cópia dos valores. Isso significa que ambas as variáveis apontam para o mesmo array na memória. Qualquer modificação feita em uma das variáveis afetará o array original e todas as outras variáveis que o referenciam.

```javascript
var fruta = ["banana", "melão", "amora"]
var fruta2 = fruta; // fruta2 agora se refere ao mesmo array que fruta

fruta[2] = "Limão"; // Modifica o array original

console.log(fruta); // Exibe o array com "Limão" na posição 2
console.log(fruta2); // Exibe o array com "Limão" na posição 2 também
```

### Cópia de Valores

Para criar uma cópia independente de um array, você pode usar técnicas como `slice()` ou o operador de propagação (`...`).

```javascript
var frutaCopia = fruta.slice(); // Cria uma cópia de fruta

// Ou usando o operador de propagação (ES6)
var frutaCopia2 = [...fruta];

fruta[2] = "Pêssego";

console.log(fruta); // Exibe o array original com "Pêssego" na posição 2
console.log(frutaCopia); // Exibe a cópia sem a modificação
console.log(frutaCopia2); // Exibe a segunda cópia sem a modificação
```

Lembre-se de que entender como as referências funcionam é importante ao trabalhar com arrays em JavaScript, pois pode evitar erros inesperados em seu código.

**Método `slice()`:**

O método `slice()` é uma forma eficaz de criar uma cópia independente de um array, especificando os índices de início e fim do intervalo que você deseja copiar. Ele não modifica o array original e retorna um novo array contendo os elementos do intervalo especificado. O formato geral é o seguinte:

```javascript
novoArray = arrayOriginal.slice(início, fim);
```

- `arrayOriginal`: O array do qual você deseja criar uma cópia.
- `início`: O índice onde a cópia deve começar (inclusive).
- `fim`: O índice onde a cópia deve terminar (exclusivo).

Vamos ver um exemplo:

```javascript
var fruta = ['maçã', 'banana', 'laranja', 'uva', 'pêssego'];
var frutaCopia = fruta.slice(1, 4);

console.log(frutaCopia); // Exibe: ['banana', 'laranja', 'uva']
```

No exemplo acima, `frutaCopia` contém uma cópia dos elementos de `fruta` do índice 1 (inclusive) ao índice 4 (exclusivo). Observe que o array original, `fruta`, não foi modificado.

**Operador de Propagação (`...`):**

O operador de propagação, introduzido no ECMAScript 6 (ES6), permite criar cópias de arrays (ou objetos) de uma maneira mais concisa. Você simplesmente usa `...` seguido do array que deseja copiar. Veja como funciona:

```javascript
var fruta = ['maçã', 'banana', 'laranja', 'uva', 'pêssego'];
var frutaCopia = [...fruta];

console.log(frutaCopia); // Exibe uma cópia idêntica de fruta
```

O operador de propagação cria uma cópia rasa do array, o que significa que, se o array contiver objetos ou arrays aninhados, eles ainda serão referências aos mesmos objetos. No entanto, para a maioria dos casos em que você deseja copiar um array simples, o operador `...` é uma alternativa conveniente e legível.

Ambos os métodos, `slice()` e o operador de propagação `(...)`, são úteis para criar cópias independentes de arrays, o que é fundamental para evitar efeitos colaterais indesejados em seu código e garantir a integridade dos dados. Escolha o método que melhor se adapta às necessidades do seu projeto.

## Unidimensional e Bidimensional
### Uma Dimensão

Um **array unidimensional** é como uma única fila de caixas, onde cada caixa guarda um item. Para acessar um item, você usa apenas um **índice**, que é como o número da caixa.

Para pegar "banana", você usaria `fruits[1]`.
```javascript
// fruits = [   0  ,     1   ,     2   ]
   fruits = ["maçã", "banana", "cereja"]
```

### Duas Dimensões

Um **array bidimensional** é como uma grade de caixas, com múltiplas linhas e colunas. Pense em uma planilha. Para acessar um item, você precisa de **dois índices**: um para a linha e outro para a coluna. Basicamente, é um "array de arrays".

Para acessar "N", você usaria `chessboard[0][1]` (primeira linha, segunda coluna).
```javascript
chessboard = [["R", "N"],["P", "P"]]

// Para ilustrar melhor
// [R, N] -> [0, 1]
// [P, P] -> [1, 1]
```

A principal diferença é a forma como os dados são organizados e acessados:

- **Unidimensional:** Uma linha, um índice. Ideal para listas simples.    
- **Bidimensional:** Uma grade, dois índices. Ideal para dados com estrutura de tabela ou matriz.


## Desestruturação de Arrays

**Array destructuring** é um recurso do JavaScript que permite extrair valores de arrays e atribuí-los a variáveis de forma mais direta e legível. Ele simplifica a "desembalagem" de elementos de um array em variáveis separadas.

1. **Atribuição concisa:** Em vez de acessar elementos por índice (ex: `fruits[0]`), você pode atribuir diretamente os valores a variáveis dentro de colchetes `[]`, seguindo a ordem dos elementos no array.
      
```javascript
let fruits = ["apple", "banana", "orange"];
let [primeira, segunda, terceira] = fruits;

console.log(primeira); // "apple"
```
    
2. **Pular elementos:** Você pode ignorar elementos do array que não te interessam usando vírgulas `,,` no padrão de desestruturação.
    
```javascript
let colors = ["red", "green", "blue", "yellow"];
let [primeiraCor, , terceiraCor] = colors; // "green" é ignorado

console.log(primeiraCor); // "red"
console.log(terceiraCor); // "blue"
```
    
3. **Valores padrão:** Se o array tiver menos elementos do que as variáveis que você está tentando atribuir, você pode definir valores padrão para as variáveis, evitando que elas fiquem `undefined`.
    
```javascript
let numbers = [1, 2];
let [a, b, c = 3] = numbers; // c recebe 3 se não houver um terceiro elemento

console.log(c); // 3
```
    
4. **Sintaxe "rest" (`...`):** Os três pontos (`...`) permitem coletar todos os elementos restantes de um array que não foram desestruturados em um novo array. A sintaxe "rest" deve ser o último elemento no padrão de desestruturação.
    
```javascript
let fruits = ["apple", "banana", "orange", "mango", "kiwi"];
let [primeira, segunda, ...resto] = fruits;

console.log(primeira); // "apple"
console.log(resto);   // ["orange", "mango", "kiwi"]
```


## Invertendo uma String com Arrays

Reverter uma string é uma tarefa comum em programação e pode ser feita em JavaScript usando uma combinação de métodos de string e array. O processo envolve três etapas principais:

### Dividir a string em um array de caracteres: `split()`

O primeiro passo é transformar a string em um array de caracteres individuais. Para isso, usa-se o método **`split()`**. Se você passar uma string vazia `("")` como argumento, ele divide a string em cada caractere.

```javascript
let str = "olá";
let charArray = str.split("");
console.log(charArray); // ["o", "l", "á"]
```

### Inverter a ordem do array: `reverse()`

Uma vez que você tem um array de caracteres, o método **`reverse()`** inverte a ordem dos elementos _no próprio array_.

```javascript
let charArray = ["o", "l", "á"];
charArray.reverse();
console.log(charArray); // ["á", "l", "o"]
```

### Juntar os caracteres de volta em uma string: `join()`

O passo final é converter o array invertido de volta para uma string. O método **`join()`** faz isso, concatenando todos os elementos do array. Se você passar uma string vazia `("")` como argumento, os caracteres serão unidos sem nenhum separador.

```javascript
let reversedArray = ["á", "l", "o"];
let reversedString = reversedArray.join("");
console.log(reversedString); // "álos"
```

É importante notar que strings em JavaScript são **imutáveis**, o que significa que você não pode modificá-las diretamente. Por isso, é necessário convertê-las em um array, inverter o array e depois transformá-lo de volta em uma string.

## Pegando o índice de um elemento do array com `indexOf()`

O método `indexOf()` em JavaScript serve para **encontrar a posição (índice)** de um elemento dentro de um array. Ele **retorna o índice da primeira ocorrência** do valor procurado. Caso o valor **não esteja presente no array**, ele retorna -1.

### Sintaxe básica:

```js
array.indexOf(elemento, índiceInicial)
```

- `elemento`: o valor que você quer encontrar.
- `índiceInicial` (opcional): a posição do array onde a busca deve começar. Se não for informado, a busca começa do início (`índice 0`).

### Exemplo – Encontrando um elemento:

```js
// Encontrando um elemento
// Neste exemplo, "banana" aparece pela primeira vez no índice 1, e é isso que `indexOf()` retorna.
let frutas = ["maçã", "banana", "laranja", "banana"];
let indice = frutas.indexOf("banana");
console.log(indice); // 1

// Elemento não encontrado
// Como "uva" não está no array, indexOf() retorna -1
frutas = ["maçã", "banana", "laranja"];
indice = frutas.indexOf("uva");
console.log(indice); // -1

// Usando o índice inicial
// Aqui, a busca por "verde" começa a partir do índice 3 (ou seja, depois do primeiro "verde"). O método então encontra a próxima ocorrência no índice 4
let cores = ["vermelho", "verde", "azul", "amarelo", "verde"];
indice = cores.indexOf("verde", 3);
console.log(indice); // 4
```
### Resumo:

- `indexOf()` retorna o **índice da primeira ocorrência** de um valor.
- Retorna `-1` se o valor **não existir**.
- Pode começar a busca de um **índice específico em diante**.

## Manipulando Arrays com `splice()`

O método `splice()` do JavaScript é uma ferramenta **versátil e poderosa** para **adicionar ou remover elementos de qualquer posição em um array**, inclusive do meio.

Ele **muda o array original** diretamente, em vez de criar um novo. Fique atento a isso ao usá-lo!

O método `splice()` **retorna um novo array contendo os elementos que foram removidos**. Se nada foi removido, ele retorna um array vazio.

### Sintaxe

```js
array.splice(startIndex, itemsToRemove, item1, item2, ...)
```

- startIndex:
	O índice onde a modificação começa.
	
- itemsToRemove (opcional): 
	Quantos elementos serão removidos a partir do `startIndex`. Se você não informar, ele remove tudo dali até o final do array.
	
- item1, item2, ...(opcional):
	Os novos elementos que você quer adicionar no array, a partir do `startIndex`.

### Remover elementos

```js
let frutas = ["maçã", "banana", "laranja", "manga", "kiwi"];
let removidas = frutas.splice(2, 2); // Começa no índice 2, remove 2 elementos ("laranja", "manga")

console.log(frutas);   // ["maçã", "banana", "kiwi"]
console.log(removidas); // ["laranja", "manga"]
```
### Adicionar elementos

```js
let cores = ["vermelho", "verde", "azul"];
cores.splice(1, 0, "amarelo", "roxo"); // Começa no índice 1, não remove nada (0), adiciona "amarelo" e "roxo"

console.log(cores); // ["vermelho", "amarelo", "roxo", "verde", "azul"]
```
### Remover e adicionar ao mesmo tempo
    
```js
let numeros = [1, 2, 3, 4, 5];
numeros.splice(1, 2, 6, 7, 8); // Começa no índice 1, remove 2 elementos (2, 3), adiciona 6, 7, 8

console.log(numeros); // [1, 6, 7, 8, 4, 5]
```
### Remover um elemento específico (sabendo o índice)
    
```js
let frutas = ["maçã", "banana", "laranja", "manga"];
let indiceParaRemover = frutas.indexOf("laranja"); // Encontra o índice de "laranja"

if (indiceParaRemover !== -1) { // Verifica se o elemento existe
	frutas.splice(indiceParaRemover, 1); // Remove 1 elemento a partir desse índice
}

console.log(frutas); // ["maçã", "banana", "manga"]
```
### Limpar um array
    
```js
let array = [1, 2, 3, 4, 5];
array.splice(0); // Remove todos os elementos a partir do índice 0

console.log(array); // []
```

```ad-caution
title: Cuidado com a mutação do array original!

Como o `splice()` modifica o array original, se você precisar **manter o array original intacto**, crie uma **cópia** dele antes de usar `splice()`. Você pode usar o **operador `spread` (`...`)** para isso:
```

```js
let original = [1, 2, 3, 4, 5];
let copia = [...original]; // Cria uma cópia rasa do array original
copia.splice(2, 1, 6); // Modifica apenas a cópia

console.log(original); // [1, 2, 3, 4, 5] (original permanece inalterado)
console.log(copia);   // [1, 2, 6, 4, 5]
```

### Quando usar e quando não usar?

O `splice()` é excelente para um controle preciso sobre a modificação de arrays. No entanto, para arrays muito grandes, **pode ser menos eficiente**, especialmente se você estiver adicionando ou removendo elementos no início do array, pois ele precisa "reorganizar" todos os elementos subsequentes.

Para adicionar ou remover apenas do final do array, métodos como `push()` (adicionar ao final) e `pop()` (remover do final) são mais eficientes. Para o início, `unshift()` (adicionar ao início) e `shift()` (remover do início) são as melhores opções.

Em resumo, o `splice()` é uma ferramenta fundamental para manipular arrays em JavaScript, oferecendo flexibilidade para adicionar ou remover elementos em qualquer posição.