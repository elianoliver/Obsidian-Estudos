## **1. O que é memoização no React?**

Memoização é uma técnica de otimização que evita cálculos ou renderizações desnecessárias, armazenando resultados ou referências para reutilização. No React, ela é usada para melhorar a performance, evitando re-renderizações de componentes ou recriações de funções quando não há mudanças relevantes.

- **useCallback**: Memoiza **funções**, garantindo que a mesma referência da função seja mantida entre renderizações, desde que suas dependências não mudem.
- **React.memo**: Memoiza **componentes**, evitando que eles sejam re-renderizados se suas props não mudarem.

## **2. O Hook useCallback**

<mark style="background: #BBFABBA6;">O `useCallback` é usado para memoizar funções</mark>, ou seja, evitar que uma função seja recriada a cada renderização do componente. Isso é **importante** porque, no React, funções são recriadas em cada render, o que pode causar problemas de performance, especialmente quando essas funções são passadas como props ou usadas em dependências de outros hooks, como o `useEffect`.

#### **Sintaxe básica do useCallback**:
```javascript
const minhaFuncao = useCallback(() => {
  // Código da função
}, [dependencias]);
```
- A função dentro do `useCallback` só é recriada se uma das **dependências** (listadas no array) mudar.
- Sem o `useCallback`, a função é recriada em cada render, mesmo que seu comportamento não mude.

#### **Exemplo prático do useCallback**:

No exemplo do componente `Counter`, temos uma função `handleClick` que incrementa um contador. Sem o `useCallback`, ela é recriada a cada render, o que faz com que o `useEffect` (que depende dela) seja executado repetidamente, mesmo sem necessidade.

```javascript
import { useState, useEffect, useCallback } from "react";

function Counter() {
  const [count, setCount] = useState(0);

  // Sem useCallback, handleClick é recriada a cada render
  const handleClick = () => {
    setCount((prevCount) => prevCount + 1);
  };

  useEffect(() => {
    console.log("useEffect runs");
  }, [handleClick]); // handleClick muda a cada render, então o useEffect roda sempre

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={handleClick}>Increment</button>
    </div>
  );
}
```

**Solução com useCallback**:
```javascript
const handleClick = useCallback(() => {
  setCount((prevCount) => prevCount + 1);
}, []); // Array vazio: a função não depende de nenhuma variável, então não é recriada
```

Agora, `handleClick` mantém a mesma referência entre renders, e o `useEffect` só roda na montagem do componente, evitando execuções desnecessárias.

## **3. O React.memo**

O `React.memo` é uma função de ordem superior (HOC) que <mark style="background: #BBFABBA6;">memoiza um componente</mark>, impedindo que ele seja re-renderizado se suas **props** não mudarem. Isso é útil para componentes que recebem props idênticas em renderizações consecutivas, mas que são re-renderizados desnecessariamente devido a mudanças no componente pai.

#### **Sintaxe básica do React.memo**:
```javascript
const MeuComponente = React.memo(({ prop }) => {
  return (
    <div>
      {/* JSX do componente */}
    </div>
  );
});
```
- O `React.memo` faz uma comparação rasa (shallow comparison) das props. Se as props forem iguais, o componente não re-renderiza.

### **Exemplo prático do React.memo**:

No exemplo, o componente `CounterChild` é um filho do componente `Counter`. O componente pai (`Counter`) re-renderiza a cada segundo devido a um estado `timer` que atualiza o horário. Isso faz com que o `CounterChild` também seja re-renderizado, mesmo que sua prop `onClick` não mude.

```javascript
const CounterChild = ({ onClick }) => {
  console.log("CounterChild component rendered");
  return <button onClick={onClick}>Increment from Child</button>;
};
```

**Solução com React.memo**:
```javascript
import React from "react";

const CounterChild = React.memo(({ onClick }) => {
  console.log("CounterChild component rendered");
  return <button onClick={onClick}>Increment from Child</button>;
});
```

Agora, o `CounterChild` só será re-renderizado se a prop `onClick` mudar. Mas há um problema: se a função `onClick` (passada do componente pai) for recriada a cada render, o `React.memo` não conseguirá evitar a re-renderização, porque a prop `onClick` terá uma nova referência.

## **4. Como useCallback e React.memo trabalham juntos?**

> [!attention]
> O `React.memo` depende de props estáveis para funcionar corretamente. Se uma prop for uma função (como `onClick`), ela precisa ser memoizada com `useCallback` para manter a mesma referência entre renders. Caso contrário, mesmo com `React.memo`, o componente filho será re-renderizado desnecessariamente.
> 


### **Exemplo combinado**:

No código abaixo, o componente `Counter` tem um estado `timer` que atualiza a cada segundo, causando re-renderizações frequentes. A função `handleClick` é passada como prop para o `CounterChild`. Sem `useCallback`, `handleClick` é recriada a cada render, fazendo com que o `CounterChild` (mesmo com `React.memo`) seja re-renderizado.

```javascript
import { useState, useEffect, useCallback } from "react";
import CounterChild from "./CounterChild";

function Counter() {
  const [count, setCount] = useState(0);
  const [timer, setTimer] = useState(new Date().toLocaleTimeString());

  // Sem useCallback, handleClick é recriada a cada render
  const handleClick = () => {
    setCount((prevCount) => prevCount + 1);
  };

  useEffect(() => {
    const interval = setInterval(() => {
      setTimer(new Date().toLocaleTimeString());
    }, 1000);
    return () => clearInterval(interval);
  }, []);

  return (
    <div>
      <h1>Time: {timer}</h1>
      <p>Count: {count}</p>
      <button onClick={handleClick}>Increment</button>
      <CounterChild onClick={handleClick} />
    </div>
  );
}
```

**Solução com useCallback e React.memo**:
```javascript
const handleClick = useCallback(() => {
  setCount((prevCount) => prevCount + 1);
}, []); // Array vazio: handleClick não depende de variáveis
```

E no `CounterChild`:
```javascript
import React from "react";

const CounterChild = React.memo(({ onClick }) => {
  console.log("CounterChild component rendered");
  return <button onClick={onClick}>Increment from Child</button>;
});
```

Agora:
- O `useCallback` garante que `handleClick` mantenha a mesma referência entre renders.

- O `React.memo` impede que o `CounterChild` seja re-renderizado a cada atualização do `timer`, já que a prop `onClick` não muda.

## **5. Quando usar useCallback e React.memo?**

- **useCallback**: Use quando uma função é passada como prop para um componente memoizado ou é usada como dependência de hooks como `useEffect`. Isso evita recriações desnecessárias da função.

- **React.memo**: Use em componentes que recebem props que não mudam frequentemente, para evitar re-renderizações desnecessárias quando o componente pai re-renderiza.

#### **Cuidados**:
- **Não exagere no uso**: Memoizar tudo pode aumentar a complexidade do código e o uso de memória, sem ganhos significativos de performance.

- **Dependências corretas no useCallback**: Certifique-se de listar todas as dependências necessárias no array de dependências do `useCallback`. No exemplo, usamos `[]` porque `handleClick` não depende de nenhuma variável. Se dependesse, por exemplo, do `count`, o array deveria ser `[count]`.

## **6. Resumo final**

- **useCallback**: Memoiza <mark style="background: #BBFABBA6;">funções</mark> para manter a mesma referência entre renders, útil para evitar execuções desnecessárias de `useEffect` ou re-renderizações de componentes filhos.

- **React.memo**: Memoiza <mark style="background: #BBFABBA6;">componentes</mark> para evitar re-renderizações quando as props não mudam.

- **Juntos**: O `useCallback` estabiliza funções passadas como props, permitindo que o `React.memo` funcione corretamente, evitando re-renderizações desnecessárias.

Com esses conceitos, você pode otimizar a performance de aplicações React, especialmente em cenários onde componentes ou funções são recriados frequentemente sem necessidade.
