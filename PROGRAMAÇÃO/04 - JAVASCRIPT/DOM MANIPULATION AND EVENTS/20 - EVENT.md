O **Event object** (objeto de evento) é um objeto em JavaScript que é criado automaticamente quando um usuário interage com uma página web. Essa interação pode ser:

- Clicar em um botão.
- Digitar algo em um campo de texto.
- Focar em um elemento de formulário.
- Até mesmo ações mais específicas, como agitar um dispositivo móvel.

Esse objeto contém informações sobre a interação que aconteceu, como **quem** disparou o evento, **que tipo** de evento foi e **detalhes específicos** sobre a ação.

## Como o Event object funciona?

Quando um evento ocorre (como um clique ou tecla pressionada), o JavaScript gera um **Event object** que é passado para a função que "escuta" esse evento (geralmente definida com `addEventListener()`). Esse objeto é como uma "caixa" cheia de informações úteis sobre o evento.

## Propriedades principais do Event object

O **Event object** tem várias propriedades, mas as mais comuns e presentes em todos os eventos são:

1. **`type`**:
   - Indica o tipo de evento que ocorreu, como `"click"`, `"keydown"`, `"submit"`, etc.
   - Esse valor corresponde ao tipo de evento que você especifica no `addEventListener()`.
   - Exemplo: Se o usuário clicar em um botão, `event.type` será `"click"`.

2. **`target`**:
   - Aponta para o elemento que disparou o evento.
   - Normalmente, é um elemento HTML (como um `<button>` ou `<input>`), mas pode ser algo como o objeto `Document` ou `Window`.
   - Exemplo: Se você clicar em um botão, `event.target` retorna o próprio botão.

## Métodos úteis do Event object

Além das propriedades, o **Event object** tem métodos (funções) que você pode chamar para controlar o comportamento do evento. Os mais comuns são:

1. **`preventDefault()`**:
   - Impede o comportamento padrão do evento.
   - Exemplo: Em um formulário, chamar `event.preventDefault()` evita que o navegador envie os dados do formulário como uma requisição POST padrão, permitindo que você lide com os dados manualmente.

2. **`stopPropagation()`**:
   - Impede que o evento "suba" (ou se propague) para elementos pais no DOM.
   - Isso é útil quando você quer que o evento seja tratado apenas pelo elemento clicado, sem afetar outros elementos que poderiam "ouvir" o mesmo evento.

## Propriedades específicas

Alguns eventos têm propriedades exclusivas, dependendo do tipo de evento. 

Por exemplo:
- Um evento do tipo `FetchEvent` (relacionado a requisições web) tem uma propriedade `request` que contém detalhes da requisição.
- Um evento de teclado (`keydown`) pode ter propriedades como `key` ou `code` para indicar qual tecla foi pressionada.

Se você não souber quais propriedades estão disponíveis, pode:
- Usar `console.log(event)` para inspecionar o objeto no console do navegador.
- Consultar a documentação oficial do JavaScript (como o MDN Web Docs).

## Exemplos práticos

1. **Capturando um clique em um botão**:
   ```javascript
   const botao = document.querySelector("#meu-botao");
   botao.addEventListener("click", function(event) {
       console.log(event.type); // "click"
       console.log(event.target); // Referência ao botão clicado
   });
   ```

2. **Impedindo o envio de um formulário**:
   ```javascript
   const formulario = document.querySelector("#meu-form");
   formulario.addEventListener("submit", function(event) {
       event.preventDefault(); // Impede o envio padrão do formulário
       console.log("Formulário não foi enviado ao servidor!");
   });
   ```

3. **Parando a propagação de um evento**:
   ```javascript
   const divFilha = document.querySelector(".filha");
   divFilha.addEventListener("click", function(event) {
       event.stopPropagation(); // Impede que o evento afete a div pai
       console.log("Clicou na div filha!");
   });
   ```

## Quando usar o Event object?

Você usa o **Event object** sempre que precisa:
- Saber **qual elemento** foi clicado ou interagido.
  
- Obter detalhes sobre a interação, como **qual tecla** foi pressionada ou **onde** o mouse clicou.
  
- Controlar o comportamento padrão, como evitar que um formulário seja enviado ou que um link redirecione a página.
  
- Criar interações dinâmicas, como validar formulários, manipular cliques ou responder a ações do usuário.

## Resumo

- **O que é?** Um objeto que contém informações sobre interações do usuário com a página (cliques, teclas, etc.).
  
- **Propriedades principais**: `type` (tipo do evento) e `target` (elemento que disparou o evento).
  
- **Métodos úteis**: `preventDefault()` (impede comportamento padrão) e `stopPropagation()` (impede propagação do evento).
  
- **Exemplos reais**: Evitar envio de formulários, capturar cliques em botões ou manipular eventos específicos como teclas ou requisições.
  
- **Dica**: Use `console.log(event)` ou consulte a documentação para explorar as propriedades disponíveis.

