## Sumário
- [[#Básico do DOM]]
- [[#Manipulando o DOM]]
## Básico do DOM
De acordo com o W3C, o Modelo de Objetos do Documento (DOM) é uma "interface de programação de aplicativos para documentos HTML válidos e documentos XML bem formados. Ele define a estrutura lógica dos documentos e a maneira como um documento é acessado e manipulado".

O quê? Em termos simples, o DOM é uma representação do seu HTML para o navegador e permite que você manipule a página.

Representação visual da árvore DOM
![[dom.png| center | 500]]

Então, por que é frequentemente referido como uma árvore? Isso ocorre porque o DOM começa com um item pai único que se ramifica em itens filhos. Esses itens filhos também podem se ramificar em suas próprias árvores menores, como você vê na foto acima.

Li em alguns sites que o que você vê nas Ferramentas de Desenvolvedor é a representação visual do DOM, e embora seja extremamente próxima, não está totalmente correta. As Ferramentas de Desenvolvedor incluirão algumas informações adicionais (como pseudo classes) que não são tecnicamente parte do DOM. Se você é uma pessoa visual como eu, esta é a representação mais próxima do DOM em nosso navegador que podemos ver.

Mas espere um segundo - isso não significa que o DOM é a mesma coisa que o HTML que estamos escrevendo? Não.

Você já deixou acidentalmente de fora um elemento obrigatório e viu o navegador corrigi-lo para você? Você verá esse elemento no DOM, mesmo que o tenha deixado de fora do seu HTML. O DOM também será diferente do seu HTML se você estiver manipulando o DOM por meio do JavaScript.

Com JavaScript, você pode fazer coisas como editar o CSS da sua página, adicionar ouvintes de eventos, alterar atributos de nós e muito mais. Todas essas ações alteram o DOM em relação ao que você tinha originalmente escrito em seu HTML.

Para resumir, embora o DOM possa parecer algo super intimidante, na verdade é como os navegadores determinam o que é renderizado em nossa página e, por meio do JavaScript, é como podemos manipular esses elementos que são renderizados.

## Manipulando o DOM
Em JavaScript, a capacidade de capturar informações do Document Object Model (DOM) é essencial para interagir com elementos HTML em uma página web. O DOM representa a estrutura da página e permite que você acesse e manipule dados em tempo real. No exemplo abaixo, veremos diferentes maneiras de capturar informações de elementos HTML usando JavaScript.

**Exemplo 001 - Caixa de Texto:**
Neste exemplo, estamos capturando o valor de uma caixa de texto com o ID "idTexto" e exibindo-o no console.

```javascript
texto = document.getElementById("idTexto").value;
console.log("Texto: " + texto);
```

Também é possível usar `document.querySelector` para fazer a mesma coisa:
```javascript
texto2 = document.querySelector("#idTexto").value;
console.log("Texto2: " + texto2);
```

Além disso, podemos usar `document.querySelectorAll` para capturar múltiplos elementos com a classe "inputTexto" e obter uma lista de elementos.
```javascript
//sem o value na captura, ele devolverá uma lista com todos as classes inputTexto
texto3 = document.querySelectorAll(".inputTexto");
console.log(texto3);
```

**Exemplo 002 - Caixa de Texto Numérica:**
Aqui, estamos capturando o valor de uma caixa de texto, mas usamos a função `Number` para converter o valor em um número porque sempre que puxamos o elemento com value, ele vêm como string.

```javascript
numero = Number(document.getElementById("idNumero").value);
console.log("Número: " + numero);
```

**Exemplo 003 - Caixa de Texto de Data:**
A captura do valor de uma caixa de texto com a data é semelhante ao primeiro exemplo, mas estamos capturando a data.

```javascript
data = document.getElementById("idData").value;
console.log("Data: " + data); // Data: "2000-09-13"
```

**Exemplo 004 - Caixa de Texto de Senha:**
Capturar uma caixa de texto de senha funciona da mesma forma que uma caixa de texto normal.

```javascript
senha = document.getElementById("idSenha").value;
console.log("Senha: " + senha); // Senha: "aaaaa"
```

**Exemplo 005 - Checkbox:**
Para capturar o estado de caixas de seleção (checkboxes), usamos a propriedade `checked`. Ela retorna `true` se a caixa estiver marcada e `false` se não estiver.

```javascript
isOp1 = document.getElementById("idOpcao1").checked; // true
isOp2 = document.getElementById("idOpcao2").checked; // false
isOp3 = document.getElementById("idOpcao3").checked; // false

console.log("Op1: " + isOp1 + " Op2: " + isOp2 + " Op3: " + isOp3);
// Op1: true 
// Op2: false 
// Op3: false

if (isOp1) {
    console.log("Entrou no if"); // entrou no if
}
```

**Exemplo 006 - Radio Button:**
Neste exemplo, estamos capturando o estado de radio buttons, geralmente usados para escolher uma opção única entre várias. Utilizamos a propriedade `checked` para verificar se um radio button está selecionado.

```javascript
feminino = document.getElementById("idFeminino").checked;   // false
masculino = document.getElementById("idMasculino").checked; // true

console.log("Masculino: " + masculino + " Feminino: " + feminino);
// Masculino: true
// Feminino: false

if (feminino) {
    console.log("Feminino"); 
} else {
    console.log("Masculino"); // Masculino
}
```

Isso permite determinar qual opção foi selecionada entre "Feminino" e "Masculino". A segunda abordagem utiliza o seletor `querySelector` para obter o valor do radio button selecionado.

Pegando o valor do sexo selecionado através do name do radio button
```javascript
var sexo = document.querySelector("input[name=nmGenero]:checked").value;
console.log("Exemplo Radio 2: " + sexo); // Exemplo Radio 2: Masculino
```

**Exemplo 007 - Select:**
Aqui, estamos capturando o `value` de um elemento select (uma caixa de seleção) e exibindo-o no console.

```javascript
itemSelected = document.getElementById("idSelect");
uf = itemSelected.value;
console.log("UF: " + uf); // UF: RS
```

Pegando o `innerText` do Elemento(Option) selecionado
```javascript            
console.log("Estado: " + itemSelected.options[itemSelected.selectedIndex].innerText);
// Estado: Rio Grande do Sul
```

**Exemplo 008 - Data List:**
Em um elemento `<input>` que utiliza uma lista de dados (datalist), você pode capturar o valor selecionado da mesma forma que em um elemento `<select>`.

```javascript
navegador = document.getElementById("idNavegadores").value;
console.log("Navegador: " + navegador); // Navegador: Firefox
```

**Exemplo 009 - Textarea:**
A captura do valor de um elemento `<textarea>` (uma área de texto) é semelhante à captura de uma caixa de texto comum.

```javascript
pergunta = document.getElementById("idTextArea").value;
console.log("Pergunta: " +  pergunta);
```
