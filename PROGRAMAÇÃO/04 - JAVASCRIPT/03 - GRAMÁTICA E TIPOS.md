## SUMÁRIO
- [[#SINTAXE BÁSICA]]
	- [[#Case-Sensitive e Conjunto de Caracteres Unicode]]
	- [[#Instruções e Espaços em Branco]]
	- [[#Ponto e Vírgula]]
- [[#COMENTÁRIOS]]
	- [[#Comentários de Uma Linha]]
	- [[#Comentários de Múltiplas Linhas]]
- [[#DECLARAÇÕES]]
	- [[#Nomes de Variáveis]]
	- [[#Declarando Variáveis]]
	- [[#Classificando Variáveis]]
	- [[#Variáveis Globais e Locais]]
	- [[#Variáveis e Hoisting]]
	- [[#Constantes]]
- [[#ESTRUTURA DE DADOS E TIPOS]]
	- [[#Tipos de Dados]]
	- [[#Conversão de Tipos de Dados]]
	- [[#Conversão de Strings para Números]]
- [[#LITERAIS]]
	- [[#Array Literal]]
	- [[#Vírgulas Extras em Array Literal]]
	- [[#Literais Boolean]]
	- [[#Literais Inteiros]]
	- [[#Literais de Ponto Flutuante]]
	- [[#Objeto Literal]]
	- [[#Expressão Regex Literal]]
	- [[#String Literal]]
## SINTAXE BÁSICA
O JavaScript é uma linguagem de programação que compartilha muitos aspectos de sua sintaxe com o Java, mas também incorpora influências de linguagens como Awk, Perl e Python.

### Case-Sensitive e Conjunto de Caracteres Unicode
É importante entender que o JavaScript é **case-sensitive**, o que significa que ele faz distinção entre letras maiúsculas e minúsculas. Por exemplo, as variáveis `Früh` e `früh` são tratadas como diferentes no JavaScript. Além disso, o JavaScript utiliza o conjunto de caracteres **Unicode**, o que permite a utilização de caracteres especiais em nomes de variáveis, como:

```javascript
var Früh = "foobar";
```

Aqui, usamos a palavra alemã "Früh" (que significa "cedo") como nome de variável.

### Instruções e Espaços em Branco
No JavaScript, as instruções são chamadas de **declarações** e são separadas por um ponto e vírgula (`;`). Espaços, tabulações e novas linhas são chamados de **espaços em branco** e são utilizados para formatar o código, tornando-o mais legível. O código fonte JavaScript é lido **da esquerda para a direita** e é convertido em uma sequência de elementos de entrada, incluindo símbolos, caracteres de controle, terminadores de linha, comentários e espaços em branco.

### Ponto e Vírgula
Embora o ECMAScript (a especificação do JavaScript) defina regras para a inserção automática de ponto e vírgula (ASI) para terminar declarações, é altamente recomendável **adicionar ponto e vírgula explicitamente no final de suas declarações**. Isso ajuda a evitar comportamentos inesperados e torna o código mais robusto e claro. Por exemplo:

```javascript
var x = 5; // Ponto e vírgula explicitamente adicionado
```

Lembre-se de que uma compreensão sólida da sintaxe é fundamental para escrever código JavaScript eficaz e livre de erros.

## COMENTÁRIOS
Os comentários são uma parte essencial da programação, pois ajudam a documentar e explicar o código para você mesmo e para outros desenvolvedores que possam trabalhar com ele. Em JavaScript, a sintaxe para criar comentários é semelhante à de muitas outras linguagens, como C++:

### Comentários de Uma Linha
Para criar um **comentário de uma linha**, você pode usar `//` seguido pelo texto do comentário. Tudo o que vem após `//` na mesma linha é tratado como um comentário e é ignorado pelo interpretador:

```javascript
// Este é um comentário de uma linha
```

### Comentários de Múltiplas Linhas
Para criar **comentários de múltiplas linhas**, você pode usar `/*` para iniciar o comentário e `*/` para encerrá-lo. Tudo o que estiver entre `/*` e `*/` será tratado como um comentário e pode abranger várias linhas:

```javascript
/*
  Este é um comentário de múltiplas linhas.
  Pode abranger várias linhas de código.
*/
```

É importante observar que você não pode **aninhar comentários**, ou seja, não pode abrir um comentário de múltiplas linhas dentro de outro comentário de múltiplas linhas. Isso resultará em um erro de sintaxe, como mostrado no exemplo abaixo:

```javascript
/*
  Isto é um comentário de múltiplas linhas.
  /* Isso não é permitido e causará um erro! */
*/
```

O uso adequado de comentários pode tornar seu código mais legível e facilitar a colaboração com outros desenvolvedores. Portanto, lembre-se de documentar seu código de forma clara e concisa.


## DECLARAÇÕES
Em JavaScript, as declarações são uma parte fundamental da linguagem e são usadas para criar variáveis e constantes. Existem três tipos principais de declarações em JavaScript:

- `var`: Declara uma variável, opcionalmente, inicializando-a com um valor.
- `let`: Declara uma variável local de escopo do bloco, opcionalmente, inicializando-a com um valor. 
- `const`: Declara uma constante de escopo de bloco, apenas de leitura.
### Nomes de Variáveis
Os nomes de variáveis, chamados de identificadores, seguem algumas regras em JavaScript:

- Deve começar com uma `letra`, sublinhado `(_)` ou cifrão `($)`.
- Os caracteres subsequentes podem ser letras, números (0-9), sublinhados ou cifrões.
- JavaScript é **case-sensitive**, o que significa que letras maiúsculas e minúsculas são diferentes. Por exemplo, `nome` e `Nome` são considerados identificadores diferentes.

Exemplos de nomes de variáveis válidos incluem `Numero_visitas`, `temp99` e `_nome`.

### Declarando Variáveis
Você pode declarar uma variável de três formas:

- Com a palavra chave `var`. Por exemplo, `var x = 42`. Esta sintaxe pode ser usada para declarar tanto variáveis locais como variáveis globais.
  
- Por simples adição de valor. Por exemplo, `x = 42`. Isso declara uma variável global. Essa declaração gera um aviso de advertência no JavaScript. <span style="color:red"> Você não deve usar essa variante. </span>

- Com a palavra chave `let`. Por exemplo, `let y = 13`. Essa sintaxe pode ser usada para declarar uma variável local de escopo de bloco.

### Classificando Variáveis 
Ao criar uma variável em JavaScript, é importante entender como ela se comporta quando você não define um valor inicial. Vamos descomplicar isso:

Se você declara uma variável usando `var` ou `let` e não atribui um valor inicial, essa variável terá o valor especial chamado de `undefined`. É como se você reservasse um espaço, mas não colocasse nada dentro dele.

```javascript
var a;
console.log("O valor de a é " + a); // Saída: "O valor de a é undefined"
```

Se você tentar acessar uma variável que não foi declarada, o JavaScript irá lançar um erro chamado `ReferenceError`. Isso é como pedir algo que nem existe, o que é um erro lógico.

```javascript
var a;
console.log("O valor de b é " + b); // Isso causará um erro (ReferenceError)
```

Agora, você pode usar o valor `undefined` para verificar se uma variável foi definida ou não. Por exemplo, se você deseja saber se a variável `input` tem um valor, pode fazer o seguinte:

```javascript
var input;
if (input === undefined) {
  façaIsso();
} else {
  façaAquilo();
}
```

O valor `undefined` também age como "falso" em contextos booleanos. Isso significa que, se você verificar uma variável com valor `undefined` em uma condição, ela será avaliada como "falsa". Por exemplo:

```javascript
var myArray = [];
if (!myArray[0]) myFunction(); // Isso executará myFunction porque myArray[0] é undefined, que é "falso".
```

Quando você realiza operações numéricas em uma variável `undefined`, ela se comporta como "NaN" (Not-a-Number), o que significa que não é um valor numérico válido:

```javascript
var a;
a + 2; // Avaliado como NaN
```

Se uma variável contém o valor `null`, ela age como "0" em contextos numéricos e como "falso" em contextos booleanos:

```javascript
var n = null;
console.log(n * 32); // A saída será 0.
```

### Variáveis Globais e Locais
Quando você cria uma variável em JavaScript, ela pode viver em diferentes "espaços" dependendo de onde você a declara. Isso afeta quem pode vê-la e usá-la no seu código.

- **Variável Global:** Imagine isso como uma lousa gigante no meio da sua escola. Qualquer pessoa que passe por ela pode ver e escrever nela. Quando você declara uma variável fora de qualquer função, ela se torna uma variável global. Isso significa que ela está disponível para qualquer pedaço de código no documento atual. Todos podem ver e modificar essa variável.

- **Variável Local:** Agora, pense em uma lousa que está dentro de uma sala de aula. Só as pessoas que estão naquela sala podem ver e escrever nela. Quando você declara uma variável dentro de uma função, ela se torna uma variável local. Isso significa que ela está disponível apenas dentro dessa função. Ninguém fora da função pode vê-la ou mexer com ela.

Antes da chegada do ECMAScript 6, JavaScript não entendia muito sobre salas de aula (ou seja, blocos). Se você declarasse uma variável dentro de um bloco de código (como um `if`), JavaScript a tratava como se estivesse no mesmo espaço que a lousa gigante (variável global). Por exemplo, se você criasse uma variável `x` dentro de um bloco `if`, ela era vista por todos como uma variável global. Mas isso mudou com o ECMAScript 6, que introduziu a declaração `let`. Agora, se você declarar uma variável com `let` dentro de um bloco, ela fica trancada naquela sala de aula (variável local) e ninguém mais pode vê-la.

Aqui está um exemplo para ilustrar: Se você cria uma variável `x` dentro de um `if`, o JavaScript antigo (pré-ES6) a tratará como global, mas se você usar `let`, ela ficará restrita àquele bloco (sala de aula).

```javascript
if (true) {
  var x = 5; // Variável global antes do ES6
}
console.log(x); // 5

if (true) {
  let y = 5; // Variável local após o ES6
}
console.log(y); // ReferenceError: y não está definido
```

### Variáveis e Hoisting
Imagine que você está construindo uma torre com vários andares. Cada andar é como um passo no seu código JavaScript. Quando você declara uma variável usando `var`, o JavaScript faz algo mágico chamado "hoisting" (elevação).

O hoisting é como se o JavaScript pegasse todas as suas declarações de variáveis e as movesse para o topo da sua torre de código. No entanto, essas variáveis não têm um valor definido quando são movidas para o topo. Elas estão lá, mas estão vazias, como caixas prontas para serem preenchidas.

```javascript
console.log(numero); // Isso não causa um erro, mas exibe "undefined"
var numero = 3; // Aqui você finalmente coloca o valor 3 na caixa
```

Quando você faz `console.log(numero)` antes de atribuir o valor 3 à variável `numero`, JavaScript não fica confuso ou quebra. Em vez disso, ele apenas diz: "Ei, essa variável `numero` existe, mas não tem um valor ainda. Deixe-me mostrar `undefined` para você."

No entanto, é uma prática recomendada declarar suas variáveis no início da torre (ou seja, no início da função ou bloco), para que você e outros programadores saibam imediatamente quais variáveis estão em jogo. Isso torna seu código mais organizado e fácil de ler.

Portanto, ao programar em JavaScript, lembre-se de que as variáveis declaradas com `var` são "elevadas" para o topo, mas ainda não têm valor até que você as atribua. Mantenha sua torre de código organizada para evitar surpresas!

```ad-info
Com `let`, o hoisting ocorre, mas as variáveis não são inicializadas automaticamente e qualquer tentativa de acesso antes de sua declaração resultará em um Reference Error.
```

### Constantes
Uma constante é uma variável que não pode ser alterada após a sua inicialização. Ela é declarada usando a palavra-chave `const`. As regras de escopo para constantes são as mesmas que as de variáveis declaradas com `let`.

- Não se pode alterar o valor de uma constante já atribuída.
- Se a palavra-chave `const` for omitida, presume-se que o identificador represente uma var.
- Não pode declarar uma constante com o mesmo nome de uma função ou variável no mesmo escopo.

```javascript
//exemplo de declaração
const PI = 3.14;

// Isso causará um erro
const minhaFuncao = 5;
function minhaFuncao() {}
```

## ESTRUTURA DE DADOS E TIPOS
Na programação, os dados são a essência de qualquer aplicação, e é fundamental compreender os tipos de dados que podemos utilizar. Eles desempenham um papel crucial na definição do comportamento do nosso código. Vamos explorar cinco tipos de dados comuns e dois tipos especiais de dados, juntamente com alguns operadores que nos ajudam a trabalhar com eles.
### Tipos de Dados
1. **string:** Uma string é um conjunto de caracteres alfanuméricos, normalmente delimitados por aspas simples (' '), duplas (" ") ou acento grave(\`\`). Por exemplo, 'isso é uma string' ou "123". Elas são usadas para representar texto.
   
2. **number:** O tipo de dado numérico é usado para representar valores numéricos, sejam eles inteiros (como 123) ou números decimais (como 12.5).
   
3. **boolean:** Este tipo de dado pode assumir apenas dois valores: `true` ou `false`. É frequentemente usado para controle de fluxo e tomada de decisões.
   
4. **Object:** O tipo "Object" é uma estrutura de dados complexa que pode conter várias propriedades e métodos. É usado para representar entidades complexas na programação.
   
5. **Function:** Funções são blocos de código que podem ser chamados para realizar tarefas específicas. Elas são essenciais para a modularização e reutilização do código.

#### Tipos de Dados Especiais
6. **Null:** O valor `null` é um tipo especial que representa a ausência de valor ou a falta de um objeto. Pode ser atribuído a variáveis quando queremos explicitamente indicar que elas não têm valor.
   
7. **Undefined:** O valor `undefined` é atribuído a uma variável quando ela foi declarada, mas ainda não recebeu um valor. Também é retornado quando se tenta acessar uma propriedade inexistente de um objeto.

#### Tipos de Objetos
Além dos tipos de dados primitivos mencionados acima, existem objetos predefinidos em JavaScript que desempenham um papel significativo na linguagem (observe que os nomes começam com maiúsculo):

1. **Object:** Representa um objeto genérico que pode conter propriedades e métodos.
2. **Date:** Utilizado para manipular datas e horários.
3. **Array:** Uma estrutura de dados que armazena uma coleção ordenada de elementos.
4. **Number:** Este objeto fornece métodos para realizar operações matemáticas em números.
5. **String:** O objeto String oferece métodos para trabalhar com strings, como concatenação, pesquisa e extração de substrings.
6. **Boolean:** O objeto Boolean oferece métodos para trabalhar com valores booleanos.

#### Operadores para testar tipos de dados
Para verificar o tipo de dados de uma variável ou expressão, podemos usar dois operadores principais:

1. **typeOf(  ):** O operador typeOf permite verificar o tipo de dado de uma variável. 
   Por exemplo, `typeOf(123)` retornaria "number".
 
4. **isNaN(  ):** O operador isNaN (Not a Number) é usado para verificar se um valor não é um número válido. Retorna `true` se o valor não for um número e `false` se for.

### Conversão de Tipos de Dados
JavaScript é uma linguagem dinamicamente tipada. Isso significa que você não precisa especificar o tipo de dado de uma variável quando declará-la, e tipos de dados são convertidos automaticamente conforme a necessidade durante a execução do script. 

Então, por exemplo, você pode definir uma variável da seguinte forma:

```javascript
var answer = 42; // Declaração inicial como número
answer = "Obrigado pelos peixes..."; // Reatribuição como string
```

**Conversão Automática em Expressões**

- Em expressões envolvendo valores numéricos e strings com o operador `+`, JavaScript converte valores numéricos para strings.

```javascript
x = "A resposta é " + 42; // "A resposta é 42"
y = 42 + " é a resposta"; // "42 é a resposta"
```

- Nas declarações envolvendo outros operadores, JavaScript não converte valores numéricos para strings.

```javascript
"37" - 7; // 30
"37" + 7; // "377"
```

### Conversão de Strings para Números

**Métodos de Conversão**
Existem métodos para converter strings que representam números em valores numéricos:

1. **parseInt()**
   - Retorna números inteiros.
   - É comumente usado para valores inteiros.
   - É uma boa prática incluir o parâmetro da base para especificar o sistema numérico a ser usado.

```javascript
var numero = parseInt("42"); // Retorna o número inteiro 42
```

2. **parseFloat()**
   - Retorna números de ponto flutuante.
   - É usado para valores com casas decimais.

```javascript
var decimal = parseFloat("3.14"); // Retorna o número de ponto flutuante 3.14
var decimal = parseFloat("A"); // Retorna NaN (Not a Number)
```

4. **Number()**
- Retorna números inteiros ou de pontos flutuantes, à depender do valor passado.
- Ela é versátil e pode ser aplicada a diversos tipos de dados, incluindo strings.

```javascript
var numero = Number("42"); // Retorna o número inteiro 42
var numero = Number("42.5"); // Retorna o número de ponto flutuante 42.5
var numero = Number("A"); // Retorna NaN (Not a Number)
```

3. **Conversão Alternativa com o Operador +**
Você também pode converter uma string em número usando o operador `+` (operação de adição):

```javascript
var resultado = +"42"; // Converte a string "42" em um número
var resultado = +"A"; // Retorna NaN (Not a Number)
```

É importante notar que, no exemplo `"1.1" + "1.1"`, a concatenação de strings resulta em `"1.11.1"`.
  
Usando o operador `+`, como em `(+"1.1") + (+"1.1")`, você obtém a soma correta de `2.2`. Os parênteses são usados apenas para maior clareza no código e não são estritamente necessários.


## LITERAIS
Imagine literais como blocos de construção básicos na linguagem JavaScript. Eles são valores fixos que você insere diretamente em seu código. Em outras palavras, são como informações concretas que você não precisa calcular ou buscar em nenhum outro lugar. Você simplesmente os "literalmente" escreve em seu script.

**Exemplos de Literais:**
- Um número como `42`.
- Uma string de texto como `"Olá, mundo!"`.
- O valor lógico `true` ou `false`.
- O valor especial `null`, indicando a ausência de valor.
- O valor `undefined`, que significa que a variável ou propriedade não foi definida.

**O Que Literais Não São?**
- Literais não são variáveis. Eles são valores fixos que não podem ser alterados.
- Eles também não são o resultado de cálculos ou operações.

**Como os Literais São Usados?**
- Quando você define o valor de uma variável diretamente em seu código, você está usando um literal. Por exemplo, `var idade = 30;` está usando o literal `30` para definir o valor da variável `idade`.

Em resumo, literais são como os blocos de construção fundamentais que você usa para criar e representar valores em JavaScript. Eles são informações fixas que você insere **diretamente** em seu código para trabalhar com dados de forma direta e concreta.

### Array Literal
Um array literal é uma lista de zero ou mais expressões, representando elementos do array, inseridas entre colchetes `[]`.

Quando você cria um array usando um array literal, ele é inicializado com os valores especificados como seus elementos.

```javascript
var coffees = ["French Roast", "Colombian", "Kona"];
```

Nesse exemplo, `coffees` é um array com três elementos e um comprimento de três.

Vamos resumir o tópico sobre "Vírgulas Extras em Array Literal":

#### Vírgulas Extras em Array Literal
Em um array literal, você não precisa especificar todos os elementos.

Se você colocar duas vírgulas em uma linha, o array é criado com `undefined` para os elementos não especificados.

```javascript
var fish = ["Lion", , "Angel"]; //fish.length = 3 elementos
//`fish[0]` é "Lion", 
//`fish[1]` é `undefined`, 
//`fish[2]` é "Angel".
```

Se você adicionar uma vírgula no final da lista de elementos de um array, essa vírgula será simplesmente ignorada.

Além disso, o número de vírgulas extras no final da lista afeta o comprimento do array, criando novos elementos vazios para cada vírgula adicional.

```javascript
var myList = ["home", , "school", ]; //myList.length = 3 elementos
// myList[0] é "home"
// myList[1] é `undefined`
// myList[2] é "school"
```

É importante observar que vírgulas extras podem criar erros em navegadores web antigos. Então não use. Ao invés disso, recomenda-se declarar explicitamente os elementos em falta como `undefined` para aumentar a clareza e a manutenção do código.
### Literais Boolean
O tipo Boolean em JavaScript é usado para representar valores lógicos, que podem ser apenas dois: verdadeiro (`true`) e falso (`false`).

- `true` ou `1` representa uma afirmação verdadeira.
- `false` ou `0` representa uma afirmação falsa.

É importante não confundir esses valores primitivos com o objeto Boolean, que é uma estrutura mais complexa usada para trabalhar com valores booleanos de maneira mais avançada. Portanto, ao lidar com verdadeiro ou falso simples, você utiliza os literais `true` e `false`.
### Literais Inteiros
Inteiros podem ser expressos em diferentes bases: 

- **decimal** (base 10). começa sem o `0`.
- **octal** (base 8). começa com `0` e pode conter apenas dígitos de 0 a 7.
- **hexadecimal** (base 16). começa com `0x` ou `0X` e pode incluir dígitos de 0 a 9 e as letras a-f (ou A-F).
- **binária** (base 2). começa com `0b` ou `0B` e só pode conter os dígitos 0 e 1.

```javascript
// 0, 117 and -345 (decimal, base 10)
// 015, 0001 and -077 (octal, base 8)
// 0x1123, 0x00111 and -0xF1A7 (hexadecimal, "hex" or base 16)
// 0b11, 0b0011 and -0b11 (binário, base 2)
```

### Literais de Ponto Flutuante
Um literal de ponto flutuante pode ter as seguintes partes:

  - Um inteiro decimal precedido por um sinal (+ ou -).
  - Um ponto decimal ( . )
  - Uma fração (outro número decimal).
  - Um expoente, indicado por "e" ou "E", seguido por um inteiro com um sinal opcional.

Um literal de ponto flutuante deve conter pelo menos um dígito, além de um ponto decimal ou um expoente.

```javascript
// A sintaxe geral é [(+|-)][digitos][.digitos][(E|e)[(+|-)]digitos].

//3.1415926
//-.123456789
//-3.1E+12
//.1e-23
```

### Objeto Literal
Um objeto literal é uma lista entre chaves `{}` que contém pares de nomes de `propriedades` e `valores` associados.

Os pares de propriedades e valores podem ser separados por vírgulas.

```javascript
var carro = {
	meuCarro: "Punto",
	getCarro: tipoCarro("Fiat"),
	especial: vendas,
};
```

Os nomes de propriedades podem ser:
- strings 
- números 
- e até strings vazias.

As propriedades de objeto podem ser acessadas usando a notação de ponto (`objeto.propriedade`) ou a notação de colchetes (`objeto["propriedade"]`).

```javascript
console.log(carro.meuCarro); // Punto
console.log(carro["getCarro"]); // Fiat
```

Caso o nome da propriedade contenha caracteres especiais ou não seja um identificador JavaScript válido, ele deve ser colocado entre aspas.

```javascript
var unusualPropertyNames = {
	"": "Uma string vazia",
	"!": "Bang!",
	2: "two"
}

console.log(unusualPropertyNames.""); // SyntaxError: string inesperada
console.log(unusualPropertyNames.!);  // Error: missing ) after argument list
console.log(foo.2);  // Error: missing ) after argument list

console.log(unusualPropertyNames[""]); // Uma string vazia
console.log(unusualPropertyNames["!"]); // Bang!
console.log(foo["2"]); // two
```

Objetos também podem ser aninhados, criando estruturas complexas de dados.

```javascript
var carros = {
	carroTipo1: {
		a: "Saab",
		b: "Jeep"
	},
	
	carroTipo2: {
	a: "marca1",
	b: "marca2",
	c: "marca3"
	},
	
	7: "Mazda"
}

console.log(carros.carroTipo1.b); // Jeep
console.log(carros.carroTipo2.b); // marca2
console.log(carros[7]); // Mazda
```

### Expressão Regex Literal
Uma expressão regex literal é como um "padrão de busca" que você coloca entre barras (`/.../`) para encontrar pedaços específicos de texto em outras strings.

Por exemplo, se você tiver o padrão `/ab+c/`, ele vai buscar por qualquer parte do texto que tenha um "a", seguido de um ou mais "b"s e um "c". Isso significa que ele encontraria palavras como "abc", "abbc", "abbbc", e assim por diante.

Você pode usar expressões regex com métodos especiais em JavaScript para fazer coisas como verificar se um padrão existe em uma string, encontrar todas as correspondências desse padrão ou substituir partes do texto que correspondem ao padrão.

Por exemplo, com o método `test()`, você pode verificar se um padrão está presente em uma string. Se estiver, ele retorna `true`, caso contrário, retorna `false`:

  ```javascript
  var re = /ab+c/;
  var string = "abc";
  var resultado = re.test(string); // Retorna true, porque "abc" corresponde ao padrão.
  ```

Os regex são usados ​​para realizar tarefas avançadas de busca e manipulação de texto em JavaScript. Eles são particularmente úteis quando você precisa encontrar, validar ou substituir partes específicas de texto em uma string.

Ao explorar expressões regex, você aprenderá sobre métodos como `exec()`, que encontra a primeira correspondência de um padrão em uma string, e `match()`, que encontra todas as correspondências em uma string. Essas são ferramentas poderosas para trabalhar com texto em JavaScript.

Entender expressões regex pode levar um tempo, mas é uma habilidade valiosa para qualquer programador que precise lidar com texto em seus projetos.

### String Literal
Uma string literal é uma sequência de caracteres envolta por aspas simples (`''`), aspas duplas (`""`) ou acento grave (\`\`). Pode conter zero ou mais caracteres.

Aqui estão alguns exemplos de strings literais:
  - `"foo"`: Uma string contendo a palavra "foo".
  - `'bar'`: Outra string contendo a palavra "bar".
  - \`bar\`: Outra string contendo a palavra "bar".
  - `"1234"`: Uma string contendo os dígitos "1234".
  - `"uma linha \n outra linha"`: Uma string que inclui uma quebra de linha (`\n`) para criar duas linhas de texto.
  - `"John's cat"`: Uma string que contém o apóstrofo `'`.

Você pode realizar operações com strings, como obter o comprimento da string, mesmo em strings literais. Por exemplo:

```javascript
console.log("John's cat".length);
// Isso exibirá a quantidade de caracteres na string, incluindo espaços em branco.
// Neste caso, são 10 caracteres.
```

Em JavaScript, você geralmente usa strings literais para representar texto. No entanto, quando você precisa realizar operações mais avançadas com strings, como encontrar, substituir ou manipular partes específicas do texto, você usa objetos string. Esses objetos oferecem métodos úteis para trabalhar com texto em JavaScript.

Portanto, na maioria dos casos, você usará strings literais para representar texto simples, e objetos string quando precisar de funcionalidades avançadas de manipulação de texto.

#### Uso de caracteres especiais em string
Além dos caracteres comuns, você também pode incluir caracteres especiais em strings, como mostrado no exemplo a seguir.

```javascript
"uma linha \n outra linha";
```

A tabela a seguir lista os caracteres especiais que podem ser usados em strings no JavaScript.

| Caracter | Descrição                                            |
|----------|-----------------------------------------------------|
| \0       | Byte nulo                                           |
| \b       | Backspace                                           |
| \f       | Alimentador de formulário                           |
| \n       | Nova linha                                          |
| \r       | Retorno do carro                                    |
| \t       | Tabulação                                           |
| \v       | Tabulação vertical                                  |
| \'       | Apóstrofo ou aspas simples                          |
| \"       | Aspas duplas                                        |
| \\       | Caractere de barra invertida                        |
| \XXX     | Caractere com a codificação Latin-1 em três dígitos octais XXX (entre 0 e 377). Por exemplo, \251 representa o símbolo de direitos autorais. |
| \xXX     | Caractere com a codificação Latin-1 em dois dígitos hexadecimais XX (entre 00 e FF). Por exemplo, \xA9 representa o símbolo de direitos autorais. |
| \uXXXX   | Caractere Unicode especificado por quatro dígitos hexadecimais XXXX. Por exemplo, \u00A9 representa o símbolo de direitos autorais em Unicode. Veja as sequências de escape Unicode para mais detalhes. |

#### Caracteres de Escape
Em JavaScript, os caracteres de escape são usados para representar caracteres especiais ou para escapar de aspas dentro de strings. Aqui estão alguns exemplos de como usar caracteres de escape:

1. **Escapando Aspas:**
   Você pode usar uma barra invertida para escapar de aspas dentro de uma string. Isso é útil quando você deseja incluir aspas dentro da própria string.
   
   ```javascript
   var quote = "Ele lê \"The Cremation of Sam McGee\" de R.W. Service.";
   console.log(quote);
   // Resultado: Ele lê "The Cremation of Sam McGee" de R.W. Service.
   ```

2. **Incluindo Barras Invertidas:**
   Se você deseja incluir uma barra invertida em uma string, você precisa escapar a barra invertida com outra barra invertida.
   
```javascript
var path = "c:\\temp"; 
// Resultado: c:\temp
```

3. **Quebras de Linha com Barra Invertida:**
   Você pode usar a barra invertida para inserir quebras de linha em strings. A barra invertida e a quebra de linha são removidas da string.
   
   ```javascript
   var multiLine = "Esta string \
   está quebrada \
   em várias \
   linhas.";
   console.log(multiLine); 
   // Resultado: Esta string está quebrada em várias linhas.
   ```

4. **Quebras de Linha com Heredoc (não oficial):**
   Embora JavaScript não tenha uma sintaxe oficial de "heredoc," você pode adicionar uma quebra de linha e um escape de quebra de linha no final de cada linha para criar strings multilinhas.
   
```javascript
var poema = "Rosas são vermelhas\n\
Violetas são azuis,\n\
Esse seu sorriso\n\
é o que me seduz. (Lucas Pedrosa)";

//Resultado:
//Rosas são vermelhas
//Violetas são azuis, 
//Esse seu sorriso
//é o que me seduz. (Lucas Pedrosa)
```

Lembre-se de que os caracteres de escape são usados para controlar como os caracteres especiais são interpretados em suas strings, permitindo que você inclua aspas, barras invertidas e quebras de linha conforme necessário.