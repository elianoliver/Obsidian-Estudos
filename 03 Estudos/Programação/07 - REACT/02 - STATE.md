O **state** (ou estado) em React é como a **memória de curto prazo** de um componente. Ele guarda informações que **podem mudar com o tempo** — como o valor de um input, o número de cliques, ou dados vindos de uma API — e **controla o que aparece na tela** com base nesses dados.

Sempre que o state muda, o React **re-renderiza automaticamente o componente**, atualizando a interface **sem recarregar a página**.

## Como usar o state com o hook `useState`

O `useState` é um **hook** do React que permite usar estado em **componentes funcionais**.

### Importação

```jsx
import { useState } from "react";
// ou
import React from "react"; // depois: React.useState(...)
```

### Sintaxe básica

```jsx
const [valorAtual, funçãoAtualizadora] = useState(valorInicial);
```

- `valorAtual`: o valor atual do estado.
- `funçãoAtualizadora`: função usada para **atualizar o estado**.
- `valorInicial`: valor que o estado terá no início (ex: `0`, `""`, `{}`).
    
### Exemplo prático: contador

```jsx
import { useState } from "react";

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <h2>{count}</h2>
      <button onClick={() => setCount(count - 1)}>Decrementar</button>
      <button onClick={() => setCount(count + 1)}>Incrementar</button>
    </div>
  );
}
```

Nesse exemplo:
- `count` é o valor atual do contador.
- `setCount` atualiza esse valor.
- O componente se re-renderiza automaticamente quando o estado muda.

## Cada componente tem seu próprio estado

Se você renderizar o mesmo componente duas vezes, cada um terá **um state independente**. O estado **não é compartilhado** automaticamente entre componentes.

Se quiser compartilhar, você precisa:

1. **"Subir o estado"** para um componente pai.
2. Passar os dados por **props**.

## Regras importantes sobre hooks:

1. Sempre chame `useState` no topo do componente.
2. Nunca dentro de loops, condicionais ou funções aninhadas.  
    Isso evita comportamentos imprevisíveis.

### Vários estados no mesmo componente

Você pode ter vários `useState`:

```jsx
function UserProfile() {
  const [isOnline, setIsOnline] = useState(false);
  const [notifications, setNotifications] = useState(0);
}
```

Ou agrupar em um objeto, útil em formulários:

```jsx
function SignUpForm() {
  const [formData, setFormData] = useState({
    name: "",
    username: "",
    email: "",
  });
}
```

## Conclusão

- `state` controla dados que mudam no tempo e afetam a UI.
    
- `useState` é a forma de declarar e atualizar esses dados.
    
- Alterar o state re-renderiza o componente.
    
- Você pode ter múltiplos estados ou agrupar tudo em um só.
    
- Respeite as regras dos hooks para evitar bugs.