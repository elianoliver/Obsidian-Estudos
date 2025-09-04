## O que é Memoization?

**Memoization** é uma técnica de otimização usada em programação para melhorar o desempenho de aplicações. Ela funciona armazenando (ou "cacheando") os resultados de funções custosas (que consomem muitos recursos ou tempo) com base nos argumentos fornecidos. Quando a mesma função é chamada novamente com os mesmos argumentos, o resultado armazenado é retornado, evitando recalcular tudo do zero.

### Como funciona o processo de memoization?

1. **Armazenar resultados**: Quando uma função é executada, o resultado é salvo junto com os argumentos usados.
   
2. **Verificar o cache**: Antes de executar a função novamente, verifica-se se o resultado para aqueles argumentos já está no cache.
   
3. **Retornar do cache**: Se o resultado existe no cache, ele é retornado imediatamente, sem executar a função.
   
4. **Calcular e armazenar**: Se o resultado não está no cache, a função é executada, o resultado é salvo no cache e então retornado.

Essa técnica é especialmente útil em aplicações React, onde re-renderizações desnecessárias ou cálculos pesados podem tornar a interface lenta.

### Por que Memoization é importante no React?

No React, quando um componente é renderizado, todas as funções e cálculos dentro dele são executados novamente, mesmo que os dados não tenham mudado. Isso pode ser um problema em aplicações grandes com:
- Listas extensas.
- Funções que realizam cálculos complexos.
- Muitos componentes filhos dependentes de um componente pai.

Para evitar cálculos redundantes e melhorar a performance, o React oferece ferramentas de memoization, como:
- **`React.memo`**: Um componente de ordem superior (HOC) que evita re-renderizações desnecessárias de componentes.
- **`useMemo`**: Um hook que memoiza valores computados.
- **`useCallback`**: Um hook que memoiza referências a funções.

Neste resumo, vamos focar no **useMemo**.

## O que é o Hook useMemo?

O **useMemo** é um hook do React que permite memoizar **valores computados** (resultados de funções) para evitar que cálculos caros sejam refeitos desnecessariamente durante re-renderizações. Ele é usado quando você quer garantir que um valor seja recalculado apenas quando suas dependências mudam.

#### Sintaxe básica do useMemo:
```javascript
const memoizedValue = useMemo(() => {
  return computeExpensiveValue(a, b);
}, [a, b]);
```

- **Primeiro argumento**: Uma função que realiza o cálculo e retorna o valor que você quer memoizar.
- **Segundo argumento**: Um array de dependências (`[a, b]`). O cálculo só será refeito se alguma das dependências mudar.

Quando as dependências não mudam, o `useMemo` retorna o valor armazenado no cache, evitando reexecutar a função.

### Exemplo Prático: Calculando o Quadrado de um Número

Vamos analisar o exemplo do texto para entender como o `useMemo` resolve problemas de performance.

#### Código sem useMemo
No exemplo fornecido, temos um componente chamado `ExpensiveSquare` que calcula o quadrado de um número (`num`):

```javascript
function ExpensiveSquare({ num }) {
  function calculateSquare(n) {
    console.log("Calculating square...");
    return n * n;
  }

  const squared = calculateSquare(num);
  return (
    <p>
      Square of {num}: {squared}
    </p>
  );
}
```

Este componente é usado em um componente pai (`App`):

```javascript
import { useState, useEffect } from "react";
import ExpensiveSquare from "./components/ExpensiveSquare";

function App() {
  const [timer, setTimer] = useState(0);
  const [num, setNum] = useState(0);

  useEffect(() => {
    const interval = setInterval(() => setTimer((c) => c + 1), 1000);
    return () => clearInterval(interval);
  }, []);

  return (
    <div>
      <h1>Timer: {timer} seconds gone</h1>
      <ExpensiveSquare num={num} />
      <button onClick={() => setNum((n) => n + 1)}>Increase Number</button>
    </div>
  );
}
```

Aqui, o componente `App` tem:
- Um estado `timer` que incrementa a cada segundo (usando `useEffect`).
- Um estado `num` que só muda quando o usuário clica no botão "Increase Number".
- O componente `ExpensiveSquare` que calcula o quadrado de `num`.

**Problema**: Toda vez que o `timer` muda (a cada segundo), o componente `App` re-renderiza, o que faz com que `ExpensiveSquare` também seja re-renderizado. Isso significa que a função `calculateSquare` é chamada novamente, mesmo que `num` não tenha mudado. Isso é ineficiente, especialmente se `calculateSquare` fosse uma função mais complexa.

---

#### Solução com useMemo

Para evitar recalcular o quadrado desnecessariamente, podemos usar o `useMemo` no componente `ExpensiveSquare`:

```javascript
import { useMemo } from "react";

function ExpensiveSquare({ num }) {
  function calculateSquare(n) {
    console.log("Calculating square...");
    return n * n;
  }

  const squared = useMemo(() => calculateSquare(num), [num]);

  return (
    <p>
      Square of {num}: {squared}
    </p>
  );
}
```

**O que mudou?**
- A chamada da função `calculateSquare(num)` foi envolvida pelo `useMemo`.
- O array de dependências `[num]` indica que o valor memoizado (`squared`) só será recalculado se `num` mudar.
- Quando o `timer` muda e o componente `App` re-renderiza, o `useMemo` verifica que `num` não mudou e retorna o valor armazenado no cache, evitando chamar `calculateSquare` novamente.

**Resultado**:
- O cálculo do quadrado só acontece:
  - Na renderização inicial.
  - Quando `num` muda (ao clicar no botão "Increase Number").
- A mensagem `"Calculating square..."` não aparece mais a cada segundo, apenas quando necessário.

## Benefícios do useMemo

1. **Melhora de performance**: Evita cálculos desnecessários, especialmente em funções complexas ou com grandes conjuntos de dados.
2. **Interface mais fluida**: Reduz o tempo de renderização, tornando a aplicação mais responsiva.
3. **Controle preciso**: O array de dependências permite definir exatamente quando o valor deve ser recalculado.

## Diferença entre useMemo e useCallback

Embora o texto mencione que o `useCallback` será abordado em outra aula, é útil entender a diferença básica:
- **`useMemo`**: Memoiza **valores computados** (o resultado de uma função).
- **`useCallback`**: Memoiza **referências a funções** (o próprio objeto da função em memória).

Por exemplo:
- `useMemo(() => computeExpensiveValue(a, b), [a, b])` armazena o **resultado** de `computeExpensiveValue`.
- `useCallback(() => doSomething(a, b), [a, b])` armazena a **própria função** `doSomething`.

## Resumo Final

- **Memoization** é uma técnica que armazena resultados de funções custosas para evitar recalculá-los desnecessariamente.
- No React, o **useMemo** é um hook que memoiza valores computados, recalculando-os apenas quando as dependências mudam.
- Ele é útil para otimizar componentes que realizam cálculos pesados ou que são re-renderizados frequentemente.
- No exemplo, o `useMemo` evitou recalcular o quadrado de um número a cada segundo, executando o cálculo apenas quando `num` mudava.