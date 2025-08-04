Uma **função callback** é uma função que você passa como argumento para outra função. Essa função callback só será executada quando a função principal terminar sua tarefa. 

```ad-note
É como dizer: "Faça isso primeiro, e quando terminar, execute essa outra função que eu te passei."
```

Pense em um exemplo do dia a dia:
- Você vai a um restaurante e faz um pedido (a função principal).
  
- Enquanto o pedido está sendo preparado, você dá uma instrução ao garçom: "Quando o prato estiver pronto, me avise" (essa instrução é a função callback).
  
- O garçom só te avisa (executa a callback) quando o prato estiver pronto.

Em JavaScript, callbacks são muito usadas para garantir que certas ações aconteçam na ordem certa, especialmente em operações que podem demorar, como loops ou requisições a servidores. Elas tornam o código mais **flexível** e **modular**.

## O que é o método forEach?

O **forEach** é um método disponível em arrays em JavaScript. Ele permite que você percorra (itere) cada elemento de um array e execute uma ação para cada um desses elementos. A ação que você quer executar é definida em uma **função callback** que você passa para o `forEach`.

Em vez de usar um loop tradicional (como `for` ou `while`), o `forEach` simplifica o processo, cuidando do loop para você. Você só precisa dizer o que fazer com cada elemento do array.

## Como o forEach usa uma função callback?

Quando você usa o `forEach`, você passa uma função callback como argumento. Essa função callback será chamada automaticamente para cada elemento do array, na ordem em que os elementos aparecem.

### Exemplo simples
Imagine que você tem um array de números e quer dobrar cada número:

```javascript
let numbers = [1, 2, 3, 4, 5];

numbers.forEach(function(number) {
  console.log(number * 2);
});
```

**O que acontece aqui?**
- O array `numbers` contém `[1, 2, 3, 4, 5]`.
- O método `forEach` percorre cada elemento do array.
- Para cada elemento, ele chama a função callback.
- A variável `number` recebe o valor do elemento atual a cada iteração.

A função callback é executada **uma vez para cada elemento** do array, e o `forEach` gerencia o loop internamente.

### Usando arrow functions
Você pode simplificar a escrita da função callback usando uma **arrow function** (função de seta), que é mais curta:

```javascript
let numbers = [1, 2, 3, 4, 5];

numbers.forEach(number => console.log(number * 2));
```

O resultado é o mesmo (imprime `2, 4, 6, 8, 10`), mas a sintaxe é mais concisa. A arrow function é apenas uma forma alternativa de escrever a função callback.

### Mais argumentos da função callback
A função callback do `forEach` pode receber até **três argumentos**:
1. **Elemento atual** (obrigatório): O elemento do array que está sendo processado.
2. **Índice** (opcional): A posição do elemento no array (começa em 0).
3. **Array original** (opcional): O array que está sendo percorrido.

Exemplo usando todos os argumentos:

```javascript
let numbers = [1, 2, 3, 4, 5];

numbers.forEach((number, index, array) => {
  console.log(`Elemento ${number} está no índice ${index} do array [${array}]`);
});
```

Aqui, a função callback usa:
- `number`: o valor do elemento atual.
- `index`: a posição do elemento no array.
- `array`: o array completo, caso você precise acessá-lo.

## Por que isso é importante?

Entender funções callback e o método `forEach` é essencial porque:
- **Callbacks** são a base para muitos conceitos avançados em JavaScript, como programação assíncrona (ex.: lidar com requisições a servidores ou timers).
  
- O `forEach` é uma maneira simples e limpa de iterar sobre arrays, sendo muito usado em aplicações modernas.
  
- Muitos outros métodos de array, como `map`, `filter` e `reduce`, também usam funções callback de forma semelhante.

## Resumo dos principais pontos

1. **Função callback**: Uma função passada como argumento para outra função, que será executada quando a função principal terminar.
   
2. **forEach**: Um método de arrays que executa uma função callback para cada elemento do array, na ordem.
   
3. **Função callback no forEach**:
   - Recebe até três argumentos: `elemento`, `índice` e `array`.
   - Define o que fazer com cada elemento do array.
     
## Exemplo prático completo

```javascript
let students = ['Ana', 'Bruno', 'Clara'];

students.forEach((student, index) => {
  console.log(`Estudante ${index + 1}: ${student}`);
});
```

- O `forEach` percorre o array `students`.
  
- A função callback `(student, index) => { ... }` é chamada para cada elemento.
  
- Para cada estudante, imprimimos seu nome e posição (índice + 1 para começar do 1).