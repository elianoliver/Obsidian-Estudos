## O que são componentes?

Componentes são **as partes fundamentais de uma aplicação React**. Eles permitem **dividir a interface** em pedaços menores, facilitando o desenvolvimento, a leitura e a manutenção de projetos grandes.

## Tipos de Componentes

- **Componentes funcionais**: hoje em dia, são os mais usados.
    
- **Componentes de classe**: mais antigos e menos comuns em projetos modernos.
    
## Como funcionam?

Um componente React é como uma **função JavaScript que retorna JSX** — uma forma especial de escrever HTML dentro do JavaScript.

```jsx
function Greeting() {
  const name = "John";
  return <h1 className="title">Hello {name}</h1>;
}
```

- A função retorna um **elemento JSX**, que será renderizado na tela.
    
- As **chaves `{}`** permitem inserir expressões JavaScript no meio do HTML.
    
- Usamos `className` em vez de `class` porque `class` é uma palavra reservada em JavaScript.

## Nomes com letra maiúscula

- Componentes **devem começar com letra maiúscula**.
    
- `<Greeting />` → é um **componente personalizado**.
    
- `<div>` → é um **elemento HTML comum**.
    
React usa essa diferença para saber **o que é HTML** e **o que é um componente seu**.

## **Como usar um componente**

Basta usar o nome dele como uma tag JSX:

```jsx
<Greeting />
```

- Atenção: **todo componente precisa ser fechado corretamente**, como `<Greeting />`.

## **Vários elementos no retorno**

Não podemos retornar **vários elementos JSX soltos**:

```jsx
return <h1>Hello</h1>
       <p>Nice to meet you</p> // ❌ Isso gera erro
```

O erro acontece porque o JSX exige **um único elemento pai**.

## **Soluções**

1. **Usar uma `<div>` ou outra tag como contêiner**:
    

```jsx
return (
  <div>
    <h1>Hello</h1>
    <p>Nice to meet you.</p>
  </div>
);
```

2. **Usar um Fragment**:

```jsx
import { Fragment } from 'react';

return (
  <Fragment>
    <h1>Hello</h1>
    <p>Nice to meet you.</p>
  </Fragment>
);
```

3. **Usar a forma curta (`<> </>`)**:
    
```jsx
return (
  <>
    <h1>Hello</h1>
    <p>Nice to meet you.</p>
  </>
);
```

## Conclusão

Componentes em React são **funções reutilizáveis que retornam UI com JSX**. Eles permitem criar interfaces complexas a partir de pedaços simples. Com boa organização, tornam os projetos mais limpos, escaláveis e fáceis de manter.

```ad-info
Nos próximos passos, você aprenderá mais sobre como trabalhar com estado, eventos e comunicação entre componentes.
```
