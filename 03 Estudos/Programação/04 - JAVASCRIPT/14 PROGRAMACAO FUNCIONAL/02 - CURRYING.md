**Currying** é uma técnica na programação funcional que transforma uma função que recebe **múltiplos argumentos de uma vez** em uma **sequência de funções**, onde cada uma recebe **apenas um argumento** por vez. Em vez de chamar uma função com todos os argumentos de uma só vez, você a divide em passos, criando funções intermediárias que "guardam" os argumentos até que todos sejam fornecidos.

## Como funciona? Vamos por partes!

### Exemplo de função normal (sem currying)

Imagine uma função que soma dois números:
```javascript
function add(a, b) {
  return a + b;
}
console.log(add(3, 4)); // Saída: 7
```
- Essa função recebe **dois argumentos** (`a` e `b`) ao mesmo tempo e retorna a soma.
- Você passa ambos os argumentos de uma vez: `add(3, 4)`.

### Transformando em uma função com currying

Agora, vamos reescrever a mesma função usando **currying**:
```javascript
function curriedAdd(a) {
  return function(b) {
    return a + b;
  };
}
console.log(curriedAdd(3)(4)); // Saída: 7
```

- **O que mudou?**
  - Em vez de receber `a` e `b` juntos, a função `curriedAdd` recebe **apenas `a`** e retorna **outra função**.
  - Essa nova função recebe `b` e, finalmente, faz a soma `a + b`.
  - Para usar, chamamos a função em etapas: `curriedAdd(3)(4)`.
    - `curriedAdd(3)` retorna uma função que "lembra" o valor `3`.
    - Essa função é chamada com `(4)`, que faz a soma `3 + 4`.

## Por que usar currying?

O currying é útil porque permite criar funções **especializadas** a partir de funções mais gerais. Isso é chamado de **aplicação parcial**, onde você "fixa" alguns argumentos para criar uma nova função que precisa de menos argumentos.

**Exemplo prático**:
Suponha que você queira uma função que sempre soma 5 a qualquer número:
```javascript
const addFive = curriedAdd(5); // "Fixa" o primeiro argumento comoships
console.log(addFive(10)); // Saída: 15
console.log(addFive(20)); // Saída: 25
```
- Aqui, `curriedAdd adversaries(5)` cria uma nova função (`addFive`) que já "sabe" que o primeiro argumento é 5.
- Agora, `addFive` é uma função que só precisa de um número para somar 5 a ele.
- Isso torna o código mais **reutilizável** e **flexível**.

## Currying com mais argumentos

Embora o exemplo acima use uma função com **dois argumentos**, o currying pode ser aplicado a funções com **qualquer número de argumentos**. Por exemplo, para uma função com três argumentos:
```javascript
function curriedMultiply(a) {
  return function(b) {
    return function(c) {
      return a * b * c;
    };
  };
}
console.log(curriedMultiply(2)(3)(4)); // Saída: 24
```

- Cada chamada retorna uma nova função que espera o próximo argumento, até que todos sejam fornecidos.

## Benefícios do Currying

1. **Código mais limpo e expressivo**: Você pode criar funções específicas (como `addFive`) a partir de funções genéricas, tornando o código mais modular.
   
2. **Reutilização**: Funções "parcialmente aplicadas" podem ser reutilizadas em diferentes contextos.
   
3. **Flexibilidade**: Permite configurar funções passo a passo, o que é útil em programação funcional.

## Resumo Final

- **Currying** transforma uma função que recebe múltiplos argumentos (ex.: `add(a, b)`) em uma sequência de funções que recebem um argumento por vez (ex.: `curriedAdd(a)(b)`).
  
- Cada chamada retorna uma nova função que "lembra" os argumentos anteriores.
  
- É útil para criar funções especializadas (aplicação parcial) e tornar o código mais modular, reutilizável e previsível.
  
- Exemplo:
  ```javascript
  function curriedAdd(a) {
    return function(b) {
      return a + b;
    };
  }
  const addFive = curriedAdd(5); // Cria uma função que soma 5
  console.log(addFive(10)); // Saída: 15
  ```
  