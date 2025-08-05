## O que é **Event Bubbling** (Propagação de Eventos)?

**Event bubbling** é o processo pelo qual um evento disparado em um elemento HTML "sobe" (ou se propaga) para seus elementos **pais** na estrutura do DOM (Document Object Model). Em outras palavras, quando um evento ocorre em um elemento, ele primeiro é processado nesse elemento (o **alvo** do evento) e depois "borbulha" para os elementos superiores na hierarquia, permitindo que eles também respondam ao mesmo evento.

### Como funciona?

- Imagine a seguinte estrutura HTML:
```html
<p>
	<span>Clique aqui!</span>
</p>
```

Aqui, o elemento `<span>` é um **filho** do elemento `<p>`. Se você clicar no `<span>`, o evento de clique (`click`) será disparado primeiro no `<span>` (o **alvo** do evento) e depois se propagará para o `<p>` (o **pai**).

- **Exemplo prático**:
  ```javascript
  const p = document.querySelector("p");
  p.addEventListener("click", (event) => {
    console.log(event.target); // Exibe o elemento <span> clicado
  });
  ```

Ao clicar no `<span>`, o evento de clique "burbulha" até o `<p>`, e o ouvinte (listener) no `<p>` é acionado.
  
O `event.target` indica o elemento que **originou** o evento (neste caso, o `<span>`), mesmo que o ouvinte esteja no `<p>`.

### Ordem de propagação:

- O evento é processado **primeiro** no elemento mais interno (`<span>`).

- Depois, ele sobe para os elementos pais (como o `<p>`), até chegar ao elemento raiz do DOM (geralmente o `document` ou `window`), a menos que a propagação seja interrompida.

### Interrompendo a propagação:

- Você pode usar o método `event.stopPropagation()` para impedir que o evento continue subindo para os elementos pais. Exemplo:
    ```javascript
    const span = document.querySelector("span");
    span.addEventListener("click", (event) => {
      console.log("Span clicado!");
      event.stopPropagation(); // Impede que o evento alcance o <p>
    });
    ```

Nesse caso, o ouvinte no `<p>` **não** será acionado, porque a propagação foi interrompida no `<span>`.

### Por que isso é importante?

O **event bubbling** permite que você capture eventos em elementos pais, mesmo que o evento tenha sido disparado em um elemento filho. Isso é útil para gerenciar eventos em estruturas complexas sem precisar adicionar ouvintes a cada elemento individualmente.

## O que é **Event Delegation** (Delegação de Eventos)?

**Event delegation** é uma técnica que aproveita o **event bubbling** para gerenciar eventos de múltiplos elementos filhos usando um **único ouvinte** no elemento pai. Em vez de adicionar ouvintes de eventos a cada elemento filho individualmente, você coloca o ouvinte no pai e deixa o evento "burbulhar" até ele, onde você decide como processá-lo.

### Como funciona?
- Em vez de adicionar um ouvinte de evento a cada `<span>` em uma lista, por exemplo, você adiciona um único ouvinte ao elemento pai (como o `<p>`). Quando um evento ocorre em qualquer `<span>`, ele se propaga até o `<p>`, e o ouvinte no `<p>` pode identificar qual elemento filho foi clicado usando `event.target`.

- **Exemplo prático**:
  ```html
  <p>
    <span>Clique aqui!</span>
    <span>Clique aqui!</span>
    <span>Clique aqui!</span>
  </p>
  ```
  ```javascript
  const p = document.querySelector("p");
  p.addEventListener("click", (event) => {
    if (event.target.tagName === "SPAN") {
      event.target.style.color = "red"; // Muda a cor do <span> clicado
    }
  });
  ```

Aqui, o ouvinte está no `<p>`, mas ele detecta cliques em qualquer `<span>` filho e altera a cor apenas do `<span>` clicado (usando `event.target`).

### Benefícios da delegação de eventos:

1. **Eficiência**: Você usa um único ouvinte em vez de vários, o que reduz o uso de memória e melhora a performance, especialmente em listas grandes ou dinâmicas.
   
2. **Flexibilidade com elementos dinâmicos**: Se novos elementos `<span>` forem adicionados ao `<p>` dinamicamente (via JavaScript), o ouvinte no `<p>` ainda funcionará para esses novos elementos, sem necessidade de adicionar novos ouvintes.
   
3. **Simplicidade**: Reduz a necessidade de gerenciar múltiplos ouvintes, simplificando o código.

### Quando usar?

- Quando você tem muitos elementos filhos que precisam do mesmo comportamento (como botões em uma lista ou itens em uma tabela).
  
- Quando elementos são adicionados ou removidos dinamicamente, e você quer evitar gerenciar ouvintes para cada um.

## Diferenças e relação entre **Event Bubbling** e **Event Delegation**

- **Event Bubbling** é o **mecanismo** pelo qual os eventos se propagam do elemento alvo para seus pais no DOM.
  
- **Event Delegation** é uma **técnica** que **usa** o bubbling para delegar o tratamento de eventos a um elemento pai, em vez de adicionar ouvintes a cada elemento filho.

**Exemplo combinado**:
```html
<p>
  <span>Clique aqui!</span>
  <span>Clique aqui!</span>
</p>
```
```javascript
const p = document.querySelector("p");
p.addEventListener("click", (event) => {
  console.log("Elemento clicado:", event.target);
  if (event.target.tagName === "SPAN") {
    event.target.style.color = "red"; // Delegação: muda a cor do <span> clicado
  }
});
```

- **Bubbling**: O clique no `<span>` se propaga até o `<p>`.
- **Delegation**: O ouvinte no `<p>` verifica se o `event.target` é um `<span>` e aplica a lógica desejada.

## Cuidados e boas práticas

1. **Verificar o `event.target`**:
   - Sempre cheque se o `event.target` é o elemento desejado (ex.: `if (event.target.tagName === "SPAN")`) para evitar ações em elementos indesejados.
     
2. **Usar `stopPropagation` com cuidado**:
   - Interromper a propagação pode quebrar outros ouvintes que dependem do bubbling. Use apenas quando necessário.
     
3. **Evitar excesso de ouvintes**:
   - A delegação de eventos é ideal para reduzir o número de ouvintes, mas certifique-se de que o ouvinte no elemento pai não está processando eventos desnecessários.

---

### Resumo final
- **Event Bubbling**: Quando um evento ocorre em um elemento, ele primeiro é processado nesse elemento e depois "sobe" para os elementos pais, permitindo que eles também respondam ao evento. Pode ser interrompido com `event.stopPropagation()`.
- **Event Delegation**: Uma técnica que usa o bubbling para gerenciar eventos de múltiplos elementos filhos com um único ouvinte no elemento pai, melhorando a eficiência e facilitando o manejo de elementos dinâmicos.
- **Por que usar?**: O bubbling é a base do funcionamento da delegação, que simplifica o código, melhora a performance e lida bem com elementos adicionados dinamicamente.

Se quiser mais exemplos práticos ou explorar cenários mais complexos (como tabelas aninhadas), é só pedir!