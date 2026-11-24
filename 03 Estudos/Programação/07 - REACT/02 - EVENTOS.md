Eventos são ações do usuário (como cliques, envio de formulários, digitação) que disparam respostas no sistema. No React, esses eventos são tratados por um sistema chamado **Synthetic Event**, que **padroniza o comportamento de eventos em todos os navegadores**.

## **Diferenças entre HTML e React no uso de eventos**

| HTML tradicional                       | React                                      |
| -------------------------------------- | ------------------------------------------ |
| `<button onclick="...">`               | `<button onClick={...}>`                   |
| Usa strings                            | Usa funções                                |
| Atributos em minúsculo (ex: `onclick`) | Atributos em **camelCase** (ex: `onClick`) |

## Como criar e usar um manipulador de evento (event handler)

```jsx
function handleClick() {
  console.log("Botão clicado!");
}

<button onClick={handleClick}>Clique aqui</button>
```

- **Sem parênteses** → Você está passando a **referência da função**, não executando ela.
    
- Convenção: nomes como `handleClick`, `handleSubmit`, etc.

## O que é o Synthetic Event?

É um objeto passado automaticamente para seu manipulador de eventos. Ele tem propriedades semelhantes ao `Event` do JavaScript puro:

```jsx
function handleClick(event) {
  console.log(event.type); // ex: "click"
}
```

## Métodos úteis do evento

- `event.preventDefault()` → Impede comportamento padrão (ex: não recarregar a página ao enviar um formulário).
    
- `event.stopPropagation()` → Impede o evento de se propagar para elementos pais.

```jsx
function handleSubmit(event) {
  event.preventDefault();
  console.log("Formulário enviado!");
}

<form onSubmit={handleSubmit}>
  <input />
  <button>Enviar</button>
</form>
```

## Passando parâmetros para handlers

Para passar dados, use uma **arrow function**:

```jsx
function handleDelete(id) {
  console.log("Deletando item:", id);
}

<button onClick={() => handleDelete(1)}>Deletar</button>
```

## **Performance**

Diferente do HTML tradicional, **React otimiza internamente** os handlers com arrow functions, graças ao uso do Virtual DOM.

## Conclusão

- Eventos em React são **similares ao HTML**, mas usam camelCase e funções.
    
- O Synthetic Event torna o comportamento consistente entre navegadores.
    
- Você pode manipular o evento, prevenir ações padrão, parar propagação e até passar dados extras sem medo de prejudicar a performance.