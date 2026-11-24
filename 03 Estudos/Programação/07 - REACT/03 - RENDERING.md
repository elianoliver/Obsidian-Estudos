Renderizar significa **exibir algo na tela**. No React, é o processo que transforma seu **código (JS, JSX e CSS)** em uma **interface visível no navegador**.

## **Etapas da renderização**

O React divide a renderização em **3 fases principais**:

### Trigger (Disparo)

- Ocorre quando algo muda: geralmente o **state** ou as **props**.
- Isso **dispara** a necessidade de atualizar a interface.

```jsx
<button onClick={() => setCount(count + 1)}>Increment</button>
```

Quando você clica no botão, muda o estado → isso **dispara** o processo de renderização.

### Render (Renderização Virtual)

- O React **recalcula** como o componente **deveria ser exibido**.
- Ele faz isso usando o **Virtual DOM** (uma cópia leve da DOM real).
- Compara o "antes" e "depois" para decidir o que mudou.

Analogia: Você está **cozinhando o prato** antes de servir.

### Commit (Aplicação na Tela)

- O React **compara** o Virtual DOM com o DOM real.
- Atualiza **somente o que mudou**, evitando recarregar tudo.
- O usuário finalmente **vê a mudança na tela**.

Analogia: Agora que a comida está pronta, você **serve o prato**.

## Exemplo completo: Contador

```jsx
function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <h1>{count}</h1>
      <button onClick={() => setCount(count - 1)}>Decrement</button>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
}
```

- Clicou no botão → **Trigger**
- React recalcula o JSX com o novo count → **Render**
- O novo número aparece no `<h1>` → **Commit**

## Por que React é rápido?

- **Evita alterar o DOM diretamente.**
- Usa o **Virtual DOM** para calcular só o que mudou.
- Isso melhora a **performance** e deixa a interface mais fluida.

## Conclusão

- **Renderizar** é transformar o código em interface visual.
    
- Acontece em **3 fases**: _Trigger → Render → Commit_.
    
- O uso do Virtual DOM torna a atualização **rápida e eficiente**.
    
- Cada vez que um estado muda, o React cuida do resto — de forma inteligente.