O **hook `useActionState`** é uma novidade do **React 19** que simplifica o gerenciamento de estado em ações de formulários ou eventos que utilizam **server actions**. Ele foi projetado para trabalhar com **server actions**, que são funções executadas no servidor (sem a necessidade de APIs tradicionais) para lidar com dados de formulários ou outras ações.

**Para que serve?**
- Gerencia o **estado** retornado por uma server action.
- Controla o **estado de carregamento** (`isPending`) de uma ação.
- Pode ser usado com **formulários** ou outros eventos, como cliques em botões.

**Importante**: Como é um hook, o `useActionState` **não pode ser usado em server components**, apenas em **client components** (marcados com `"use client"`).

## Sintaxe do `useActionState`

```javascript
const [state, action, isPending] = useActionState(actionFunction, initialState, permalink);
```

- **`state`**: O estado atual retornado pela server action 
  (ex.: `{ message: "Hello, John!" }`).
  
- **`action`**: A função que dispara a server action 
  (ex.: `submitForm`).
  
- **`isPending`**: Um booleano que indica se a ação está em andamento (`true`) ou não (`false`).
  
- **`actionFunction`**: A server action que será executada (definida com `"use server"`).
  
- **`initialState`**: O estado inicial antes que a ação seja executada (ex.: `{ message: "" }`).
  
- **`permalink`** (opcional): Uma string com a URL única da página que o formulário modifica.

## Como funciona? Exemplo com formulário

#### 1. Definindo a server action

Primeiro, você precisa de uma **server action**, que é uma função marcada com `"use server"`. Exemplo:

```javascript
"use server";

export async function submitForm(_, formData) {
  const name = formData.get("name");
  const hour = new Date().getHours();
  let greeting = hour < 12 ? "Good morning" : hour < 18 ? "Good afternoon" : "Good evening";
  return { message: `${greeting}, ${name}` };
}
```

- Essa função extrai o campo `name` de um formulário e retorna uma saudação baseada na hora do dia.

#### 2. Usando `useActionState` no componente

No componente, importe o `useActionState` e a server action, e use o hook para gerenciar o estado:

```javascript
"use client";

import { useActionState } from "react";
import { submitForm } from "./actions/submitForm";

function Greeter() {
  const [state, submit, isPending] = useActionState(submitForm, { message: "" });

  return (
    <div className="flex flex-col items-center justify-center min-h-screen bg-gray-100 p-6">
      <form action={submit} className="bg-white p-6 rounded-2xl shadow-md w-full max-w-md">
        <h2 className="text-2xl text-center font-semibold text-gray-700 mb-4">
          Greet Someone
        </h2>
        <input
          type="text"
          name="name"
          placeholder="Enter your name"
          required
          className="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-green-400"
        />
        <button
          type="submit"
          disabled={isPending}
          className="w-full mt-4 p-3 bg-green-500 text-white font-semibold rounded-lg hover:bg-green-600 disabled:bg-gray-400 transition-all"
        >
          {isPending ? "Greeting..." : "Greet"}
        </button>
        {state.message && (
          <p className="mt-4 text-green-600 text-center font-medium">{state.message}</p>
        )}
      </form>
    </div>
  );
}

export default Greeter;
```

**Explicação**:
- O hook `useActionState` é inicializado com a função `submitForm` e um estado inicial `{ message: "" }`.
  
- O formulário usa o atributo `action={submit}` para disparar a server action.
  
- **`isPending`** é usado para desabilitar o botão e mostrar "Greeting..." enquanto a ação está em andamento.
  
- O estado `state.message` exibe a mensagem retornada (ex.: "Good morning, John").

**No navegador**:
- O usuário digita um nome, clica em "Greet", e o botão muda para "Greeting..." durante o processamento.
- A mensagem final aparece com base na hora do dia (ex.: "Good afternoon, Maria").

## Usando `useActionState` fora de formulários

O `useActionState` também pode ser usado com eventos como cliques em botões. Exemplo: buscar usuários de uma API.

#### 1. Definindo a server action

```javascript
"use server";

export async function getUsers() {
  const res = await fetch("https://jsonplaceholder.typicode.com/users?_start=0&_limit=5/");
  return await res.json();
}
```

#### 2. Usando `useActionState` com um botão

```javascript
"use client";

import { useActionState, startTransition } from "react";
import { getUsers } from "./actions/getUsers";

export default function FetchUsers() {
  const [users, fetchAction, isPending] = useActionState(getUsers, []);

  return (
    <div className="p-6 max-w-lg mx-auto">
      <button
        onClick={() => startTransition(() => fetchAction())}
        disabled={isPending}
        className="px-4 py-2 bg-green-500 text-white rounded-lg hover:bg-green-600 disabled:bg-gray-400 font-bold"
      >
        {isPending ? "Fetching Users..." : "Fetch Users"}
      </button>
      <ul className="mt-4 space-y-2">
        {users.map((user) => (
          <li key={user.id} className="p-3 bg-gray-100 rounded-lg">
            <p className="font-semibold">{user.name}</p>
            <p className="text-sm text-gray-600">{user.email}</p>
          </li>
        ))}
      </ul>
    </div>
  );
}
```

**Explicação**:
- A server action `getUsers` busca 5 usuários de uma API.
  
- O hook `useActionState` gerencia a lista de usuários (`users`) e o estado `isPending`.
  
- O evento `onClick` usa `startTransition` para envolver `fetchAction`, garantindo que a UI permaneça responsiva durante a busca assíncrona.
  
- **Por que `startTransition`?**
  
  - Sem ele, o estado `isPending` pode não atualizar corretamente devido à prioridade de renderização do React.
    
  - `startTransition` marca a atualização como de baixa prioridade, permitindo que a UI permaneça fluida.

**No navegador**:
- O botão muda de "Fetch Users" para "Fetching Users..." durante o carregamento.
  
- Após a busca, a lista de usuários é exibida.

## Resumo das principais ideias:

1. **O que é `useActionState`?**
   - Um hook do React 19 que gerencia estado e ações para **server actions**, simplificando formulários e eventos.
   - Retorna `[state, action, isPending]` para controlar o estado, disparar a ação e indicar carregamento.

2. **Como funciona?**
   - Use com **formulários** (via atributo `action`) ou **eventos** (ex.: cliques em botões).
   - Integra com server actions, que são funções marcadas com `"use server"`.
   - Para ações assíncronas fora de formulários, use `startTransition` para garantir responsividade.

3. **Quando usar?**
   - Para formulários que enviam dados ao servidor sem APIs tradicionais.
   - Para eventos como cliques que disparam server actions (ex.: buscar dados).
   - Apenas em **client components** (`"use client"`).

4. **Boas práticas**:
   - Use `isPending` para desabilitar botões e mostrar estados de carregamento.
   - Envolva ações assíncronas com `startTransition` para evitar problemas de renderização.
   - Mantenha o estado inicial claro e consistente com o retorno da server action.

## Dica final para iniciantes:

- Use o `useActionState` para formulários simples ou ações que interagem com o servidor, aproveitando a integração com server actions.
- Teste com formulários pequenos antes de aplicá-lo em fluxos complexos.
- Se precisar de mais controle, combine com outros hooks como `useState` ou `useEffect`.
