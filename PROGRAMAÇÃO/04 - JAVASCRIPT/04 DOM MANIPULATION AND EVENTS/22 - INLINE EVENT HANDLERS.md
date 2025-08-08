**Inline event handlers** são atributos especiais adicionados diretamente a elementos HTML que executam código JavaScript quando um evento ocorre. Esses atributos começam com `on`, como `onclick`, `onmouseover`, `onsubmit`, etc., e contêm ou chamam código JavaScript.

## Exemplo 1: Código JavaScript direto no atributo

```html
<button onclick="alert('Olá, Mundo!')">Mostrar alerta</button>
```

- Aqui, o atributo `onclick` contém um código JavaScript (`alert('Olá, Mundo!')`) que é executado quando o botão é clicado.
  
- **Resultado**: Ao clicar no botão, uma caixa de alerta exibe a mensagem "Olá, Mundo!".

## Exemplo 2: Chamando uma função definida

Você também pode chamar uma função JavaScript definida em outro lugar, como em uma tag `<script>`:
```html
<script>
  function changeBgColor() {
    document.body.style.backgroundColor = "lightblue";
  }
</script>

<button onclick="changeBgColor()">Mudar cor de fundo</button>
```

- Nesse caso, o atributo `onclick` chama a função `changeBgColor()`, que muda a cor de fundo da página para azul claro.
  
- **Resultado**: Ao clicar no botão, a cor de fundo da página muda.

## Por que inline event handlers não são recomendados?

Embora os inline event handlers sejam simples, eles têm limitações e desvantagens significativas, tornando-os uma prática desencorajada em JavaScript moderno. Aqui estão os principais motivos:

1. **Limitação a um único ouvinte por evento**:
   - Um atributo como `onclick` só pode conter um único manipulador de evento. Se você tentar adicionar outro manipulador ao mesmo elemento, ele substituirá o anterior.
   - Exemplo: Se você adicionar `onclick="outraFuncao()"`, o primeiro `onclick` será sobrescrito.
   - Com o `addEventListener()`, você pode adicionar múltiplos ouvintes para o mesmo evento em um elemento, permitindo maior flexibilidade.

2. **Mistura de HTML e JavaScript**:
   - Inline event handlers misturam código HTML (estrutural) com JavaScript (lógico), o que dificulta a leitura, manutenção e organização do código.
   - Essa mistura vai contra o princípio da **separação de responsabilidades**, que recomenda manter HTML, CSS e JavaScript em arquivos ou contextos separados.
   - Usar `addEventListener()` mantém o JavaScript em arquivos `.js` ou tags `<script>`, deixando o HTML mais limpo.

3. **Dificuldade de manutenção**:
   - Quando o código JavaScript está espalhado pelos atributos HTML, é mais difícil encontrar, editar ou depurar.
   - Com `addEventListener()`, todo o código relacionado a eventos fica centralizado no JavaScript, facilitando a manutenção e a escalabilidade.

## Por que usar `addEventListener()` é a melhor prática?

O método **`addEventListener()`** resolve os problemas dos inline event handlers e oferece vantagens adicionais:

- **Múltiplos ouvintes**: Você pode adicionar várias funções para o mesmo evento em um elemento.
```javascript
const btn = document.getElementById("btn");
btn.addEventListener("click", () => alert("Primeira ação"));
btn.addEventListener("click", () => console.log("Segunda ação"));
```

- **Separação de responsabilidades**: O JavaScript fica isolado do HTML, tornando o código mais organizado e fácil de manter.
  
- **Flexibilidade**: Permite opções avançadas, como configurar a fase de captura (`useCapture`) ou remover ouvintes com `removeEventListener()`.
  
- **Facilidade de gerenciamento**: Você pode adicionar, remover ou modificar ouvintes dinamicamente sem alterar o HTML.

### Exemplo com `addEventListener()`

Reescrevendo o exemplo anterior com `addEventListener()`:
```html
<button id="btn">Mudar cor de fundo</button>

<script>
	const btn = document.getElementById("btn");
	
	btn.addEventListener("click", () => {
	    document.body.style.backgroundColor = "lightblue";
	});
</script>
```

- **Vantagem**: O HTML fica mais limpo, e o JavaScript está separado, facilitando a manutenção e a adição de mais ouvintes, se necessário.

## Resumo

- **Inline event handlers**: São atributos HTML (como `onclick`) que executam JavaScript diretamente ou chamam funções quando um evento ocorre.
  
- **Problemas**:
  - Só permitem um ouvinte por evento.
  - Misturam HTML e JavaScript, dificultando a manutenção.
  - Tornam o código menos legível e organizado.
    
- **Por que usar `addEventListener()`?**:
  - Permite múltiplos ouvintes para o mesmo evento.
  - Mantém o JavaScript separado do HTML.
  - Oferece maior flexibilidade e facilidade de manutenção.
    
- **Melhor prática**: Evite inline event handlers e use `addEventListener()` para gerenciar eventos em JavaScript moderno.