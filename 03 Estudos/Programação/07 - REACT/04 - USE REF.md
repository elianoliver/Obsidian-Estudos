React _não foi feito_ pra mexer direto no DOM. Ele prefere que você controle tudo via **estado (`useState`) e props**.  
Mas... **tem situações que não dá pra evitar** o acesso direto ao DOM. Ex:

- Dar foco em um input
- Rolar a página até uma seção
- Medir altura/largura de um elemento
- Pausar, tocar ou manipular um vídeo
- Controlar um canvas, animações, bibliotecas externas (ex: Chart.js, Mapbox)

O `ref` é a forma **segura e oficial** de acessar um **elemento real do DOM** dentro do React.

> Em JavaScript puro, usamos `getElementById()` ou `querySelector()`.  
> Em React, usamos **refs**, geralmente criadas com o hook `useRef()`.

## Como criar e usar um ref

### Importe o `useRef`
```jsx
import { useRef } from "react";
```
### Crie a referência (inicialmente `null`)
```jsx
const inputRef = useRef(null);
```
### Atribua o ref ao elemento JSX com o atributo `ref`
```jsx
<input ref={inputRef} type="text" />
```
### Acesse o elemento com `ref.current`
```jsx
inputRef.current.focus(); // exemplo de uso
```

## Exemplo prático: foco ao clicar em um botão

```jsx
import { useRef } from "react";

const Focus = () => {
  const inputRef = useRef(null);

  const handleFocus = () => {
    if (inputRef.current) {
      inputRef.current.focus();
    }
  };

  return (
    <div>
      <input ref={inputRef} type="text" placeholder="Digite algo" />
      <button onClick={handleFocus}>Focar no input</button>
    </div>
  );
};
```

## Ciclo de vida do ref

- Inicialmente: `ref.current === null`
- Após montagem do componente: `ref.current` é o elemento DOM.
- Após desmontagem: volta a ser `null`.

## Boas práticas com refs

Use refs para:
- Acessar/manipular elementos DOM.
- Guardar valores mutáveis que **não causam re-render**.
    
Evite usar refs para gerenciar estado -> Use `useState` quando a mudança deve atualizar a interface.

Sempre verifique se `ref.current` existe antes de acessar suas propriedades
```jsx
if (ref.current) {
  // seguro usar ref.current
}
```

## Conclusão

- `useRef()` cria uma referência reutilizável.
    
- `ref.current` guarda o valor (geralmente o elemento DOM).
    
- Ideal para interações diretas com o DOM sem causar re-renderizações.