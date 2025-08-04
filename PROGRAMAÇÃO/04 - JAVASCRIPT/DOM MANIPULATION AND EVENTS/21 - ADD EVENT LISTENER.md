**Eventos** são ações ou interações que acontecem em uma página web, geralmente desencadeadas pelo usuário. Exemplos incluem:

- Clicar em um botão.
- Digitar em um campo de texto.
- Mover o mouse sobre um elemento.
- Enviar um formulário.

Esses eventos são como "sinais" que a página envia para o JavaScript, permitindo que você execute ações em resposta a essas interações.

## O que é o `addEventListener()`?

O método **`addEventListener()`** é usado para "escutar" esses eventos e executar um código quando eles ocorrem. Ele é aplicado a um elemento HTML e define o que deve acontecer quando um evento específico é disparado.

## Sintaxe básica

A sintaxe do `addEventListener()` é:
```javascript
elemento.addEventListener("evento", ouvinte);
```

- **elemento**: O elemento HTML que você quer monitorar (ex.: um botão, um input, etc.).
  
- **evento**: O tipo de evento que você quer escutar, como `"click"`, `"input"`, `"mouseover"`, etc.
  
- **ouvinte**: Geralmente uma função que será executada quando o evento ocorrer. Essa função pode ser definida diretamente ou referenciada por um nome.

## Como funciona?

1. **Selecione o elemento**: Use métodos como `document.getElementById()` ou `document.querySelector()` para acessar o elemento HTML que você quer monitorar.
   
2. **Adicione o ouvinte**: Use `addEventListener()` para especificar o evento e a função que será chamada quando ele ocorrer.

## Exemplos práticos

### 1. Escutando um evento de clique

Imagine que você tem o seguinte HTML:
```html
<button id="btn">Mostrar alerta</button>
```

Para mostrar um alerta quando o botão for clicado, você pode usar:
```javascript
// Seleciona o botão
const btn = document.getElementById("btn");

// Adiciona um ouvinte para o evento "click"
btn.addEventListener("click", () => {
    alert("Você clicou no botão!");
});
```

**Resultado**: Toda vez que o botão for clicado, uma mensagem de alerta com o texto "Você clicou no botão!" será exibida.

Você também pode definir a função separadamente para maior clareza:
```javascript
function mostrarAlerta() {
    alert("Você clicou no botão!");
}

const btn = document.getElementById("btn");
btn.addEventListener("click", mostrarAlerta);
```

### 2. Escutando um evento de input

Agora, suponha que você tenha um campo de texto:
```html
<input type="text" id="input" placeholder="Digite algo" />
```

Para registrar no console o que o usuário digita, use o evento `"input"`:
```javascript
// Seleciona o campo de texto
const input = document.getElementById("input");

// Adiciona um ouvinte para o evento "input"
input.addEventListener("input", () => {
    console.log(input.value);
});
```

**Resultado no console** (se o usuário digitar "hello"):
```
h
he
hel
hell
hello
```

Cada vez que o usuário digita algo, o valor do campo é exibido no console.

## Outros tipos de eventos

Além de `"click"` e `"input"`, existem muitos outros eventos que você pode escutar com o `addEventListener()`. Alguns exemplos comuns:

- **`mouseover`**: Quando o mouse passa por cima de um elemento.
- **`mouseout`**: Quando o mouse sai de um elemento.
- **`keydown`**: Quando uma tecla é pressionada.
- **`keyup`**: Quando uma tecla é solta.
- **`submit`**: Quando um formulário é enviado.

### Interface EventListener (opcional)

Em casos mais avançados, o ouvinte pode ser um **objeto** que implementa a interface `EventListener`. Essa interface exige um método chamado `handleEvent()`, que será chamado automaticamente quando o evento ocorrer. Exemplo:
```javascript
const meuObjeto = {
    handleEvent() {
        alert("Evento disparado!");
    }
};

const btn = document.getElementById("btn");
btn.addEventListener("click", meuObjeto);
```

Na prática, isso é raramente usado, e uma função simples é suficiente na maioria dos casos.

## Por que usar `addEventListener()`?

- **Flexibilidade**: Permite adicionar múltiplos ouvintes para o mesmo elemento.

- **Organização**: Funções separadas tornam o código mais fácil de ler e manter.

- **Interatividade**: Possibilita criar páginas dinâmicas que respondem às ações do usuário.

## Resumo

- **Eventos**: São interações do usuário, como cliques, digitação ou envio de formulários.

- **addEventListener()**: Método que "escuta" eventos em um elemento HTML e executa uma função quando o evento ocorre.

- **Sintaxe**: `elemento.addEventListener("evento", função)`.

- **Exemplos práticos**: Mostrar alertas em cliques de botões ou capturar o que o usuário digita em um campo.

- **Outros eventos**: Incluem `mouseover`, `keydown`, `submit`, entre outros.

- **Dica**: Use funções separadas para manter o código organizado e fácil de manter.