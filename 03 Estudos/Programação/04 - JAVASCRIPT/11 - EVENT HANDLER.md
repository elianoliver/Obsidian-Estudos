Event Handlers, em programação, são mecanismos que permitem que você "ouça" e responda a eventos ou ações que ocorrem em um programa ou aplicação. Esses eventos podem variar de interações do usuário, como cliques de mouse e pressionamentos de teclas, a eventos internos do sistema, como notificações e temporizadores.

## Sumário
- [[#Event Handler Inline]]
- [[#Event Handler Nv1]]
- [[#Event Handler Nv2]]
- [[#preventDefault()]]

## Event Handler Inline
Event Handler Inline é uma técnica de manipulação de eventos em JavaScript na qual os atributos de eventos são incluídos diretamente nos elementos HTML. Isso significa que os eventos, como `onclick`, `onmouseover`, `onkeydown`, entre outros, são definidos como atributos dentro das tags HTML. Quando o evento ocorre, o código JavaScript associado a esses atributos é executado.

A sintaxe básica de Event Handler Inline é a seguinte:

```html
<button onclick="testarClique()">Clique-me</button>
```

Neste exemplo, o atributo `onclick` é incorporado ao botão HTML e, quando o botão é clicado, a função `testarClique()` é chamada.

**Exemplo de Uso:**

Aqui está um exemplo de Event Handler Inline usado em um elemento HTML:

```javascript
function testarClique() {
	alert("MÁ PRÁTICA: Clicou em clique me!!!");
}
```

Neste caso, quando o botão é clicado, uma caixa de diálogo de alerta é exibida com a mensagem "MÁ PRÁTICA: Clicou em clique me!!!".

**Vantagens do Event Handler Inline:**
1. **Simplicidade:** É uma técnica simples e direta para atribuir comportamento a elementos HTML.

**Desvantagens do Event Handler Inline:**
1. **Má Prática:** É geralmente considerada uma má prática de programação, pois mistura o código JavaScript diretamente no HTML, tornando-o menos legível e mais difícil de manter.
2. **Poluição do HTML:** Incluir atributos de eventos inline no HTML pode poluir o código HTML e dificultar a compreensão do conteúdo da página.
3. **Escopo Limitado:** O escopo das variáveis e funções definidas no Event Handler Inline é limitado ao elemento específico que os contém, o que pode levar a problemas de reutilização de código.

## Event Handler Nv1
O Event Handler de Nível 1 é uma técnica de manipulação de eventos em JavaScript que envolve a atribuição direta de manipuladores de eventos a elementos HTML usando propriedades específicas, como `onclick`, `ondblclick` e `onmouseover`. Essas propriedades são usadas para definir funções que serão executadas quando o evento associado ocorrer no elemento HTML alvo.

A sintaxe básica do Event Handler de Nível 1 envolve as seguintes etapas:

1. Seleção do elemento HTML alvo usando métodos como `document.getElementById`, `document.querySelector`, ou qualquer outro método de seleção de elementos.
```javascript
var botao = document.getElementById("idBotao2")
```

2. Atribuição de um manipulador de evento a uma propriedade do elemento HTML.
```javascript
botao.onclick = tratamentoBotao2
```
3. Definição de uma função que será executada quando o evento ocorrer.
```javascript
function tratamentoBotao2() {
	console.log("Clicou Botão 2");
}
```

Aqui está um exemplo do Event Handler de Nível 1 no código fornecido:

```javascript
// Seleciona o elemento HTML com o ID "idBotao2"
var botao = document.getElementById("idBotao2");

// Atribui uma função ao evento de clique (onclick) no botão
botao.onclick = tratamentoBotao2;

// Define a função que será executada quando o botão for clicado
function tratamentoBotao2() {
    console.log("Clicou Botão 2");
}

// Atribui uma função anônima ao evento de clique duplo (ondblclick) no botão
botao.ondblclick = function() {
    console.log("Clique duplo em Botão 2");
}

// Atribui uma função anônima ao evento de passagem do mouse (onmouseover) no botão
botao.onmouseover = function() {
    console.log("Passou o mouse por cima do botão 2");
}
```

Neste exemplo, o Event Handler de Nível 1 é usado para atribuir três tipos diferentes de manipuladores de eventos ao botão com o ID "idBotao2". O evento `onclick` é tratado pela função `tratamentoBotao2()`, enquanto os eventos `ondblclick` e `onmouseover` são tratados por funções anônimas definidas diretamente no local da atribuição do evento.

**Vantagens do Event Handler de Nível 1:**
1. **Simplicidade:** É uma técnica direta e fácil de entender para atribuir eventos a elementos HTML.
2. **Compreensão Rápida:** A abordagem é fácil de entender, mesmo para iniciantes em JavaScript.

**Limitações do Event Handler de Nível 1:**
1. **Poluição Global:** As funções associadas a eventos são globais e podem causar conflitos de nomes se não forem gerenciadas adequadamente.
2. **Limitação de Um Único Manipulador:** Cada propriedade de evento pode ter apenas um único manipulador atribuído a ela. Isso limita a flexibilidade em situações mais complexas.

## Event Handler Nv2
O Event Handler de Nível 2 envolve o uso do método `addEventListener` para associar funções de manipulação de eventos a elementos HTML. Em vez de atribuir diretamente manipuladores de eventos a propriedades do elemento, essa abordagem permite a anexação de vários manipuladores de eventos ao mesmo elemento, proporcionando maior organização do código e flexibilidade na manipulação de eventos.

A sintaxe básica do Event Handler de Nível 2 envolve as seguintes etapas:

1. Seleção do elemento HTML alvo usando métodos como `document.getElementById`, `document.querySelector`, ou qualquer outro método de seleção de elementos.
   
```javascript
var botao3 = document.getElementById("idBotao3")
```

2. Uso do método `addEventListener` para especificar o tipo de evento (como "click" ou "mouseover") e a função de tratamento associada a esse evento.
   
```javascript
botao3.addEventListener("click", tratamentoBota3) //função de callback
```

3. Definição da função de tratamento que será executada quando o evento ocorrer.
```javascript
function tratamentoBota3() {
	console.log("Clicou Botão 3");
}
```

**Exemplo de Uso:**

Aqui está um exemplo do Event Handler de Nível 2 no código fornecido:

```javascript
// Seleciona o elemento HTML com o ID "idBotao3"
var botao3 = document.getElementById("idBotao3");

// Atribui um manipulador de evento "click" ao botão
botao3.addEventListener("click", tratamentoBota3);

// Define a função que será executada quando o botão for clicado
function tratamentoBota3() {
    console.log("Clicou Botão 3");
}

// Atribui um manipulador de evento "mouseover" ao botão
botao3.addEventListener("mouseover", function() {
    console.log("Passou o mouse por cima do botão 3");
});
```

Neste exemplo, o Event Handler de Nível 2 é usado para associar dois manipuladores de eventos ao botão com o ID "idBotao3". Os eventos "click" e "mouseover" são tratados pelas funções `tratamentoBota3()` e uma função anônima, respectivamente.

**Vantagens do Event Handler de Nível 2:**
1. **Organização do Código:** A abordagem `addEventListener` torna o código mais organizado, pois permite que você liste todos os manipuladores de eventos associados a um elemento em um só lugar.
2. **Flexibilidade:** Você pode associar vários manipuladores de eventos ao mesmo elemento sem substituir os existentes. Isso é útil em cenários em que diferentes partes do código precisam responder aos mesmos eventos.
3. **Maior Reutilização de Código:** O código JavaScript é separado do HTML, o que facilita a reutilização de funções de manipulação de eventos em outros elementos.

**Limitações do Event Handler de Nível 2:**
1. **Compatibilidade com Navegadores Antigos:** Em versões mais antigas do Internet Explorer, pode haver problemas de compatibilidade com o método `addEventListener`. Nesse caso, é necessário fornecer uma alternativa.

## preventDefault()
O `preventDefault()` é um método que faz parte do objeto de evento (`Event`) em JavaScript. Ele é usado para evitar que o comportamento padrão associado a um evento ocorra. O comportamento padrão de um evento é a ação que geralmente ocorre quando o evento é acionado, como abrir um link ou enviar um formulário.

**Quando Usar o `preventDefault()`?**
Você deve usar o `preventDefault()` quando deseja controlar ou impedir que o comportamento padrão de um evento ocorra. Alguns cenários comuns incluem:

1. **Links:** Para impedir que um hiperlink navegue para outra página.
2. **Formulários:** Para evitar o envio automático de um formulário quando um botão de envio é clicado.
3. **Eventos de Teclado:** Para evitar que uma tecla pressionada execute uma ação padrão, como o retorno de uma tecla "Enter" em um formulário.

**Sintaxe do `preventDefault()`:**
A sintaxe básica do `preventDefault()` envolve as seguintes etapas:

1. O evento, como um clique em um link ou um envio de formulário, é acionado.
2. Uma função de tratamento de evento é chamada, e o objeto de evento é passado como um argumento.
3. A função de tratamento de evento chama o método `preventDefault()` no objeto de evento.
4. O método `preventDefault()` evita que o comportamento padrão do evento ocorra.

**Exemplo de Uso:**
Aqui está um exemplo de uso do `preventDefault()` para evitar o envio de um formulário quando um botão de envio é clicado:

```html
<form id="meuFormulario">
    <input type="text" name="campo1" placeholder="Digite algo">
    <button type="submit" id="botaoEnviar">Enviar</button>
</form>

<script>
    const formulario = document.getElementById("meuFormulario");
    const botaoEnviar = document.getElementById("botaoEnviar");

    botaoEnviar.addEventListener("click", function(event) {
        event.preventDefault(); // Impede o envio padrão do formulário
        console.log("Formulário não foi enviado.");
    });
</script>
```

Neste exemplo, quando o botão "Enviar" é clicado, o método `preventDefault()` é chamado no objeto de evento associado ao clique. Isso evita que o formulário seja enviado automaticamente.

**Vantagens do `preventDefault()`:**
1. **Controle do Comportamento:** Permite que você controle o que acontece quando um evento é acionado, impedindo o comportamento padrão.
2. **Validação de Dados:** Pode ser usado para validar dados antes de permitir a execução de ações, como o envio de um formulário.
3. **Melhoria da Experiência do Usuário:** Ajuda a criar uma experiência mais interativa e responsiva para o usuário.

**Limitações do `preventDefault()`:**
1. **Compatibilidade com Navegadores:** É importante verificar a compatibilidade do navegador, pois alguns navegadores mais antigos podem não oferecer suporte completo ao `preventDefault()`. Nesses casos, você pode precisar fornecer alternativas.