Para iniciar sua jornada de aprendizado em JavaScript, você não precisa de nada mais do que um navegador web moderno. As versões recentes de navegadores populares, como Firefox, Chrome, Microsoft Edge e Safari, oferecem suporte aos recursos que discutiremos neste curso.

### Usando o Console JavaScript
Uma ferramenta incrivelmente útil para explorar e experimentar com JavaScript é o **Console JavaScript** (às vezes chamado de Web Console ou simplesmente Console). Ele é uma ferramenta que permite inserir e executar código JavaScript na página atual.

Aqui, mostraremos como abrir o console nos navegadores mais comuns:

- **Firefox:** No Firefox, você pode abrir o console pressionando `Ctrl + Shift + K` 
  (ou `Cmd + Option + K` em Mac). 

- **Chrome:** No Chrome, você pode abrir o console pressionando `Ctrl + Shift + J` 
  (ou `Cmd + Option + J` em Mac). 

- **Microsoft Edge:** Para abrir o console no Microsoft Edge, use `Ctrl + Shift + J` 
  (ou `Cmd + Option + J` em Mac).

### Inserindo e Executando JavaScript
Assim que o console estiver aberto, você verá uma linha de entrada na parte inferior, onde pode inserir código JavaScript. A saída será exibida no painel acima.

O console funciona de maneira semelhante à função `eval()` do JavaScript: a última expressão digitada é retornada. Isso significa que você pode experimentar com código JavaScript diretamente no console.

Exemplo:
```javascript
// Exemplo 1: Avaliando uma expressão
let resultado = eval("2 + 3");
console.log(resultado); // Isso imprimirá "5" no console

// Exemplo 2: Definindo uma função e chamando-a
eval("function saudacao(nome) { return 'Olá, ' + nome; }");
console.log(saudacao("Alice")); // Isso imprimirá "Olá, Alice" no console
```
#### Inserção de Múltiplas Linhas
Você pode inserir código JavaScript em várias linhas no console:

- Se a string digitada estiver incompleta (por exemplo, você digitou `function foo() {`), o console tratará Enter como uma quebra de linha e permitirá que você digite outra linha.

- Se você segurar Shift enquanto pressiona Enter, o console também permitirá que você insira várias linhas.

- No Firefox, você pode ativar o modo de entrada multilinha, onde pode inserir várias linhas em um mini-editor e, em seguida, executar tudo quando estiver pronto.

Agora, para começar a praticar, abra o console e copie o seguinte código JavaScript. Cole-o na linha de comando e pressione Enter para vê-lo em ação:

```javascript
(function () {
	"use strict";
	
	/* Início do seu código */
	function greetMe(texto) {
		alert(`Olá ${texto}`);
	}
	
	greetMe("Mundo");
	/* Fim do seu código */
})();
```
