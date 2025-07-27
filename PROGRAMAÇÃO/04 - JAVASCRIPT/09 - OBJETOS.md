## Sintaxe Básica

Um **objeto** é uma estrutura que **armazena dados em pares chave-valor** (também chamados de **propriedades**). Ele é como uma "caixa" onde cada coisa tem um nome (a chave) e um conteúdo (o valor).

```javascript
const pessoa = {
  nome: "Alice",
  idade: 30,
  cidade: "Nova York"
};
```

- `"nome"`, `"idade"` e `"cidade"` são **chaves**
- `"Alice"`, `30` e `"Nova York"` são os **valores**

### Como acessar as propriedades de um objeto

#### Notação por ponto (`.`)
É a forma mais comum e fácil de ler:

```javascript
console.log(pessoa.nome);  // Alice
console.log(pessoa.idade); // 30

// Só pode ser usada quando a chave for um nome válido de variável (sem espaços, não começa com número, etc.)

```


#### Notação por colchetes (`[]`)
Permite acessar as propriedades usando **strings**:

```javascript
console.log(pessoa["nome"]);  // Alice
console.log(pessoa["idade"]); // 30
```

Essa forma é mais **flexível**, pois permite:

- Usar **nomes de propriedade inválidos** como identificadores:

```javascript
const estranho = {
  "1aChave": "valor1",
  "com espaços": "valor2"
};

console.log(estranho["1aChave"]);     // valor1
console.log(estranho["com espaços"]); // valor2
```

- Usar **variáveis** como chave:

```javascript
let propriedade = "cidade";
console.log(pessoa[propriedade]); // Nova York
```

## **O que é Object Destructuring?**

**Destructuring** é uma forma de **extrair valores de um objeto e atribuí-los a variáveis** de forma concisa.

Em vez de acessar propriedades uma por uma (`obj.prop`), você pode extrair várias de uma só vez.

### Sintaxe
Aqui estamos criando variáveis `nome` e `idade` diretamente a partir das propriedades do objeto.

```javascript
const pessoa = { nome: "Alice", idade: 30, cidade: "Nova York" };

const { nome, idade } = pessoa;

console.log(nome);  // Alice
console.log(idade); // 30
```

### Renomeando variáveis durante a extração
Você pode **dar outro nome** para a variável que recebe a propriedade:

```javascript
const pessoa = { nome: "Alice", idade: 30 };

const { nome: nomePessoa, idade: idadePessoa } = pessoa;

console.log(nomePessoa);  // Alice
console.log(idadePessoa); // 30
```

### Valores padrão
Se a propriedade não existir no objeto, você pode **definir um valor padrão**:

```javascript
const pessoa = { nome: "Alice" };

const { nome, pais = "Desconhecido" } = pessoa;

console.log(pais); // "Desconhecido"
```

### Destructuring em funções
Muito útil para extrair dados de objetos passados como parâmetro:

```javascript
function exibirPessoa({ nome, idade }) {
  console.log(`${nome} tem ${idade} anos`);
}

const pessoa = { nome: "Bob", idade: 25 };
exibirPessoa(pessoa); // Bob tem 25 anos
```

### Shorthand na criação de objetos
Se o nome da variável for o mesmo do nome da propriedade, você pode usar **notação curta**:

```javascript
let nome = "Carlos";
let idade = 28;

let pessoa = { nome, idade };
console.log(pessoa); // { nome: "Carlos", idade: 28 }
```


## Removendo propriedades de um objeto

Há várias maneiras de remover propriedades de um objeto, sendo o operador delete o método mais simples e comumente usado.
### Usando o operador `delete`
O jeito mais direto de **remover uma propriedade** de um objeto existente.

```javascript
const pessoa = {
  nome: "Alice",
  idade: 30,
  profissao: "Engenheira"
};

delete pessoa.profissao;

console.log(pessoa); // { nome: "Alice", idade: 30 }
```

- Modifica o objeto original
- Não funciona em objetos com `sealed` ou `frozen`

### Usando destructuring com rest (`...`)
Esse método não altera o objeto original, mas **cria um novo sem as propriedades indesejadas**.

```javascript
const pessoa = {
  nome: "Bob",
  idade: 25,
  cidade: "Nova York",
  profissao: "Designer"
};

const { cidade, profissao, ...restante } = pessoa;

console.log(restante); // { nome: "Bob", idade: 25 }
```

- Ideal quando você quer preservar o original  
- Funciona bem com objetos imutáveis ou programação funcional

## Verificar sem um objeto tem uma determinada propriedade

### Usando `hasOwnProperty()`
Verifica se o objeto **possui diretamente** a propriedade (sem considerar heranças).

```javascript
const pessoa = { nome: "Alice", idade: 30 };

console.log(pessoa.hasOwnProperty("nome")); // true
console.log(pessoa.hasOwnProperty("profissao")); // false
```

### Usando o operador `in`

Verifica se **a propriedade existe no objeto**, **mesmo que tenha vindo da herança (prototype)**:

```javascript
const pessoa = { nome: "Bob", idade: 25 };

console.log("nome" in pessoa);      // true
console.log("toString" in pessoa);  // true (vem do protótipo)
```

### Verificando contra `undefined`
Você pode simplesmente testar se a propriedade **não é `undefined`**:

```javascript
const carro = {
  marca: "Toyota",
  modelo: "Corolla",
  ano: undefined
};

console.log(carro.marca !== undefined); // true
console.log(carro.cor !== undefined);   // false
```

Cuidado! Se a propriedade existir mas tiver valor `undefined`, o teste falhará — mesmo que ela exista.


## O que são objetos e arrays aninhados?

São estruturas de dados que **contêm outros objetos ou arrays dentro de si** — comuns em APIs e bancos de dados.

```javascript
const pessoa = {
  nome: "Alice",
  idade: 30,
  contato: {
    email: "alice@example.com",
    telefone: {
      residencial: "123-456-7890",
      trabalho: "098-765-4321"
    }
  }
};
```

### Como acessar propriedades aninhadas

#### Usando notação por ponto (`.`)
```javascript
console.log(pessoa.contato.telefone.trabalho); // "098-765-4321"
```

#### Usando notação por colchetes (`[]`)
Útil quando a propriedade tem espaços, caracteres especiais ou quando vem de uma variável.
```javascript
console.log(pessoa["contato"]["telefone"]["trabalho"]); // "098-765-4321"
```

### Acessando arrays dentro de objetos

Aqui acessamos o **segundo item do array** (`[1]`) e depois a propriedade `cidade`.

```javascript
const pessoa = {
  nome: "Alice",
  idade: 30,
  enderecos: [
    { tipo: "casa", rua: "Rua A", cidade: "Cidade 1" },
    { tipo: "trabalho", rua: "Rua B", cidade: "Cidade 2" }
  ]
};

console.log(pessoa.enderecos[1].cidade); // "Cidade 2"
```

### Boas práticas ao acessar dados aninhados

Acessar algo que **não existe** resulta em erro:
```javascript
console.log(pessoa.contato.whatsapp.numero); 
// ❌ Erro: Cannot read properties of undefined
```

Use **optional chaining (`?.`)** para evitar isso:
```javascript
console.log(pessoa.contato?.whatsapp?.numero); // undefined (sem erro)
```

## Diferença entre tipos primitivos e não primitivos

Em JavaScript, os **tipos de dados** se dividem em **primitivos** e **não primitivos**, e entender essa diferença é essencial para evitar bugs e escrever código eficiente.

### Tipos Primitivos
São os tipos mais simples. Incluem: `number`, `string`, `boolean`, `null`, `undefined` e `symbol`.

Eles **armazenam diretamente o valor** na variável. São **imutáveis**, ou seja, não dá para alterar o valor original, apenas substituir por outro.

```js
let num1 = 5;
let num2 = num1;
num1 = 10;
console.log(num2); // 5
```
    
`num2` continua com o valor 5, porque ele **recebeu uma cópia do valor**, não uma referência.

### Tipos Não Primitivos (Objetos)
São estruturas mais complexas, como: `Object`, `Array` e `Function`.
    
As variáveis armazenam **uma referência na memória**, e não o valor em si. Isso significa que **alterações em uma variável afetam todas que apontam para o mesmo objeto**.

```js
const original = { age: 30 };
const copia = original;
original.age = 31;
console.log(copia.age); // 31
```

`copia` reflete a alteração porque **ambas apontam para o mesmo objeto**.

### Resumindo

| Característica | Tipos Primitivos        | Tipos Não Primitivos          |
| -------------- | ----------------------- | ----------------------------- |
| Armazenamento  | Valor direto            | Referência (ponteiro)         |
| Cópia          | Cópia do valor          | Cópia da referência           |
| Imutabilidade  | Imutáveis               | Mutáveis                      |
| Exemplos       | `number`, `string`, etc | `object`, `array`, `function` |

## Diferença entre Funções e Métodos

**Funções** e **métodos** são formas de organizar e reutilizar código em JavaScript. Ambos são blocos de código que executam tarefas, mas **funcionam em contextos diferentes**.

### Funções
- São blocos de código independentes.
- Não estão associadas a nenhum objeto.
- Usadas para tarefas gerais e reutilizáveis.
    
```javascript
function greet(name) {
  return "Hello, " + name + "!";
}
console.log(greet("Alice")); // "Hello, Alice!"
```

### Métodos
- São funções **associadas a objetos**.
- Definidas como **propriedades de um objeto**.
- Usam `this` para acessar os dados internos do objeto.

```javascript
const person = {
  name: "Bob",
  sayHello: function() {
    return "Hello, my name is " + this.name;
  }
};

console.log(person.sayHello()); // "Hello, my name is Bob"
```


## O que é o construtor `Object()`?

`Object()` é um **construtor** usado para **criar e inicializar objetos** em JavaScript. Ele pode ser chamado com ou sem a palavra-chave `new`.

```javascript
const obj1 = new Object(); // cria um objeto vazio
const obj2 = Object();     // também cria um objeto, mas com comportamento diferente dependendo do valor passado
```

### Quando usar `Object()`?
Geralmente, **você não usa `Object()` para criar objetos novos**. Em vez disso, usa a **sintaxe literal**:

```javascript
const pessoa = { nome: "João" };
```

### Casos de uso
#### Garantir que um valor seja tratado como objeto
Aqui, o número foi convertido para um objeto wrapper.

```javascript
const numero = 42;
const numeroObj = Object(numero);
console.log(typeof numeroObj); // "object"
```

#### Lidar com valores de tipo desconhecido
Essa função garante que qualquer valor (inclusive primitivos como `true`, `42`, `"texto"`) seja transformado em um objeto, o que é útil em códigos mais genéricos.

```javascript
function toObject(value) {
  if (value === null || value === undefined) return {};
  if (typeof value === "object") return value;
  return Object(value);
}
```

### E se passar `null` ou `undefined`?
Resultado: um **objeto vazio**.

```javascript
const vazio = Object(null);
console.log(vazio); // {}
```

