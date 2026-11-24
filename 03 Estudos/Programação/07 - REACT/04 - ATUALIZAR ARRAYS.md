Em React, o `state` é **imutável**, o que significa que **não podemos modificar diretamente arrays** com métodos como `push()`, `pop()` ou `splice()`.

Isso porque o React **detecta mudanças comparando referências**. Se a referência do array for a mesma, ele **não re-renderiza** o componente.

## ❌ O que NÃO fazer

```jsx
import { useState } from "react";

function ItemsList() {
  const [items, setItems] = useState([
    { id: 0, name: "Item 1" },
    { id: 1, name: "Item 2" },
    { id: 2, name: "Item 3" },
  ]);
// ============================================================================
  const addItem = () => {
    const newItem = { id: items.length + 1, name: `Item ${items.length + 1}` };
    items.push(newItem); // This modifies the original array
    setItems(items); // React will not detect this change
  };
// ============================================================================
  return (
    <div>
      <button onClick={addItem}>Add Item</button>
      <ul>
        {items.map((item) => (
          <li key={item.id}>{item.name}</li>
        ))}
      </ul>
    </div>
  );
}

export default ItemsList;
```

Mesmo que o array mude no console, **a tela não será atualizada** porque o React ainda vê a "mesma" lista (mesmo endereço na memória).

## ✅ Forma correta: criar um novo array

### Adicionar item (com spread `...`):

```jsx
setItems((prevItems) => [...prevItems, newItem]);
```

- Copia todos os itens anteriores.
- Adiciona o novo item no final.
- Gera um novo array → React detecta a mudança.
### Remover item (com `filter`):

```jsx
setItems((prevItems) => prevItems.filter(item => item.id !== id));
```

- Cria um novo array **excluindo** o item desejado.
- Evita modificar o original.

## Exemplo prático completo

```jsx
import { useState } from "react";

function ItemsList() {
  const [items, setItems] = useState([
    { id: 0, name: "Item 1" },
    { id: 1, name: "Item 2" },
    { id: 2, name: "Item 3" },
  ]);
// ============================================================================
  const addItem = () => {
    const newItem = { id: items.length + 1, name: `Item ${items.length + 1}` };
    setItems((prevItems) => [...prevItems, newItem]); // Creates a new array
  };
// ============================================================================
  const removeItem = (id) => {
    setItems((prevItems) => prevItems.filter((item) => item.id !== id)); // Creates a new array
  };
// ============================================================================
  return (
    <div>
      <button onClick={addItem}>Add Item</button>
      <ul>
        {items.map((item) => (
          <li key={item.id}>
            {item.name}{" "}
            <button onClick={() => removeItem(item.id)}>Remove</button>
          </li>
        ))}
      </ul>
    </div>
  );
}

export default ItemsList;
```

## Dica final

Evite **modificar arrays diretamente**. Sempre use métodos como:

- `map()` → para transformar itens
- `filter()` → para remover
- `concat()` ou `[...arr, novoItem]` → para adicionar
- `slice()` ou `...spread` → para copiar

## Conclusão

- React só re-renderiza quando o **array é novo**.
    
- Nunca use `push()` ou `pop()` diretamente no state.
    
- Use sempre **funções puras** que retornam **novos arrays**.