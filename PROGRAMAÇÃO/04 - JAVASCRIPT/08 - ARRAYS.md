Arrays são estruturas de dados que armazenam coleções de elementos em JavaScript. Eles são usados para organizar dados como listas de nomes, números ou objetos, permitindo manipulá-los de forma eficiente.

## Declaração de Arrays

### Array Vazio
Você pode criar um array vazio simplesmente usando colchetes vazios:

```javascript
var vazio = [];
```

### Array Pré-inicializado
É possível criar um array com valores iniciais, separados por vírgulas, envolvidos por colchetes:

```javascript
const fruta = ['laranja', 'morango', 'abacate'];
console.log(fruta); // Exibe: ["laranja", "morango", "abacate"]
```

### Array usando o Construtor
Você também pode usar o construtor da classe Array para criar arrays:

```javascript
let legumes = new Array('brócolis', 'cenoura', 'alface');
```

```ad-hint
title: Dica
Prefira a sintaxe literal [] por ser mais simples e amplamente usada.
```

## Acessando Elementos

Os elementos de um array são acessados por índices, começando em 0

```javascript
const frutas = ['laranja', 'morango', 'abacate'];
console.log(frutas[2]); // Acessa o terceiro elemento ("abacate")
```

Você pode atribuir valores a elementos específicos do array da mesma maneira:

```javascript
const frutas = ['laranja', 'morango', 'abacate'];
frutas[3] = "limão";
frutas[4] = "physalis";
console.log(frutas)
```

## Tamanho do Array

Use a propriedade .length para saber quantos elementos o array contém:

```javascript
const frutas = ['laranja', 'morango', 'abacate'];
console.log("Tamanho do Array: " + frutas.length); 
```

## Métodos de Arrays

Aqui estão os principais métodos de arrays, organizados por funcionalidade:
### Adicionar e Remover Elementos

#### `push` Adiciona um ou mais elementos ao final do array.
```js
const frutas = ['laranja', 'morango', 'abacate'];
frutas.push("kiwi");
console.log(frutas); // ["laranja", "morango", "abacate", "kiwi"]
```

#### `pop` Remove e retorna o último elemento.
```js
const frutas = ['laranja', 'morango', 'abacate'];
let ultima = frutas.pop();
console.log(ultima); // "abacate"
```

#### `unshift` Adiciona elementos ao início.
```js
const frutas = ['laranja', 'morango', 'abacate'];
frutas.unshift("manga");
console.log(frutas); // ["manga", "laranja", "morango", "abacate"]
```

#### `shift` Remove e retorna o primeiro elemento.
```javascript
const frutas = ['laranja', 'morango', 'abacate'];
let primeira = frutas.shift();
console.log(primeira); // "laranja"
```

#### `splice` Adiciona ou remove elementos em uma posição específica.
```js
const frutas = ['laranja', 'morango', 'abacate'];
frutas.splice(1, 1, "pêra"); // Remove 1 elemento no índice 1 e adiciona "pêra"
console.log(frutas); // ["laranja", "pêra", "abacate"]
```

```ad-caution
title: Cuidado
O splice modifica o array original. Faça uma cópia se precisar preservá-lo.
```

### Consultar e Pesquisar

#### `indexOf` Retorna o índice da primeira ocorrência de um valor.
```javascript
const frutas = ['laranja', 'morango', 'abacate'];
console.log(frutas.indexOf("laranja")); // 0
```

#### `includes` Verifica se um valor existe no array.
```javascript
const frutas = ['laranja', 'morango', 'abacate'];
console.log(frutas.includes("maçã")); // false
```

#### `findIndex` Retorna o índice do primeiro elemento que satisfaz uma condição.
```javascript
const numeros = [5, 12, 8, 130, 44];
const indice = numeros.findIndex(num => num > 10);
console.log(indice); // 1 (índice de 12)
```

#### `find` Retorna o primeiro elemento que satisfaz uma condição.
```javascript
const numeros = [5, 12, 8, 130, 44];
const maiorQue10 = numeros.find(num => num > 10);
console.log(maiorQue10); // 12
```


```ad-info
title: Nota
Se nenhum elemento for encontrado
- findIndex retorna -1
- find retorna undefined
```


### Transformar e Filtrar

#### `filter` Cria um novo array com elementos que passam em um teste.
```javascript
const tarefas = [
  { nome: "Lavar louça", concluida: true },
  { nome: "Estudar", concluida: false }
];
const pendentes = tarefas.filter(tarefa => !tarefa.concluida);
console.log(JSON.stringify(pendentes)); // [{ nome: "Estudar", concluida: false }]
```

#### `map` Cria um novo array transformando cada elemento.
```javascript
const numeros = [5, 12, 8, 130, 44];
const dobrados = numeros.map(num => num * 2);
console.log(dobrados); // [10, 24, 16, 260, 88]
```

#### `reduce` Reduz o array a um único valor.
```javascript
const numeros = [5, 12, 8, 130, 44];
const soma = numeros.reduce((total, num) => total + num, 0);
console.log(soma); // 199
```

### Verificar Condições

#### `some` Verifica se pelo menos um elemento satisfaz uma condição.
```javascript
const numeros = [5, 12, 8, 130, 44];
console.log(numeros.some(num => num > 100)); // true
```

#### `every` Verifica se todos os elementos satisfazem uma condição.
```javascript
const numeros = [5, 12, 8, 130, 44];
console.log(numeros.every(num => num > 0)); // true
```

### Ordenar e Reorganizar

#### `sort` Ordena os elementos do array.
```javascript
let letras = ["c", "a", "b"];
letras.sort();
console.log(letras); // ["a", "b", "c"]
```

#### `reverse` Inverte a ordem dos elementos.
```javascript
let letras = ["a", "b", "c"];
letras.reverse();
console.log(letras); // ["c", "b", "a"]
```

### Combinar e Aplanar

#### `concat` Combina dois ou mais arrays.
```javascript
const frutas = ['laranja', 'morango', 'abacate'];
let maisFrutas = frutas.concat(["melancia", "abacaxi"]);
console.log(maisFrutas); // ["laranja", "morango", "abacate", "melancia", "abacaxi"]
```

#### `join` Junta todos os elementos em uma string.
```javascript
const frutas = ['laranja', 'morango', 'abacate'];
console.log(frutas.join(" - ")); // "laranja - morango - abacate"
```

#### `flat` Aplana arrays aninhados.
```javascript
let aninhado = [1, [2, 3], [4, [5]]];
console.log(aninhado.flat(1)); // [1, 2, 3, 4, [5]]
```

## Iteração em Arrays

Iterar um array significa percorrer todos os seus elementos para realizar alguma operação. Existem várias maneiras de fazer isso em JavaScript:

#### `forEach` Executa uma função para cada elemento.
```javascript
const frutas = ['laranja', 'morango', 'abacate'];
frutas.forEach(fruta => console.log(fruta));
// laranja
// morango
// abacate
```

## Desestruturação de Arrays

A desestruturação permite extrair elementos facilmente:

```javascript
const frutas = ['laranja', 'morango', 'abacate'];
let [primeira, segunda] = frutas;
console.log(primeira, segunda); // "laranja" "morango"
```

Com o operador `rest`:
```js
const frutas = ['laranja', 'morango', 'abacate'];
let [inicio, ...resto] = frutas;
console.log(resto); // ["morango", "abacate"]
```

## Cópias Rasas vs. Profundas

### Cópia Rasa: Copia apenas o nível superficial.

```js
let original = [{ nome: "Ana" }];
let copiaRasa = [...original];
copiaRasa[0].nome = "Beatriz";
console.log(original[0].nome); // "Beatriz" (referência alterada)
```

### Cópia Profunda: Copia todos os níveis

```js
let original = [{ nome: "Ana" }];
let copiaProfunda = JSON.stringify(original);
console.log(copiaProfunda)
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

### Encontrando um elemento:

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

O método `splice()` do JavaScript é uma ferramenta **versátil e poderosa** para adicionar e ou remover elementos de qualquer posição em um array, inclusive do meio. 

- Muda o array original diretamente, em vez de criar um novo. Fique atento a isso ao usá-lo!
- Retorna um novo array contendo os elementos que foram removidos**. Se nada foi removido, ele retorna um array vazio.

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

## Verificando se um array tem um determinado valor com `includes()`

É um método de array em JavaScript que **verifica se um valor existe dentro do array**. Ele retorna:

- `true` - se o valor for encontrado 
- `false` - se o valor não estiver no array
    
### Sintaxe

```javascript
let frutas = ["maçã", "banana", "laranja"];
console.log(frutas.includes("banana")); // true
console.log(frutas.includes("uva"));    // false
```

### Case-sensitive

```javascript
console.log(frutas.includes("banana")); // true
console.log(frutas.includes("Banana")); // false
```

### Começar a busca em um índice específico

Você pode passar um segundo argumento para dizer a partir de qual posição o JavaScript deve começar a procurar:

```javascript
let numeros = [10, 20, 30, 40, 30];
console.log(numeros.includes(30, 3)); // true (pois há um 30 depois do índice 3)
```

### Comparação estrita (`===`)

O `includes()` **diferencia tipos**:

```javascript
let misto = [1, "2", 3];
console.log(misto.includes(2));   // false (número)
console.log(misto.includes("2")); // true  (string)
```

## O que é uma shallow copy?

Uma **shallow copy** é uma nova array que **copia os elementos do array original**, mas **não copia objetos ou arrays aninhados** — apenas suas referências.

Ou seja: os elementos primitivos (números, strings, booleanos) são copiados, mas objetos internos **ainda apontam para os mesmos dados**.

### **Por que usar?**

Quando você quer **fazer alterações sem modificar o array original**, uma cópia rasa permite isso — mas **sem duplicar objetos internos**.

### **3 formas comuns de criar uma shallow copy**

1. Usando `concat()`: Você concatena um array vazio com o original, criando um novo array.

```javascript
let original = [1, 2, 3];
let copia = [].concat(original);

console.log(copia);              // [1, 2, 3]
console.log(copia === original); // false
```


2. Usando `slice()`: Sem argumentos, `slice()` retorna uma cópia do array inteiro.

```javascript
let original = [1, 2, 3];
let copia = original.slice();

console.log(copia);              // [1, 2, 3]
console.log(copia === original); // false
```

3. Usando o spread operator `...`: O spread "espalha" os elementos do array original em um novo array.

```javascript
let original = [1, 2, 3];
let copia = [...original];

console.log(copia);              // [1, 2, 3]
console.log(copia === original); // false
```

### Atenção com objetos dentro do array

Mesmo com shallow copy, **objetos internos continuam sendo os mesmos** — a alteração se reflete nos dois arrays.

```javascript
let original = [{ nome: "Elian" }];
let copia = [...original];

copia[0].nome = "Outro nome";

console.log(copia[0].nome); // Copia - "Outro nome"
console.log(original[0].nome); // Original - "Outro nome"
```

Use shallow copies para duplicar arrays de forma simples e rápida, mas cuidado com dados complexos. Para cópias profundas, outras técnicas são necessárias (como `structuredClone()` ou `JSON.parse(JSON.stringify())`, com limitações).