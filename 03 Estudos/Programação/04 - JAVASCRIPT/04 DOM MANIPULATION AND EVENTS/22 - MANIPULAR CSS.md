## O que são `Element.style` e `Element.classList`?
Essas são duas formas de manipular estilos de elementos HTML diretamente no JavaScript:

- **`Element.style`**: Permite alterar estilos **inline** (diretamente no atributo `style` do elemento HTML).

- **`Element.classList`**: Permite gerenciar classes CSS de um elemento, adicionando, removendo ou alternando classes, o que afeta os estilos definidos no CSS.

Ambas são úteis para criar páginas web dinâmicas, como mostrar/esconder menus ou destacar elementos com base em interações do usuário.

## 1. Usando `Element.style`

A propriedade **`Element.style`** é usada para **ler ou definir estilos inline** de um elemento HTML. Estilos inline são aqueles aplicados diretamente no atributo `style` do elemento, como `<p style="color: red;">`.

### Como funciona?
- Você acessa o elemento HTML com métodos como `document.getElementById()` ou `document.querySelector()`.
- Usa `element.style.propriedade` para definir ou modificar um estilo CSS.
- As propriedades CSS são escritas em **camelCase** no JavaScript (ex.: `background-color` vira `backgroundColor`).

### Exemplo
**HTML**:
```html
<p id="para">Este é um parágrafo</p>
```

**JavaScript**:
```javascript
const paraEl = document.getElementById("para");
paraEl.style.color = "red";
paraEl.style.backgroundColor = "yellow";
paraEl.style.fontSize = "20px";
```

**Resultado no HTML**:
```html
<p id="para" style="color: red; background-color: yellow; font-size: 20px;">Este é um parágrafo</p>
```

- **O que aconteceu?** O JavaScript adicionou os estilos diretamente no atributo `style` do elemento `<p>`, mudando a cor do texto para vermelho, o fundo para amarelo e o tamanho da fonte para 20px.

- **Propriedades suportadas**: Você pode usar qualquer propriedade CSS, como `color`, `backgroundColor`, `fontWeight`, `display`, etc.

### Quando usar?
- Quando você precisa alterar estilos específicos de forma direta e pontual.

- Exemplo: Alterar a cor de um elemento ao clicar em um botão ou ajustar a posição de um elemento dinamicamente.

### Limitação
- O `Element.style` só modifica estilos inline, não afetando estilos definidos em arquivos CSS externos ou internos.

- Pode tornar o HTML mais "poluído" se muitos estilos forem aplicados diretamente.

## 2. Usando `Element.classList`

A propriedade **`Element.classList`** permite gerenciar as **classes CSS** de um elemento. Em vez de manipular estilos diretamente, você adiciona, remove ou alterna classes que já estão definidas no CSS, mantendo a separação entre lógica (JavaScript) e apresentação (CSS).

### Métodos principais do `classList`
- **`classList.add("classe")`**: Adiciona uma ou mais classes ao elemento.
- **`classList.remove("classe")`**: Remove uma ou mais classes do elemento.
- **`classList.toggle("classe")`**: Adiciona a classe se ela não estiver presente, ou remove se estiver.

#### Exemplo 1: Adicionando uma classe
**HTML**:
```html
<p id="para">Este é um parágrafo</p>
```

**CSS**:
```css
.highlight {
  background-color: yellow;
}
```

**JavaScript**:
```javascript
const paraEl = document.getElementById("para");
paraEl.classList.add("highlight");
```

**Resultado no HTML**:
```html
<p id="para" class="highlight">Este é um parágrafo</p>
```

**O que aconteceu?** A classe `highlight` foi adicionada ao elemento, aplicando o estilo de fundo amarelo definido no CSS.

Você também pode adicionar múltiplas classes de uma vez:
```javascript
paraEl.classList.add("classe1", "classe2", "classe3");
```

#### Exemplo 2: Removendo uma classe
```javascript
paraEl.classList.remove("highlight");
```

**Resultado**: A classe `highlight` é removida, e o fundo amarelo desaparece.

#### Exemplo 3: Alternando uma classe (toggle)
Um caso comum é mostrar/esconder um menu ao clicar em um botão.

**HTML**:
```html
<button id="toggle-btn">Alternar Menu</button>
<nav id="menu" class="menu">
  <ul>
    <li>Home</li>
    <li>Sobre</li>
    <li>Produtos</li>
  </ul>
</nav>
```

**CSS**:
```css
.menu {
  display: none;
  background-color: lightgray;
  width: 50%;
  padding: 10px;
}

.menu.show {
  display: block;
}
```

**JavaScript**:
```javascript
const menu = document.getElementById("menu");
const toggleBtn = document.getElementById("toggle-btn");

toggleBtn.addEventListener("click", () => {
  menu.classList.toggle("show");
});
```

- **O que aconteceu?**
  - Ao clicar no botão, a classe `show` é adicionada ao elemento `<nav>` se não estiver presente, fazendo o menu aparecer (`display: block`).
  - Se a classe `show` já estiver presente, ela é removida, escondendo o menu (`display: none`).
    
- **Resultado**: O menu alterna entre visível e invisível a cada clique no botão.

## Diferenças entre `Element.style` e `Element.classList`
| **Aspecto**              | **`Element.style`**                              | **`Element.classList`**                          |
|--------------------------|--------------------------------------------------|--------------------------------------------------|
| **O que faz?**           | Altera estilos inline diretamente no elemento.   | Gerencia classes CSS, aplicando estilos do CSS.   |
| **Exemplo**              | `element.style.color = "red"`                   | `element.classList.add("highlight")`             |
| **Separação de código**  | Mistura estilos com JavaScript.                 | Mantém estilos no CSS, promovendo separação.     |
| **Flexibilidade**        | Ideal para mudanças pontuais e dinâmicas.        | Ideal para aplicar múltiplos estilos via classes.|
| **Manutenção**           | Pode ser difícil gerenciar muitos estilos inline.| Mais fácil de manter, pois estilos ficam no CSS. |

## Por que usar `classList` é geralmente melhor?

- **Separação de responsabilidades**: Mantém os estilos no CSS, deixando o JavaScript focado na lógica.
  
- **Manutenção mais fácil**: Alterar estilos no CSS é mais simples do que modificar código JavaScript.
  
- **Reutilização**: Uma classe CSS pode ser aplicada a vários elementos, enquanto estilos inline precisam ser definidos individualmente.

No entanto, `Element.style` é útil para mudanças dinâmicas e específicas, como ajustar a posição de um elemento com base em cálculos.

## Quando usar cada um?

- **Use `Element.style`**:
  - Para mudanças pontuais, como ajustar `width`, `color` ou `position` dinamicamente.
  - Exemplo: Mover um elemento com `element.style.left = "100px"`.

- **Use `Element.classList`**:
  - Para aplicar ou remover estilos complexos definidos no CSS.
  - Exemplo: Mostrar/esconder um menu ou destacar elementos com classes predefinidas.

## Resumo
- **`Element.style`**:
  - Modifica estilos inline diretamente no elemento (ex.: `element.style.color = "red"`).
  - Ideal para mudanças específicas e dinâmicas, mas pode "poluir" o HTML.
    
- **`Element.classList`**:
  - Gerencia classes CSS com métodos como `add()`, `remove()` e `toggle()`.
  - Mantém estilos no CSS, promovendo melhor organização e manutenção.
    
- **Exemplo prático**: Use `style` para mudar a cor de um texto diretamente; use `classList` para mostrar/esconder um menu com uma classe CSS.
  
- **Boa prática**: Prefira `classList` para estilos complexos ou reutilizáveis, reservando `style` para ajustes pontuais.