As tabelas desempenham um papel essencial na exibição e organização de dados tabulares em páginas da web. O CSS oferece uma variedade de propriedades para personalizar a aparência e o comportamento das tabelas. Vamos explorar os principais atributos e seus possíveis valores:

## `empty-cells`

A propriedade `empty-cells` é usada para definir como as células vazias (sem conteúdo) são exibidas em uma tabela. Os valores possíveis incluem:

- `show`: Exibe as células vazias com bordas e espaços.
- `hide`: Oculta as células vazias, removendo as bordas e espaços.

Exemplo:
```css
table {
    empty-cells: hide; /* Oculta células vazias */
}
```

## `table-layout`

A propriedade `table-layout` é usada para controlar a maneira como as células de uma tabela são dimensionadas e distribuídas. Os valores possíveis incluem:

- `auto`: As células têm seu tamanho definido pelo conteúdo. A largura da coluna é ajustada conforme o conteúdo.
- `fixed`: As células têm um tamanho fixo, definido por larguras de coluna especificadas. O conteúdo pode ser truncado ou distribuído para caber nas células.

Exemplo:
```css
table {
    table-layout: fixed; /* Define um layout de tabela fixo */
}
```

## Estilo de Borda e `border-collapse`

Para personalizar as bordas de uma tabela e suas células, você pode usar propriedades como `border-style`, `border-top-style` e outras. A propriedade `border-collapse` é usada para controlar o espaçamento entre as bordas das células.

Exemplo:
```css
table, th, td {
    border-style: solid; /* Define o estilo da borda para sólido */
    border-top-style: dotted; /* Define o estilo da borda superior como pontilhado */
    border-collapse: collapse; /* Remove o espaço entre as bordas das células */
}
```

## Estilização de Cabeçalhos e Linhas

Você pode estilizar cabeçalhos (`th`) e linhas (`tr`) individualmente. Isso inclui ajustar preenchimento, cor de fundo e cores de texto.

Exemplo:
```css
th {
    padding-left: 25px;
    padding-right: 25px;
    line-height: 25px;
    background-color: black;
    color: antiquewhite;
    border-color: brown;
}

tr {
    background-color: chartreuse; /* Cor de fundo das linhas */
}
```

## Alternância de Cores e Efeitos de Hover

Você pode alternar cores de fundo entre linhas usando pseudoclasses como `:nth-child(even)` e `:nth-child(odd)`. Além disso, você pode adicionar efeitos de hover para destacar células quando o mouse passar sobre elas.

Exemplo:
```css
td:hover {
    background-color: thistle; /* Cor de fundo quando hover */
}

tr:nth-child(odd) {
    background-color: bisque; /* Cor de fundo das linhas ímpares */
}
```

## Personalização Adicional

Você pode ajustar outras propriedades, como `height`, `width`, `text-align` e `vertical-align`, para controlar o dimensionamento e o alinhamento das células da tabela.

```css
td {
    height: 50px; /* Altura das células */
    width: 200px; /* Largura das células */
    text-align: center; /* Alinhamento horizontal */
    vertical-align: top; /* Alinhamento vertical */
}
```

## Conclusão

O CSS oferece uma variedade de propriedades para personalizar a aparência e o comportamento das tabelas em páginas web. Através do uso de propriedades como `empty-cells`, `table-layout`, `border-collapse`, `border-style`, `background-color` e pseudoclasses, você pode criar tabelas visualmente atraentes e interativas. Essas personalizações podem melhorar significativamente a apresentação e a legibilidade de dados tabulares em seus projetos.