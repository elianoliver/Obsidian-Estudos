O Grid Layout é uma poderosa ferramenta do CSS que permite criar layouts complexos e responsivos de forma eficiente. Ele organiza elementos em uma grade (ou grid) bidimensional, proporcionando um alto nível de controle sobre o posicionamento e o dimensionamento de elementos em uma página da web. Neste guia, vamos explorar os conceitos básicos do Grid Layout e como começar a usá-lo em seus projetos.
![[layout-padrao-grid.png]]
# O Básico
## Começando com nosso código
Sem mais delongas, vamos começar a codificar e pôr em prática tudo isso. A primeira parte será definir o **HTML** da página:
```html
<header class="o-header">Header</header>
<aside class="o-aside">Aside</aside>
<main class="o-footer">Main</main>
<footer class="o-footer">Footer</footer>
```

Nosso primeiro passo será definir qual tag vai receber as "lacunas" para posteriormente adicionarmos nossos elementos. Bom, se tudo esta dentro de `body`, temos um bom candidato:

```css
body {
  display: grid;
}
```

Vejam que o `display` ganhou um novo valor chamado `grid`. Com isso estamos dizendo: "Olha, navegador, a tag `body` vai receber um grid, assim posso informar onde cada tag vai ficar". Mas, afinal, onde estamos dizendo e informando o posicionamento de cada tag ?
## Posicionando nossas tags
Para posicionar nossas tags, devemos praticamente "desenhar" no CSS, onde elas estarão:
```css
body {
	display: grid;
	grid-template-areas:
	"header header header"
	"aside main main"
	"footer footer footer";
}
```

## Entendendo o Template Areas
Com a propriedade `css-template-areas` "desenhamos" nosso _layout_, assim conseguimos informar como e por quais elementos ele vai ser composto. O _header_ e _footer_ foram declarados três vezes, porque estamos trabalhando com um layout de três colunas, isso deve-se ao fato da segunda linha do nosso _template_.

- "header header header": Aqui estamos dizendo que a primeira linha vai ser composta por um _header_.
- "aside main main": Aqui estamos dizendo que a segunda linha vai ser composta por um _aside_ na esquerda e por um main na direita.
- "footer footer footer": Aqui estamos dizendo que a terceira e última linha vai ser composta por um _footer_.

## Dizendo aos elementos onde devem ficar
Para dizer aos elementos onde eles devem ficar, ou seja, qual "lacuna" é de cada um, precisamos ir em um por um deles e informar. Repare  que o nome informado na propriedade `grid-area` deve ser **exatamente** igual aos nomes dados no `grid-template-areas`.
```css
.o-header {
grid-area: header;
}

.o-aside {
grid-area: aside;
}

.o-main {
grid-area: main;
}

.o-footer {
grid-area: footer;
}
```

# Propriedades e Atributos
### Display: grid e inline-grid
A propriedade `display` é fundamental para a criação de um Grid Layout em CSS, pois define se um elemento HTML será um container de grid ou um item dentro desse grid.

1. **`display: grid;`**: Quando você define `display: grid;` em um elemento HTML, ele se torna um container de grade. Isso significa que ele será responsável por organizar seus filhos diretos em uma grade bidimensional. Qualquer elemento que seja um filho direto desse container se tornará automaticamente um item de grade, a menos que sua propriedade `display` seja explicitamente definida como outra coisa.
```css
.grid-container {
display: grid;}
```

1. **`display: inline-grid;`**: Semelhante ao `display: grid;`, quando você define `display: inline-grid;`, o elemento HTML se torna um container de grid, mas ele é tratado como um elemento inline em relação a outros elementos em linha. Isso significa que ele fluirá como um elemento de linha normal no contexto de um texto, mas ainda criará uma grade para seus filhos diretos.
```css
.grid-container {
display: inline-grid;}
```

### container: grid-template-columns
A propriedade `grid-template-columns` é uma parte essencial do Grid Layout do CSS, permitindo que você defina a estrutura das colunas em um grid. Vamos explorar mais detalhes sobre a propriedade `grid-template-columns`:

1. **Definindo a Estrutura de Colunas:**
   Ao usar a propriedade `grid-template-columns`, você pode definir a estrutura das colunas em um container de grid. Existem várias maneiras de especificar as colunas:

   - **Valores Fixos:** Você pode definir o tamanho de uma coluna usando valores fixos, como pixels (`px`) ou centímetros (`cm`).
- 
```css
.grid-container {
display: grid;
grid-template-columns: 100px 200px 300px;}
```

   - **Valores Flexíveis:** Você também pode usar valores flexíveis, como frações (`fr`), para criar colunas que se ajustam automaticamente ao espaço disponível.
```css
.grid-container {
display: grid;
grid-template-columns: 1fr 2fr 3fr;}
```

   - **Valores Automáticos:** Você pode usar o valor `auto` para que uma coluna tenha o tamanho do conteúdo dentro dela.
```css
.grid-container {
display: grid;
grid-template-columns: auto auto auto;}
```

   - **Repetição de Padrões:** A função `repeat(n, value)` permite criar um padrão repetido de colunas.
```css
.grid-container {
display: grid;
grid-template-columns: repeat(3, 1fr);}
```

### container: grid-template-rows
A propriedade `grid-template-rows` é outra parte fundamental do Grid Layout do CSS, permitindo que você defina a estrutura das linhas em um grid. Vamos explorar mais detalhes sobre a propriedade `grid-template-rows`:

1. **Definindo a Estrutura de Linhas:**
   Assim como a propriedade `grid-template-columns` define a estrutura das colunas, a `grid-template-rows` define a estrutura das linhas em um container de grid. Você pode especificar as linhas de várias maneiras:

   - **Valores Fixos:** Defina o tamanho de uma linha com valores fixos, como pixels (`px`) ou centímetros (`cm`).
```css
.grid-container {
display: grid;
grid-template-rows: 100px 200px 300px;}
```

   - **Valores Flexíveis:** Use valores flexíveis, como frações (`fr`), para criar linhas que se ajustam automaticamente ao espaço disponível.
```css
.grid-container {
display: grid;
grid-template-rows: 1fr 2fr 3fr;}
```

   - **Valores Automáticos:** O valor `auto` permite que uma linha tenha o tamanho do conteúdo dentro dela.
 ```css
.grid-container {
display: grid;
grid-template-rows: auto auto auto;}
```

   - **Repetição de Padrões:** Use a função `repeat(n, value)` para criar um padrão repetido de linhas.
```css
.grid-container {
display: grid;
grid-template-rows: repeat(3, 1fr);}
```
### container: grid gap
As propriedades `gap`, `column-gap` e `row-gap` são usadas para definir espaçamentos entre as células de uma grade, controlando o espaçamento entre colunas e linhas. Vamos explorar cada uma delas:

1.**`gap`:**
   A propriedade `gap` é uma propriedade abreviada que permite definir o espaçamento entre as colunas e as linhas de uma grade em um único valor. Você pode especificar dois valores separados por um espaço para controlar o espaçamento entre colunas e linhas, respectivamente.
```css
.grid-container {
display: grid;
gap: 10px 20px; /* Espaçamento de 10px entre linhas e 20px entre colunas */}
```

2. **`column-gap`:**
   A propriedade `column-gap` é usada para definir o espaçamento apenas entre as colunas de uma grade. Ela permite controlar o espaçamento horizontal entre as colunas.
```css
.grid-container {
display: grid;
column-gap: 20px; /* Espaçamento de 20px entre as colunas */}
```

3. **`row-gap`:**
   A propriedade `row-gap` é usada para definir o espaçamento apenas entre as linhas de uma grade. Ela permite controlar o espaçamento vertical entre as linhas.
```css
.grid-container {
display: grid;
row-gap: 10px; /* Espaçamento de 10px entre as linhas */}
```

### items: grid lines
As "grid lines" são as linhas imaginárias que dividem uma grade de CSS em colunas e linhas. Essas linhas são usadas para posicionar elementos dentro do grid e são fundamentais para o sistema de layout do Grid CSS. Aqui estão alguns conceitos importantes relacionados às "grid lines":

1. **Column Lines (Linhas de Coluna):** São as linhas que se estendem verticalmente entre as colunas de uma grade. Elas dividem a grade em colunas individuais. As colunas são numeradas a partir de 1, começando da esquerda para a direita.

2. **Row Lines (Linhas de Linha):** São as linhas que se estendem horizontalmente entre as linhas de uma grade. Elas dividem a grade em linhas individuais. As linhas também são numeradas a partir de 1, começando de cima para baixo.

3. **Posicionamento de Itens:** Para posicionar um elemento em um grid, você pode usar as propriedades `grid-column-start`, `grid-column-end`, `grid-row-start` e `grid-row-end`. Essas propriedades permitem que você especifique em qual linha ou coluna o item deve começar e terminar.

   Por exemplo, se você deseja posicionar um elemento na primeira coluna (coluna inicial) e fazê-lo terminar na terceira coluna (coluna final), você pode usar as propriedades `grid-column-start` e `grid-column-end`:
```css
.item1 {
	grid-column-start: 1; /* Começa na primeira coluna */
	grid-column-end: 3;   /* Termina na terceira coluna */}
```

   Essa configuração coloca o `.item1` entre as "grid lines" 1 e 3 nas colunas, ocupando duas colunas.

4. **Intervalos de Linhas:** Você também pode usar a propriedade `span` para definir um elemento para ocupar várias linhas ou colunas.
```css
.item2 {
	grid-column-start: 2;
	grid-column-end: span 2; /* Ocupa 2 colunas a partir da segunda coluna */}
```

Isso fará com que o `.item2` comece na segunda coluna e termine após ocupar mais duas colunas.

### items: grid-column, grid-row
A propriedade `grid-column` é uma propriedade do CSS que é usada para definir em qual(s) coluna(s) um item de grade será posicionado em um grid. Além disso, a propriedade `grid-row` é usada para definir em qual(s) linha(s) o item de grade será posicionado em relação às linhas do grid. Essas propriedades permitem que você especifique tanto o início quanto o fim da posição de um item em relação às colunas e linhas da grade. Aqui estão os principais conceitos relacionados às propriedades `grid-column` e `grid-row`:

1. **Definindo o Início e o Fim da Posição em Colunas:**
   - A propriedade `grid-column` permite que você defina onde um item de grade começará e onde terminará em relação às colunas do grid.

```css
.item1 {
grid-column: 1 / 5;}
```

Neste exemplo, estamos posicionando o `.item1` para iniciar na primeira coluna e terminar antes da quinta coluna. Isso significa que o item ocupará quatro colunas no total (da coluna 1 à coluna 4).

2. **Definindo o Início e o Fim da Posição em Linhas:**
   - A propriedade `grid-row` é usada para definir onde um item de grade começará e onde terminará em relação às linhas do grid.

```css
.item1 {
grid-row: 2 / 4;}
```

Neste exemplo, estamos posicionando o `.item1` para iniciar na segunda linha e terminar antes da quarta linha. Isso significa que o item ocupará duas linhas no total (da linha 2 à linha 3).

3. **Uso de "span" em Colunas e Linhas:**
   - Você pode usar a palavra-chave "span" tanto na propriedade `grid-column` quanto na `grid-row` para indicar que um item deve se estender por um certo número de colunas ou linhas a partir de um ponto de início específico.

```css
.item2 {
grid-column: 2 / span 2;
grid-row: span 3;}
```

Neste caso, o `.item2` começará na segunda coluna, se estenderá por mais duas colunas (totalizando três colunas ocupadas) e se estenderá por três linhas.

1. **Valores Abreviados:**
   - As propriedades `grid-column` e `grid-row` também podem ser abreviadas para definir tanto o início quanto o fim em uma única declaração.

```css
.item3 {
grid-column: 3 / 5; /* Início na coluna 3 e fim na coluna 5 */
grid-row: 1 / 3;    /* Início na linha 1 e fim na linha 3 */}
```

5. **Uso de Linhas Numéricas:**
   - Você pode se referir às "grid lines" por seus números para especificar o início e o fim do item em relação às colunas e linhas. Isso oferece um alto grau de controle sobre o posicionamento.

```css
.item4 {
grid-column: 1 / 3; /* Início na primeira coluna e fim na terceira coluna */
grid-row: 2 / 4;    /* Início na segunda linha e fim na quarta linha */}
```
### items: grid area
A propriedade `grid-area` é uma propriedade de atalho do CSS que permite definir, de uma só vez, tanto o início quanto o fim das posições de um item de grade em relação às linhas e colunas do grid. Ela é especialmente útil quando você deseja combinar as propriedades `grid-row-start`, `grid-column-start`, `grid-row-end` e `grid-column-end` em uma única declaração. Aqui estão os principais conceitos relacionados à propriedade `grid-area`:

1. **Uso da Propriedade `grid-area`:**
- A propriedade `grid-area` permite definir todas as informações de posicionamento em uma única declaração. Ela segue a seguinte ordem: `grid-row-start`, `grid-column-start`, `grid-row-end` e `grid-column-end`.

```css
.item1 {
grid-area: 2 / 1 / 4 / 4;}
```

Neste exemplo, estamos posicionando o `.item1` com base nos seguintes valores:
- `grid-row-start`: Início na segunda linha.
- `grid-column-start`: Início na primeira coluna.
- `grid-row-end`: Fim na quarta linha.
- `grid-column-end`: Fim na quarta coluna.

2. **Uso de "span" com `grid-area`:**
- Você também pode usar a palavra-chave "span" com a propriedade `grid-area` para definir quanto o item deve se estender em relação às linhas e colunas.

```css
.item2 {
grid-area: 3 / 2 / span 2 / span 3;}
```

Neste caso, o `.item2` começará na terceira linha e na segunda coluna, estendendo-se por mais duas linhas (totalizando três linhas ocupadas) e por mais três colunas (totalizando quatro colunas ocupadas).

3. **Uso de Valores Abreviados:**
- A propriedade `grid-area` também pode ser abreviada para definir tanto o início quanto o fim em uma única declaração.

```css
.item3 {
grid-area: 2 / 1 / 4 / 3; /* Início na segunda linha, primeira coluna; Fim na quarta linha, terceira coluna */}
```
