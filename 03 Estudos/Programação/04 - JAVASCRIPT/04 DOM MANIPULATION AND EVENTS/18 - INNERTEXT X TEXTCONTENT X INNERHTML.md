As propriedades **`innerText`**, **`textContent`** e **`innerHTML`** em JavaScript são usadas para acessar ou modificar o conteúdo de elementos HTML no DOM. Apesar de parecerem semelhantes, elas têm diferenças importantes em comportamento, uso e desempenho. Vamos explorar cada uma de forma didática e compará-las.

## 1. `innerText`

- **O que é**: Representa o **texto visível** de um elemento HTML e seus descendentes, considerando apenas o texto que é renderizado na página (exclui tags HTML e texto escondido).
  
- **Características**:
  - Retorna apenas o texto visível, ignorando elementos ocultos (como com o atributo `hidden` ou `display: none`).
  - Respeita quebras de linha visíveis e formatação CSS.
  - Ao definir `innerText`, substitui todo o conteúdo do elemento por um novo texto, convertendo quebras de linha em elementos `<br>`.

### Exemplo
**Explicação**: O texto do `<p>` com `hidden` é ignorado, pois não é visível.
```html
<div id="container">
  <p>Olá, Mundo!</p>
  <p hidden>Estou aprendendo JavaScript</p>
</div>
```

```javascript
const container = document.getElementById("container");
console.log(container.innerText);
// Saída:
// Olá, Mundo!
```

### Definindo `innerText`
  ```javascript
  container.innerText = "JavaScript é incrível!";
  ```
  
**Resultado no DOM**:
  ```html
  <div id="container">JavaScript é incrível!</div>
  ```

Todo o conteúdo anterior é substituído por texto puro.

### Cuidados
- **Performance**: Acessar `innerText` pode ser mais lento, pois dispara um **reflow** (recalculo de layout) para determinar quais elementos são visíveis.

- **Uso**: Ideal quando você precisa do texto exatamente como ele aparece para o usuário.

## 2. `textContent`

- **O que é**: Retorna ou define o **texto puro** de um elemento e todos os seus descendentes, incluindo texto em elementos ocultos, scripts e estilos, sem considerar a visibilidade.

- **Características**:
  - Inclui **todo o texto**, independentemente de estar visível ou não.
  - Mantém espaços e quebras de linha do HTML original.
  - Não processa tags HTML; trata tudo como texto puro.
  - Ao definir `textContent`, substitui todos os nós filhos por um único nó de texto.

### Exemplo
**Explicação**: Inclui o texto do `<p>` oculto, pois `textContent` não considera visibilidade.
```html
<div id="container">
  <p>Olá, Mundo!</p>
  <p hidden>Estou aprendendo JavaScript</p>
</div>
```

```javascript
const container = document.getElementById("container");
console.log(container.textContent);
// Saída:
// Olá, Mundo!
// Estou aprendendo JavaScript
```


### Definindo `textContent`:
  ```javascript
  container.textContent = "JavaScript é incrível!";
  ```
  
**Resultado no DOM**:
  ```html
  <div id="container">JavaScript é incrível!</div>
  ```

Todo o conteúdo anterior é substituído por texto puro.

### Cuidados:
- **Segurança**: Mais seguro que `innerHTML`, pois não interpreta HTML, evitando injeção de código malicioso.

- **Performance**: Mais rápido que `innerText`, pois não depende de cálculos de layout (reflow).

- **Uso**: Ideal para extrair ou definir texto puro, especialmente quando você precisa de todo o conteúdo, visível ou não.

## 3. `innerHTML`

- **O que é**: Retorna ou define o **conteúdo HTML** de um elemento, incluindo tags, atributos e texto. Permite criar novos elementos no DOM a partir de uma string HTML.

- **Características**:
  - Interpreta a string como HTML, criando nós correspondentes (elementos, texto, etc.).
  - Substitui todo o conteúdo do elemento quando definido.
  - Pode ser usado para obter o HTML completo de um elemento e seus descendentes.

### Exemplo
**Explicação**: Retorna o HTML completo, incluindo tags e atributos, independentemente de visibilidade.
```html
<div id="container">
  <p>Olá, Mundo!</p>
  <p hidden>Estou aprendendo JavaScript</p>
</div>
```

```javascript
const container = document.getElementById("container");
console.log(container.innerHTML);
// Saída:
// <p>Olá, Mundo!</p>
// <p hidden>Estou aprendendo JavaScript</p>
```

### Definindo `innerHTML`:
  ```javascript
  container.innerHTML = "<ul><li>JavaScript é incrível!</li></ul>";
  ```

**Resultado no DOM**:
  ```html
  <div id="container">
    <ul>
      <li>JavaScript é incrível!</li>
    </ul>
  </div>
  ```

O conteúdo anterior é substituído por uma nova estrutura HTML.

### Cuidados:
- **Segurança**: Pode ser perigoso se a string vier de uma fonte não confiável (ex.: entrada do usuário), pois pode permitir **injeção de código** (XSS). Exemplo: `<script>alert('Hacked!')</script>`.
  
- **Solução**: Use `textContent` para texto puro ou sanitize a entrada HTML.
  
- **Uso**: Ideal para criar ou manipular estruturas HTML dinamicamente.

## Comparação entre `innerText`, `textContent` e `innerHTML`
| Propriedade     | Retorna/Define                     | Inclui Texto Oculto? | Interpreta HTML? | Performance         | Segurança                     |
|-----------------|------------------------------------|----------------------|------------------|---------------------|-------------------------------|
| **`innerText`** | Texto visível (sem tags)          | Não                  | Não              | Mais lenta (reflow) | Segura (só texto)             |
| **`textContent`**| Texto puro (com espaçamento)      | Sim                  | Não              | Mais rápida         | Segura (só texto)             |
| **`innerHTML`** | Conteúdo HTML (tags + texto)      | Sim                  | Sim              | Moderada            | Risco de XSS se não controlada |

## Quando usar cada uma?

- **`innerText`**:
  - Use quando precisar do texto **exatamente como aparece** para o usuário (ex.: copiar texto visível).
  - Exemplo: Mostrar apenas o texto visível de um elemento em uma interface.
    
- **`textContent`**:
  - Use quando quiser **todo o texto**, incluindo o de elementos ocultos, ou para inserir texto puro com segurança.
  - Exemplo: Extrair todo o conteúdo textual ou substituir texto sem risco de injeção.
    
- **`innerHTML`**:
  - Use quando precisar criar ou manipular **estruturas HTML** dinamicamente, mas apenas com conteúdo seguro.
  - Exemplo: Adicionar uma lista ou outros elementos complexos ao DOM.

## Exemplo prático combinado
```html
<div id="container">
  <p>Olá, Mundo!</p>
  <p hidden>Estou escondido!</p>
</div>
```

```javascript
const container = document.getElementById("container");

console.log(container.innerText); // "Olá, Mundo!"
console.log(container.textContent); // "Olá, Mundo!\n  Estou escondido!"
console.log(container.innerHTML); // "<p>Olá, Mundo!</p>\n  <p hidden>Estou escondido!</p>"

container.innerText = "Texto visível";
container.textContent = "Texto puro";
container.innerHTML = "<strong>Texto com HTML</strong>";
```

## Resumo
- **`innerText`**: Retorna ou define o texto visível, ignorando elementos ocultos. Mais lento devido ao reflow. Ideal para texto renderizado.
  
- **`textContent`**: Retorna ou define todo o texto puro, incluindo ocultos. Mais rápido e seguro. Ideal para manipular texto sem HTML.
  
- **`innerHTML`**: Retorna ou define o conteúdo HTML, interpretando tags. Útil para criar estruturas, mas cuidado com segurança (XSS).
  
- **Escolha com base no caso**:
  - Use `innerText` para texto visível.
  - Use `textContent` para texto puro e segurança.
  - Use `innerHTML` para manipular HTML, mas apenas com conteúdo confiável.

Essas propriedades são ferramentas poderosas para manipular o conteúdo do DOM, e entender suas diferenças é essencial para usá-las corretamente!