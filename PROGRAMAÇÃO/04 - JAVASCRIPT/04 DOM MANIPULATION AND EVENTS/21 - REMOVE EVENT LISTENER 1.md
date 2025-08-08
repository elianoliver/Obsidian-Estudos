O método **`removeEventListener()`** é usado para **remover um ouvinte de evento** que foi previamente adicionado a um elemento HTML com o método `addEventListener()`. Ele é útil quando você deseja que um elemento pare de responder a um evento específico, como um clique ou um movimento do mouse.

## Sintaxe básica

A sintaxe do `removeEventListener()` é:
```javascript
elemento.removeEventListener("evento", ouvinte);
```

- **elemento**: O elemento HTML do qual você quer remover o ouvinte (ex.: um botão, um parágrafo, etc.).
  
- **evento**: O tipo de evento que você quer parar de escutar (ex.: `"click"`, `"mouseover"`, etc.).
  
- **ouvinte**: A função que foi usada no `addEventListener()` para lidar com o evento. **Importante**: Deve ser a mesma referência da função original, ou seja, não pode ser uma função anônima nova.

## Argumentos opcionais

Além dos dois argumentos principais, o `removeEventListener()` aceita um terceiro argumento opcional:

- **`options`**: Um objeto que especifica configurações do ouvinte, como `{ passive: true }` ou `{ once: true }`.

- **`useCapture`**: Um valor booleano (`true` ou `false`) que indica se o evento foi configurado para usar a fase de captura durante a propagação do evento.

Na maioria dos casos, você só precisará usar os dois primeiros argumentos (`evento` e `ouvinte`).

## Como funciona?

1. **Adicione um ouvinte com `addEventListener()`**: Primeiro, você associa uma função a um evento de um elemento.

2. **Remova o ouvinte com `removeEventListener()`**: Quando você não quer mais que o elemento responda a esse evento, use `removeEventListener()` com os mesmos argumentos (evento e função) usados no `addEventListener()`.

## Exemplo prático

Vamos usar o exemplo fornecido para ilustrar:

#### HTML
```html
<h1>Exemplos de Event Listener</h1>
<p id="para">Passe o mouse aqui para remover o ouvinte de evento</p>
<button id="btn">Mudar cor de fundo</button>
```

#### CSS
```css
body {
  background-color: grey;
}
```

#### JavaScript
Queremos que o botão mude a cor de fundo da página entre cinza e azul quando clicado, mas, ao passar o mouse sobre o parágrafo, o ouvinte do botão deve ser removido.

1. **Selecionar os elementos**:
```javascript
const bodyEl = document.querySelector("body");
const para = document.getElementById("para");
const btn = document.getElementById("btn");
```

2. **Criar a função para alternar cores**:
```javascript
let isBgColorGrey = true;

function toggleBgColor() {
   bodyEl.style.backgroundColor = isBgColorGrey ? "blue" : "grey";
   isBgColorGrey = !isBgColorGrey;
}
```
   
   - A variável `isBgColorGrey` rastreia a cor atual.
   - A função `toggleBgColor` alterna a cor de fundo entre cinza e azul.

3. **Adicionar o ouvinte ao botão**: Quando o botão é clicado, a função `toggleBgColor` é chamada, mudando a cor de fundo.
```javascript
btn.addEventListener("click", toggleBgColor);
```

4. **Remover o ouvinte ao passar o mouse no parágrafo**: Quando o mouse passa sobre o parágrafo, o ouvinte de clique do botão é removido. Depois disso, clicar no botão não mudará mais a cor de fundo.
```javascript
para.addEventListener("mouseover", () => {
   btn.removeEventListener("click", toggleBgColor);
});
```

## Por que isso funciona?

- O `removeEventListener()` só remove o ouvinte se a função passada for **exatamente a mesma** usada no `addEventListener()`. Por isso, usamos a função nomeada `toggleBgColor` em vez de uma função anônima, pois funções anônimas criam novas referências e não podem ser removidas diretamente.

## Cuidados ao usar `removeEventListener()`

- **Função deve ser a mesma**: Se você usou uma função anônima no `addEventListener()`, não poderá removê-la com `removeEventListener()`, pois não terá a referência exata da função.

- **Argumentos devem coincidir**: O evento (ex.: `"click"`) e a função devem ser idênticos aos usados no `addEventListener()`. Se você usou `{ capture: true }` ao adicionar, deve usar o mesmo ao remover.

## Exemplos do mundo real

- **Fechar um modal**: Quando um modal (janela pop-up) é fechado, você pode remover os ouvintes de eventos associados a ele para evitar consumo desnecessário de memória.

- **Logout de usuário**: Ao fazer logout, você pode remover ouvintes de eventos de botões ou formulários para garantir que eles não sejam acionados após o usuário sair.

## Resumo

- **O que faz?** O `removeEventListener()` remove um ouvinte de evento previamente adicionado com `addEventListener()`.

- **Sintaxe**: `elemento.removeEventListener("evento", função)`.

- **Quando usar?** Quando você quer que um elemento pare de responder a um evento, como após fechar um modal ou logout.

- **Cuidados**: Use a mesma função e argumentos do `addEventListener()`. Funções anônimas não podem ser removidas diretamente.

- **Exemplo prático**: Remover um ouvinte de clique de um botão quando o mouse passa sobre outro elemento.
