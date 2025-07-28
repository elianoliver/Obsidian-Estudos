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


## For in

O `for...in` é um tipo de loop em JavaScript usado para **percorrer as propriedades (chaves)** de um **objeto**.

Ele percorre **todas as propriedades enumeráveis**, incluindo:

- Propriedades definidas no próprio objeto
- Propriedades herdadas da cadeia de protótipos

### Sintaxe básica

```javascript
for (variável in objeto) {
  // bloco de código
}
```

- A **variável** representa a **chave atual** (nome da propriedade).
- Você pode acessar o **valor** da propriedade com `objeto[variável]`.

### Exemplo com objeto simples
Aqui, `prop` será `"nome"`, `"cor"` e `"preco"` em cada repetição.

```javascript
const fruta = {
  nome: 'maçã',
  cor: 'vermelha',
  preco: 1.25
};

for (const prop in fruta) {
  console.log(fruta[prop]);
}
```

### Exemplo com objeto aninhado
Nesse caso, a propriedade `endereco` é um **objeto aninhado**.

```javascript
const pessoa = {
  nome: 'João',
  idade: 30,
  endereco: {
    rua: 'Rua A',
    cidade: 'Bairro B',
    estado: 'SP'
  }
};

for (const prop in pessoa) {
  console.log(pessoa[prop]);
}
```

### Acessando propriedades internas com loop aninhado

Se você quiser percorrer as **propriedades internas**, use um `for...in` dentro de outro:

Essa lógica garante que você **não entre em arrays** nem em `null`, que são tratados como objetos por engano em JavaScript.

```javascript

const pessoa = { 
	nome: 'João', 
	idade: 30, 
	endereco: {
		rua: 'Rua A', 
		cidade: 'Bairro B', 
		estado: 'SP' 
	} 
};

function isObjeto(val) {
  return typeof val === 'object' && !Array.isArray(val) && val !== null;
}

for (const prop in pessoa) {

  if (isObjeto(pessoa[prop])) {
  
    for (const subprop in pessoa[prop]) {
      console.log(pessoa[prop][subprop]);
    }
  } else {
    console.log(pessoa[prop]);
  }
}
```

### Evite usar `for...in` com arrays
Embora funcione, **não é recomendado** usar `for...in` com arrays, porque:

- Ele percorre **índices como strings**
- Pode acessar **propriedades extras adicionadas ao array**
- A ordem dos índices **não é garantida**

Use `for...of`, `forEach`, `map`, etc. com arrays.


## While

O `while` é um laço de repetição que executa um bloco de código **enquanto uma condição for verdadeira**.

### Sintaxe
A **condição é verificada antes** de executar o bloco.
Se for **falsa já no início**, o código **não será executado nenhuma vez**.

```javascript
while (condição) {
  // código a ser executado
}
```

### Exemplo

```javascript
let entrada = prompt("Digite um número entre 1 e 10");

while (isNaN(entrada) || Number(entrada) < 1 || Number(entrada) > 10) {
  entrada = prompt("Entrada inválida. Digite um número entre 1 e 10.");
}

alert("Você digitou um número válido!");
```

Neste exemplo:
- `isNaN()` verifica se a entrada **não é um número**.
- `Number()` converte a string digitada em número.
- O loop repete até o usuário digitar um número **entre 1 e 10**.

## Do While

O `do...while` é parecido com o `while`, mas com uma **diferença importante**: Ele **sempre executa o bloco pelo menos uma vez**, **antes** de verificar a condição.

### Sintaxe:

```javascript
do {
  // código a ser executado
} while (condição);
```

### Exmplo

```javascript
let entrada;

do {
  entrada = prompt("Digite um número entre 1 e 10");
} while (Number(entrada) < 1 || Number(entrada) > 10);

alert("Você digitou um número válido!");
```

- Mesmo que a condição fosse falsa logo no começo, o `prompt` seria exibido **pelo menos uma vez**.
- O loop só para quando o número estiver dentro do intervalo válido.

## ForEach:
O `forEach` é um método disponível em todos os objetos do tipo array em JavaScript. Sua finalidade é percorrer cada elemento de um array e aplicar uma função de retorno de chamada a cada um deles. Isso permite que você realize ações específicas em cada elemento do array sem a necessidade de criar um loop manualmente.

### Sintaxe

```javascript
array.forEach(function(element, index, array) {
    // Código a ser executado para cada elemento
});
```

- `array`: É o array que você deseja percorrer.
- `element`: Representa o elemento atual do array em cada iteração.
- `index`: É o índice (posição) do elemento atual no array.
- `array`: É o próprio array que está sendo percorrido.

### Exemplo

```javascript
const frutas = ['maçã', 'banana', 'laranja', 'morango'];

frutas.forEach(function(fruta, index) {
    console.log(`A fruta no índice ${index} é ${fruta}`);
});
```

Neste exemplo, o `forEach` percorre o array `frutas`, e a função de retorno de chamada é executada para cada elemento. Ela imprime uma mensagem informando a fruta e o índice correspondente no array.

## Break

O `break` é usado para **interromper um loop imediatamente**, ou seja, **sair do loop antes de ele terminar naturalmente**.

### Exemplo
- Quando `i === 5`, o `break` **encerra o loop**.   
- Muito útil para **parar a busca** por um valor quando ele é encontrado.
```javascript
for (let i = 0; i < 10; i++) {
  if (i === 5) {
    break;
  }
  console.log(i);
}
```


    

---

### ⏭️ **O que é o `continue`?**

O `continue` **não encerra o loop**, mas **pula a iteração atual** e segue para a próxima.

#### ✅ Exemplo:

```javascript
for (let i = 0; i < 10; i++) {
  if (i === 5) {
    continue;
  }
  console.log(i);
}
```

**Saída:**

```
0  
1  
2  
3  
4  
6  
7  
8  
9
```

- Quando `i === 5`, o `console.log(i)` **não é executado**.
    
- O loop continua com o próximo valor (`i = 6`).
    

---

### 🏷️ **E se houver loops aninhados?** (rótulos com `break` e `continue`)

Em loops dentro de loops, você pode usar **rótulos (labels)** para controlar qual loop deseja afetar com o `break` ou `continue`.

#### ✅ Exemplo com `break` usando rótulo:

```javascript
outerLoop: for (let i = 0; i < 3; i++) {
  for (let j = 0; j < 3; j++) {
    if (i === 1 && j === 1) {
      break outerLoop;
    }
    console.log(`i: ${i}, j: ${j}`);
  }
}
```

**Saída:**

```
i: 0, j: 0  
i: 0, j: 1  
i: 0, j: 2  
i: 1, j: 0
```

- Quando `i === 1` e `j === 1`, o `break outerLoop` **interrompe o loop externo inteiro**.
    
- Sem o rótulo, o `break` só encerraria o loop interno.
    

---

### 📌 **Resumo das Diferenças**

|Comando|O que faz|Quando usar|
|---|---|---|
|`break`|Sai imediatamente do loop|Quando você encontrou o que procurava ou quer parar tudo|
|`continue`|Pula para a próxima iteração|Quando quer **ignorar apenas uma repetição**|
|`break` com rótulo|Sai de um loop **específico** (em aninhados)|Para sair do loop de fora|

---

### ✅ **Conclusão**

- Use `**break**` para **interromper totalmente** um loop com base em uma condição.
    
- Use `**continue**` para **pular uma repetição** e seguir com o restante.
    
- Labels são úteis em **loops aninhados**, mas raramente necessários em códigos simples.
    
- Saber usar esses comandos ajuda a ter **mais controle sobre o fluxo dos seus loops**.