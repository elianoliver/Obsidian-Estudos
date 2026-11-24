O evento **`DOMContentLoaded`** é disparado pelo navegador quando **todo o HTML do documento foi carregado e analisado** (ou seja, quando o DOM – Document Object Model – está completamente construído). Ele **não espera** que recursos externos, como imagens, folhas de estilo (CSS) ou scripts externos, sejam carregados. Isso o diferencia do evento **`load`**, que só é disparado quando **todos os recursos** (HTML, CSS, imagens, etc.) estão completamente carregados.

- **Quando é útil?** Use o `DOMContentLoaded` quando você precisa executar código JavaScript assim que o DOM estiver pronto, mas sem esperar por recursos como imagens ou estilos, o que torna a execução mais rápida.

## Como funciona?

O `DOMContentLoaded` é um evento associado ao objeto `document`. Você pode "escutá-lo" usando o método `addEventListener()` para executar uma função assim que o DOM estiver carregado.

## Sintaxe básica
```javascript
document.addEventListener("DOMContentLoaded", function () {
    console.log("O DOM foi carregado!");
});
```

- **O que acontece?** Quando o HTML é completamente carregado e o DOM está pronto, a função passada no `addEventListener()` é executada. No exemplo acima, a mensagem "O DOM foi carregado!" será exibida no console.

## Diferença entre `DOMContentLoaded` e `load`

- **`DOMContentLoaded`**: Dispara assim que o HTML é carregado e o DOM está pronto, ignorando recursos externos (imagens, CSS, etc.).

- **`load`**: Dispara apenas quando **tudo** na página (HTML, CSS, imagens, scripts, etc.) está carregado.

- **Por que isso importa?** O `DOMContentLoaded` é mais rápido, pois não espera pelos recursos externos, sendo ideal para manipulações no DOM que não dependem de imagens ou estilos.

## Exemplo prático

Vamos analisar o exemplo fornecido para entender melhor:
### HTML
```html
<h1>Mudança de Imagem ao Carregar o DOM</h1>
<img
  id="example-img"
  src="https://cdn.freecodecamp.org/curriculum/cat-photo-app/relaxing-cat.jpg"
  alt="Gato relaxando"
/>
```

### JavaScript
Queremos mudar a imagem assim que o DOM estiver carregado.

1. **Função para mudar a imagem**: Essa função seleciona a imagem pelo `id` e altera o atributo `src` para uma nova URL, exibindo uma mensagem no console.
```javascript
function changeImg() {
	const img = document.getElementById("example-img");
	img.src = "https://cdn.freecodecamp.org/curriculum/responsive-web-design-principles/FCCStickers-CamperBot200x200.jpg";
	console.log("A imagem foi alterada");
}
```

2. **Verificar o estado do DOM e adicionar o evento**:
   ```javascript
   if (document.readyState === "loading") {
       document.addEventListener("DOMContentLoaded", changeImg);
   } else {
       console.log("DOMContentLoaded já foi disparado");
       changeImg();
   }
   ```

- **`document.readyState`**: Verifica o estado de carregamento do documento:
	- `"loading"`: O DOM ainda está sendo carregado, então adicionamos o ouvinte para `DOMContentLoaded`.
	- Qualquer outro estado (como `"interactive"` ou `"complete"`): O DOM já está carregado, então chamamos `changeImg()` diretamente.

- **Resultado**: Quando o DOM está pronto, a imagem muda para a nova URL. Você pode notar um leve "piscar" na tela, pois a troca ocorre rapidamente após o carregamento do HTML.

## Por que usar `DOMContentLoaded`?

- **Velocidade**: Permite executar código JavaScript assim que o DOM está pronto, sem esperar por imagens ou estilos pesados.

- **Casos de uso**:
  - Inicializar elementos do DOM, como adicionar ouvintes de eventos a botões ou formulários.
  - Manipular elementos HTML (ex.: alterar textos, classes ou atributos) antes que a página esteja completamente carregada.
  - Exemplo: Mostrar um menu, configurar formulários ou carregar dados dinamicamente assim que o DOM estiver acessível.

## Cuidados

- **Recursos externos**: O `DOMContentLoaded` não espera por imagens ou CSS, então, se seu código depende desses recursos, use o evento `load` em vez disso.
  
- **Verificação de estado**: Sempre verifique `document.readyState` para garantir que o evento `DOMContentLoaded` não foi perdido (caso o código execute após o DOM já estar carregado).

## Resumo

- **O que é?** O evento `DOMContentLoaded` é disparado quando o HTML é carregado e o DOM está pronto, sem esperar por imagens ou CSS.
  
- **Como usar?** Adicione um ouvinte com `document.addEventListener("DOMContentLoaded", funcao)`.
  
- **Diferença do `load`**: O `load` espera todos os recursos (imagens, CSS, etc.), enquanto o `DOMContentLoaded` é mais rápido, focando apenas no HTML.
  
- **Exemplo prático**: Alterar o atributo `src` de uma imagem assim que o DOM está pronto.
  
- **Quando usar?** Para manipulações no DOM que não dependem de recursos externos, como configurar elementos ou adicionar eventos.
  
- **Dica**: Use `document.readyState` para verificar se o DOM já foi carregado e evitar erros.

