---
Livro: "[[Entendendo Algoritmos.pdf]]"
cssclasses:
  - rounded-images
tags:
  - EntendendoAlgoritmos
---
---
# Recursão
Recursão é quando uma função chama a si mesma para resolver problemas divididos em partes menores. Vamos começar com um exemplo de pseudocódigo para calcular o fatorial de um número. 

O fatorial de um número `n` (escrito como `n!`) é o produto de todos os números de `n` até 1. Por exemplo, `5! = 5 * 4 * 3 * 2 * 1`.

```pseudo
função fatorial(n):
    se n == 1:
        retorna 1
    senão:
        retorna n * fatorial(n - 1)
```

Aqui, a função `fatorial` se chama repetidamente, reduzindo o valor de `n` até que `n` seja igual a 1. Esse é o caso mais simples, conhecido como **caso base**.

# Caso base e caso recursivo
Uma função recursiva precisa de dois componentes principais para funcionar corretamente:

1. **Caso base**: A condição em que a função para de se chamar.
2. **Caso recursivo**: A parte em que a função se chama novamente para resolver uma parte menor do problema.

**Caso base**:
```pseudo
se n == 1:
    retorna 1
```
Quando `n` chega a 1, o fatorial de 1 é simplesmente 1, então a função para e retorna esse valor.

**Caso recursivo**:
```pseudo
senão:
    retorna n * fatorial(n - 1)
```
Se `n` for maior que 1, a função se chama novamente, mas com `n - 1`, até que eventualmente `n` chegue a 1.

Outro exemplo de recursão é a sequência de Fibonacci. O número de Fibonacci em uma posição `n` é a soma dos dois números anteriores na sequência.

```pseudo
função fibonacci(n):
    se n == 0:
        retorna 0
    se n == 1:
        retorna 1
    senão:
        retorna fibonacci(n - 1) + fibonacci(n - 2)
```
Aqui, os casos base são `fibonacci(0)` e `fibonacci(1)`, e o caso recursivo soma os dois valores anteriores.

# Uma pilha tem duas operações: push e pop
Uma **pilha** é uma estrutura de dados com duas operações principais: **push** (adicionar um item) e **pop** (remover um item). Ela segue o princípio "último a entrar, primeiro a sair" (LIFO). Vamos ilustrar essas operações em pseudocódigo:

```pseudo
pilha = []

função push(item):
    pilha.adiciona(item)  // Adiciona um item ao topo da pilha

função pop():
    se pilha não está vazia:
        retorna pilha.remove_ultimo()  // Remove e retorna o item do topo da pilha
    senão:
        retorna "Erro: Pilha vazia"
```

Por exemplo, se adicionarmos os números 1, 2 e 3 à pilha, o item no topo será 3. Quando fazemos um `pop`, 3 será removido, e o próximo `pop` removerá 2, e assim por diante.

# A pilha de chamada (call stack)
A **pilha de chamada** funciona como uma pilha normal, mas é usada internamente para controlar a execução das funções. 

Sempre que uma função é chamada, as informações dessa função (seus parâmetros, variáveis locais, etc.) são armazenadas na pilha de chamada. Quando a função termina, ela é removida (pop) da pilha.

Vamos considerar o exemplo da função recursiva `fatorial`:

**Chamada recursiva para `fatorial(3)`**:
```pseudo
fatorial(3):
    3 * fatorial(2)
        2 * fatorial(1)
            retorna 1 (caso base)
```
A pilha de chamada ficaria assim:

1. **Chamada**: `fatorial(3)` → A função é empilhada.
2. **Chamada**: `fatorial(2)` → A função é empilhada.
3. **Chamada**: `fatorial(1)` → A função é empilhada.
4. **Retorno**: `fatorial(1)` retorna 1 → A função é removida (pop) da pilha.
5. **Retorno**: `fatorial(2)` retorna 2 → A função é removida.
6. **Retorno**: `fatorial(3)` retorna 6 → A função é removida.

Cada chamada recursiva adiciona uma nova função à pilha de chamada, e as funções começam a ser removidas quando o caso base é alcançado.

# A pilha de chamada pode ficar muito grande e ocupar muita memória
Um problema com recursão é que, se houver muitas chamadas recursivas, a pilha de chamada pode crescer demais e ocupar muita memória, causando um **estouro de pilha** (stack overflow). Isso ocorre porque cada chamada de função ocupa um espaço na pilha, e se a recursão for muito profunda, esse espaço acaba.

Por exemplo, se tentarmos calcular o fatorial de um número muito grande sem otimizar o código, a pilha de chamada pode ficar enorme:

```pseudo
fatorial(10000)  // Isso causaria um estouro de pilha
```

Uma maneira de evitar esse problema é usando técnicas como **recursão de cauda** (tail recursion) ou substituindo a recursão por um loop. Aqui está uma versão do cálculo de fatorial usando um loop, que não usa a pilha de chamada recursiva:

```pseudo
função fatorial_iterativo(n):
    resultado = 1
    para i de 2 até n:
        resultado = resultado * i
    retorna resultado
```
Dessa forma, evitamos o crescimento da pilha de chamada, pois a função usa um loop ao invés de se chamar repetidamente.