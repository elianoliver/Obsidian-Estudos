---
cssclasses:
  - rounded-images
---
O Flexbox, ou "Flexible Box Layout," é um modelo de layout em CSS que permite criar designs complexos e responsivos com facilidade, especialmente quando se trata de organizar elementos em um contêiner. O Flexbox é uma ferramenta poderosa para desenvolvedores web, pois simplifica a tarefa de distribuir espaços e alinhar elementos dentro de um contêiner. Uma das propriedades-chave do Flexbox é `flex-direction`.

Quando utilizamos o _Flexbox_, é muito importante saber quais propriedades são declaradas no elemento-pai (por exemplo, uma `div` que irá conter os elementos a serem alinhados) e quais serão declaradas nos elementos-filhos. 

## Sumário
#### Propriedades para o elemento pai
- [[#A Propriedade `flex-direction`]]
- [[#A Propriedade `justify-content`]]
- [[#A Propriedade `flex-wrap`]]
- [[#A Propriedade `flex-flow`]]
- [[#A Propriedade `align-items`]]
- [[#A Propriedade `align-content`]]
#### Propriedades para o elemento filho
- [[#A Propriedade `order`]]
- [[#A Propriedade `flex-grow`]]
- [[#A Propriedade `flex-shrink`]]
- [[#A Propriedade `flex-basis`]]
- [[#A Propriedade `flex`]]
- [[#A Propriedade `align-self`]]


## A Propriedade `flex-direction`
A propriedade `flex-direction` é usada para definir a direção principal ao longo da qual os elementos flexíveis (itens) serão dispostos dentro de um contêiner flexível (pai). Existem quatro valores possíveis para `flex-direction`, cada um afetando a organização dos itens de maneira diferente:

![[flex-direction.svg]]

- `row`: Este é o valor padrão. Os itens são organizados na direção horizontal, da esquerda para a direita. Isso significa que o eixo principal é horizontal e o eixo cruzado é vertical.

- `row-reverse`: Semelhante a `row`, mas os itens são organizados na direção oposta, da direita para a esquerda.

- `column`: Os itens são organizados na direção vertical, de cima para baixo. Isso significa que o eixo principal é vertical e o eixo cruzado é horizontal.

- `column-reverse`: Semelhante a `column`, mas os itens são organizados na direção oposta, de baixo para cima.

### Exemplo de Uso
Vamos ver um exemplo simples de como a propriedade `flex-direction` pode ser aplicada em um contêiner flexível:

```css
.container {
  display: flex;
  flex-direction: row; /* ou column, row-reverse, column-reverse */
}
```

Neste exemplo, estamos criando um contêiner com a classe `.container` e aplicando `display: flex;` para habilitar o Flexbox. A propriedade `flex-direction` é usada para definir a direção dos itens dentro deste contêiner. Dependendo do valor escolhido, os itens serão organizados horizontalmente (`row` ou `row-reverse`) ou verticalmente (`column` ou `column-reverse`).

---

## A Propriedade `justify-content`
A propriedade `justify-content` é uma das propriedades mais importantes do modelo de layout Flexbox em CSS. Ela é usada para controlar o alinhamento dos itens flexíveis (elementos) ao longo do eixo principal do contêiner flexível (pai). A propriedade `justify-content` permite distribuir o espaço disponível de várias maneiras, proporcionando um controle preciso sobre o posicionamento dos itens.
### Valores
1. `flex-start`: Este é o valor padrão. Os itens são alinhados no início do eixo principal. No caso de `flex-direction: row`, os itens se alinham à esquerda; para `flex-direction: column`, os itens se alinham na parte superior.
   ![[justify-content-flex-start.png|center|500]]
   
1. `flex-end`: Os itens são alinhados no final do eixo principal. No caso de `flex-direction: row`, os itens se alinham à direita; para `flex-direction: column`, os itens se alinham na parte inferior.
   ![[justify-content-flex-end.png|center|500]]
   
1. `center`: Os itens são centralizados ao longo do eixo principal. Eles são distribuídos de forma igual nas duas direções, criando um layout centrado.
   ![[justify-content-center.png|center|500]]
   
1. `space-between`: Os itens são espaçados uniformemente ao longo do eixo principal. O primeiro item começa no início do contêiner, o último item termina no final do contêiner, e o espaço restante é distribuído igualmente entre os itens.
   ![[justify-content-space-between.png|center|500]]
   
1. `space-around`: Os itens são espaçados uniformemente ao longo do eixo principal e também têm espaço adicional antes do primeiro item e após o último item.
   ![[justify-content-space-around.png|center|500]]
   
1. `space-evenly`: Os itens são espaçados uniformemente ao longo do eixo principal, incluindo espaço igual antes do primeiro item e após o último item.
   ![[justify-content-space-evenly.png|center|500]]
   
### Exemplo de Uso
Aqui está um exemplo de como a propriedade `justify-content` pode ser aplicada em um contêiner Flexbox:

```css
.container {
  display: flex;
  justify-content: center; /* ou outro valor de sua escolha */
}
```

Neste exemplo, estamos criando um contêiner com a classe `.container` e aplicando `display: flex;` para habilitar o Flexbox. A propriedade `justify-content` é usada para centralizar os itens ao longo do eixo principal. Dependendo do valor escolhido (como `center`, `flex-start`, ou outro), os itens serão alinhados de acordo com a direção especificada.

---


## A Propriedade `flex-wrap`
A propriedade `flex-wrap` é outra propriedade importante do modelo de layout Flexbox em CSS. Ela controla como os itens flexíveis (elementos) se comportam quando não há espaço suficiente no contêiner flexível (pai) para acomodá-los ao longo do eixo principal. A propriedade `flex-wrap` permite que você decida se os itens devem ser quebrados em várias linhas ou se devem permanecer em uma única linha.
![[flex-wrap.png.png|center|500]]
### Valores
A propriedade `flex-wrap` possui três valores possíveis:

1. `nowrap` (valor padrão): Isso significa que os itens flexíveis não serão quebrados em várias linhas, mesmo que não haja espaço suficiente para acomodá-los ao longo do eixo principal. Eles se sobreporão ou podem estender além dos limites do contêiner se necessário.

2. `wrap`: Os itens flexíveis serão quebrados em várias linhas quando não houver espaço suficiente ao longo do eixo principal. Isso permite que os itens se ajustem a uma nova linha, mantendo a ordem original.

3. `wrap-reverse`: Semelhante a `wrap`, mas os itens são quebrados em várias linhas em ordem reversa. Isso significa que o último item da ordem original será o primeiro na nova linha e vice-versa.

### Exemplo de Uso
Aqui está um exemplo de como a propriedade `flex-wrap` pode ser aplicada em um contêiner Flexbox:

```css
.container {
  display: flex;
  flex-wrap: wrap; /* ou nowrap ou wrap-reverse */
}
```

Neste exemplo, estamos criando um contêiner com a classe `.container` e aplicando `display: flex;` para habilitar o Flexbox. A propriedade `flex-wrap` é usada para definir o comportamento de quebra dos itens flexíveis. Dependendo do valor escolhido (como `wrap`, `nowrap` ou `wrap-reverse`), os itens serão quebrados em várias linhas ou permanecerão em uma única linha conforme a disponibilidade de espaço.

---


## A Propriedade `flex-flow`

A propriedade `flex-flow` é uma propriedade abreviada no modelo de layout Flexbox em CSS. Ela é usada para definir simultaneamente duas outras propriedades importantes: `flex-direction` e `flex-wrap`. Isso permite que você especifique a direção de layout e o comportamento de quebra dos itens flexíveis em um único lugar.

### Sintaxe
A sintaxe da propriedade `flex-flow` é a seguinte:

```css
.container {
  flex-flow: <flex-direction> <flex-wrap>;
}
```

Onde `<flex-direction>` é um valor que define a direção principal do layout (como `row`, `column`, `row-reverse`, `column-reverse`), e `<flex-wrap>` é um valor que define o comportamento de quebra dos itens (como `nowrap`, `wrap`, `wrap-reverse`).

### Exemplo de Uso
Aqui está um exemplo de como a propriedade `flex-flow` pode ser aplicada em um contêiner Flexbox:

```css
.container {
  display: flex;
  flex-flow: row wrap; /* ou outra combinação de valores */
}
```

Neste exemplo, estamos criando um contêiner com a classe `.container` e aplicando `display: flex;` para habilitar o Flexbox. A propriedade `flex-flow` está sendo usada para definir a direção do layout como `row` (itens dispostos horizontalmente) e o comportamento de quebra como `wrap` (itens quebram em várias linhas quando não há espaço suficiente).

### Vantagens da Propriedade `flex-flow`
A principal vantagem da propriedade `flex-flow` é a conveniência, pois permite definir a direção do layout e o comportamento de quebra dos itens em uma única declaração, tornando o código mais limpo e fácil de ler. Além disso, quando você precisa atualizar o layout, basta modificar essa única propriedade em vez de alterar duas propriedades separadas (`flex-direction` e `flex-wrap`).

---




## A Propriedade `align-items`
A propriedade `align-items` é uma das propriedades-chave do modelo de layout Flexbox em CSS. Ela é usada para controlar o alinhamento vertical dos itens flexíveis (elementos) dentro de um contêiner flexível (pai). A propriedade `align-items` permite que você ajuste a posição dos itens ao longo do eixo cruzado do contêiner.

### Valores
A propriedade `align-items` possui vários valores possíveis, cada um com um comportamento específico:

1. `flex-start`: Este é o valor padrão. Os itens são alinhados no início do eixo cruzado. No caso de `flex-direction: row`, os itens são alinhados no topo; para `flex-direction: column`, os itens são alinhados à esquerda.
   ![[align-items-flex-start.png|center]]
2. `flex-end`: Os itens são alinhados no final do eixo cruzado. No caso de `flex-direction: row`, os itens são alinhados na parte inferior; para `flex-direction: column`, os itens são alinhados à direita.
   ![[align-items-flex-end.png|center]]
3. `center`: Os itens são centralizados ao longo do eixo cruzado. Eles são distribuídos de forma igual nas duas direções, criando um alinhamento vertical centralizado.
   ![[align-items-center.png|center]]
4. `baseline`: Os itens são alinhados com base na linha de base do texto. Isso é útil quando você tem itens de texto e deseja alinhar seus textos de maneira consistente.
   ![[align-items-baseline.png|center]]
5. `stretch`: Este valor faz com que os itens se estiquem para preencher o contêiner no eixo cruzado. Eles ocuparão todo o espaço disponível verticalmente.
   ![[align-items-strech.png|center]]
### Exemplo de Uso
Aqui está um exemplo de como a propriedade `align-items` pode ser aplicada em um contêiner Flexbox:

```css
.container {
  display: flex;
  align-items: center; /* ou outro valor de sua escolha */
}
```

Neste exemplo, estamos criando um contêiner com a classe `.container` e aplicando `display: flex;` para habilitar o Flexbox. A propriedade `align-items` está sendo usada para centralizar verticalmente os itens dentro do contêiner. Dependendo do valor escolhido (como `center`, `flex-start`, ou outro), os itens serão alinhados verticalmente de acordo com a direção especificada.

## A Propriedade `align-content`

A propriedade `align-content` é usada no modelo de layout Flexbox em CSS para controlar o alinhamento vertical de um grupo de itens flexíveis dentro de um contêiner flexível quando há espaço extra no eixo cruzado. Ao contrário da propriedade `align-items`, que controla o alinhamento dos itens individualmente, `align-content` afeta o alinhamento de todo o conjunto de itens dentro do contêiner.

### Valores
A propriedade `align-content` possui vários valores possíveis, cada um com um comportamento específico:

1. `flex-start`: Este é o valor padrão. O conjunto de itens é alinhado no início do eixo cruzado.
   ![[align-content-flex-start.png|center]]
2. `flex-end`: O conjunto de itens é alinhado no final do eixo cruzado.
![[align-content-flex-end.png|center]]
3. `center`: O conjunto de itens é centralizado verticalmente ao longo do eixo cruzado.
![[align-content-center.png|center]]
4. `space-between`: Os itens são distribuídos uniformemente ao longo do eixo cruzado, com espaço entre eles e nos limites do contêiner.
![[align-content-space-between.png|center]]
5. `space-around`: Os itens são distribuídos uniformemente ao longo do eixo cruzado, com espaço igual antes do primeiro item, entre os itens e após o último item.
![[align-content-space-around.png|center]]
6. `stretch`: Este valor faz com que o conjunto de itens se estique para preencher todo o espaço disponível no eixo cruzado.
![[align-content-stretch.png|center]]
### Exemplo de Uso
Aqui está um exemplo de como a propriedade `align-content` pode ser aplicada em um contêiner Flexbox:

```css
.container {
  display: flex;
  flex-wrap: wrap;
  align-content: center; /* ou outro valor de sua escolha */
}
```

Neste exemplo, estamos criando um contêiner com a classe `.container` e aplicando `display: flex;` para habilitar o Flexbox. A propriedade `flex-wrap` está sendo usada para permitir a quebra de itens em várias linhas, se necessário. A propriedade `align-content` é usada para centralizar verticalmente todo o conjunto de itens dentro do contêiner.

---


## A Propriedade `order`
O atributo `order` é usado para controlar a ordem em que os itens flexíveis são exibidos dentro de um contêiner flexível. Ele permite que você reorganize visualmente os elementos sem alterar a estrutura real do HTML. O valor padrão para `order` é 0, e os itens com valores menores aparecem primeiro. Valores negativos são permitidos, tornando possível a reorganização completa dos itens.
![[flex-item-order.png|center|450]]

Aqui está um exemplo simples:

```css
.flex-container {
  display: flex;
}

.flex-item1 {
  order: 2;
}

.flex-item2 {
  order: 1;
}

.flex-item3 {
  order: 3;
}
```

Neste exemplo, `flex-item2` será exibido antes de `flex-item1`, apesar de `flex-item1` aparecer antes de `flex-item2` no código HTML. O `order` permite uma flexibilidade significativa na disposição dos itens flexíveis.

---



## A Propriedade `flex-grow`
A propriedade `flex-grow` é uma das propriedades principais do Flexbox, que permite controlar como os itens flexíveis dentro de um contêiner se expandem para ocupar o espaço disponível. Ela determina a quantidade de espaço extra que um item flexível pode ocupar em relação aos outros itens quando há espaço extra no contêiner.
![[flex-grow.png|center|500]]
### Utilização Básica
A propriedade `flex-grow` aceita valores numéricos, que representam a proporção em que os itens flexíveis crescem em relação aos outros itens. O valor padrão é 0, o que significa que o item flexível não crescerá automaticamente para preencher o espaço adicional.

Aqui está um exemplo simples:

```css
.flex-container {
  display: flex;
}

.flex-item1 {
  flex-grow: 1;
}

.flex-item2 {
  flex-grow: 2;
}

.flex-item3 {
  flex-grow: 1;
}
```

Neste exemplo, `flex-item2` tem um `flex-grow` de 2, enquanto `flex-item1` e `flex-item3` têm um `flex-grow` de 1 cada. Isso significa que, quando há espaço extra disponível no contêiner, `flex-item2` crescerá em uma taxa duas vezes maior em relação aos outros itens. Isso permite criar layouts onde alguns itens são mais flexíveis do que outros em termos de expansão.

### Percentagens e Valores Não-Inteiros
Além de valores inteiros, a propriedade `flex-grow` também aceita valores decimais e porcentagens. Isso permite uma granularidade maior no controle da expansão dos itens flexíveis.

```css
.flex-item1 {
  flex-grow: 0.5; /* Cresce a metade da taxa padrão */
}

.flex-item2 {
  flex-grow: 1.5; /* Cresce uma vez e meia mais rápido que o padrão */
}

.flex-item3 {
  flex-grow: 1; /* Cresce na taxa padrão */
}
```


## A Propriedade `flex-shrink`
A propriedade `flex-shrink` é uma das propriedades fundamentais do Flexbox, usada para controlar como os itens flexíveis dentro de um contêiner encolhem quando o espaço disponível é insuficiente para acomodá-los completamente. Essa propriedade permite que você especifique como os itens flexíveis devem diminuir de tamanho quando necessário para evitar que ocorram estouros de layout.

### Utilização Básica
A propriedade `flex-shrink` aceita valores numéricos, onde cada valor representa a proporção em que um item flexível deve encolher em relação aos outros quando o espaço é limitado. O valor padrão é 1, o que significa que todos os itens flexíveis encolherão na mesma proporção.

Aqui está um exemplo simples:

```css
.flex-container {
  display: flex;
  width: 300px; /* Um espaço limitado para os itens */
}

.flex-item1 {
	  flex-shrink: 2;
  /* Este item encolherá duas vezes mais rápido que os outros */
}

.flex-item2 {
  flex-shrink: 1;
  /* Este item encolherá na taxa padrão (mesma proporção que os outros com flex-shrink: 1) */
}

.flex-item3 {
  flex-shrink: 3;
  /* Este item encolherá três vezes mais rápido que os outros */
}
```

Neste exemplo, quando o espaço disponível no contêiner é limitado a 300 pixels, `flex-item3` encolherá três vezes mais rápido que os outros itens, `flex-item1` encolherá duas vezes mais rápido que os outros e `flex-item2` encolherá na taxa padrão.

### Limitações de Encolhimento
É importante observar que a propriedade `flex-shrink` não permite que os itens flexíveis encolham indefinidamente. Ela não pode reduzir um item flexível abaixo do tamanho mínimo especificado por seu conteúdo ou pela propriedade `min-width` ou `min-height`.
## A Propriedade `flex-basis`
A propriedade `flex-basis` é uma das propriedades chave do Flexbox, usada para definir o tamanho base dos itens flexíveis em um contêiner flexível. Ela controla o tamanho inicial dos itens antes de qualquer expansão ou encolhimento, permitindo que você estabeleça o espaço ocupado por cada item antes que o espaço extra seja distribuído.

### Utilização Básica
A propriedade `flex-basis` aceita valores numéricos, porcentagens ou unidades de medida como `px`, `em`, `rem`, etc., para especificar o tamanho base de um item flexível. Por padrão, `flex-basis` é definido como `auto`, o que significa que o tamanho base é determinado pelo conteúdo do item.

Aqui está um exemplo simples:

```css
.flex-container {
  display: flex;
}

.flex-item1 {
  flex-basis: 100px;
  /* Este item terá um tamanho base de 100 pixels */
}

.flex-item2 {
  flex-basis: 20%;
  /* Este item terá um tamanho base de 20% do espaço disponível no contêiner */
}
```

Neste exemplo, `flex-item1` terá um tamanho base de 100 pixels, enquanto `flex-item2` terá um tamanho base de 20% do espaço disponível no contêiner.

### Combinação com `flex-grow` e `flex-shrink`
A propriedade `flex-basis` é frequentemente usada em conjunto com `flex-grow` e `flex-shrink` para criar layouts flexíveis mais complexos. Quando você define `flex-basis`, está especificando o tamanho base a partir do qual os itens podem expandir ou encolher, dependendo das outras propriedades.

Por exemplo:

```css
.flex-container {
  display: flex;
}

.flex-item1 {
  flex-basis: 100px;
  flex-grow: 1;
  /* Este item crescerá a partir do tamanho base de 100 pixels */
}

.flex-item2 {
  flex-basis: 20%;
  flex-shrink: 2;
  /* Este item encolherá a partir do tamanho base de 20% em dobro da taxa dos outros itens */
}
```

## A Propriedade `flex`
A propriedade `flex` é uma propriedade abreviada em Flexbox que combina três propriedades principais: `flex-grow`, `flex-shrink`, e `flex-basis`. Ela é usada para controlar o comportamento de crescimento, encolhimento e tamanho base dos itens flexíveis em um contêiner flexível de uma só vez, proporcionando um controle flexível e compacto sobre o layout.

### Sintaxe
A propriedade `flex` tem a seguinte sintaxe:

```css
flex: <flex-grow> <flex-shrink> <flex-basis>;
```

- `<flex-grow>` especifica a proporção em que o item flexível deve crescer em relação aos outros quando há espaço disponível.
- `<flex-shrink>` especifica a proporção em que o item flexível deve encolher em relação aos outros quando o espaço é limitado.
- `<flex-basis>` especifica o tamanho base do item flexível antes de qualquer expansão ou encolhimento.

Aqui está um exemplo:

```css
.flex-item {
  flex: 2 1 200px;
}
```

Neste exemplo, o item flexível `flex-item` possui as seguintes configurações:
- `flex-grow`: 2 (crescerá duas vezes mais rápido que os outros itens quando houver espaço extra).
- `flex-shrink`: 1 (encolherá na mesma proporção que os outros itens quando o espaço for limitado).
- `flex-basis`: 200px (tamanho base de 200 pixels antes de qualquer expansão ou encolhimento).

### Uso Conveniente
A propriedade `flex` é especialmente útil quando você deseja definir todas as três propriedades relacionadas de um item flexível em uma única linha de código. Isso torna o código mais limpo e legível, reduzindo a necessidade de repetição.

Além disso, você pode usar a propriedade `flex` com valores abreviados, como `auto`, `none`, ou `initial`, quando apropriado.

```css
.flex-item {
  flex: auto; /* Crescerá/encolherá de acordo com o espaço disponível e tamanho base padrão */
}

.flex-item2 {
  flex: none; /* Não crescerá/encolherá, manterá o tamanho base padrão */
}
```
# A Propriedade `align-self`
A propriedade `align-self` é uma propriedade CSS usada para controlar a alinhamento vertical de um item flexível (um filho de um contêiner flexível) dentro de um contêiner flexível. Ela permite que você ajuste individualmente o alinhamento vertical de um item em relação aos outros itens no mesmo contêiner, independentemente das configurações de alinhamento definidas para o contêiner pai.
![[align-self.png|center|500]]

### Utilização Básica
A propriedade `align-self` aceita uma variedade de valores que determinam como um item flexível é alinhado verticalmente dentro do contêiner flexível. Alguns dos valores mais comuns incluem:

- `flex-start`: Alinha o item no início do eixo vertical do contêiner (parte superior).
- `flex-end`: Alinha o item no final do eixo vertical do contêiner (parte inferior).
- `center`: Alinha o item verticalmente no centro do contêiner.
- `baseline`: Alinha o item de acordo com a linha de base dos textos dos outros itens.
- `stretch`: Estica o item verticalmente para ocupar todo o espaço disponível (valor padrão).

Aqui está um exemplo de uso básico:

```css
.flex-container {
  display: flex;
}

.flex-item1 {
  align-self: flex-start;
  /* Este item será alinhado no topo do contêiner */
}

.flex-item2 {
  align-self: center;
  /* Este item será alinhado no centro do contêiner */
}

.flex-item3 {
  align-self: flex-end;
  /* Este item será alinhado na parte inferior do contêiner */
}
```

### Uso em Itens Individuais
A propriedade `align-self` é aplicada a itens individuais dentro do contêiner flexível, o que significa que você pode controlar o alinhamento vertical de cada item separadamente. Isso é particularmente útil quando você deseja que alguns itens tenham um alinhamento diferente dos outros.

## Combinando com `align-items`

A propriedade `align-self` substitui a configuração de alinhamento vertical definida para um item pelo valor da propriedade `align-items` do contêiner pai. Isso permite que você controle o alinhamento vertical de um item individualmente, mesmo quando o contêiner pai tem uma configuração global de alinhamento.