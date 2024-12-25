No CSS, a escolha da fonte pode desempenhar um papel significativo no design e na legibilidade do seu site. Vamos explorar como definir estilos de fontes usando diferentes propriedades CSS:

## `font-family`

A propriedade `font-family` permite especificar a fonte a ser usada para o texto. Você pode fornecer uma lista de fontes, separadas por vírgulas, para que o navegador tente carregar a primeira fonte disponível.

Exemplo:
```css
.font01 {
    font-family: 'Courier New', Courier, 'Lucida Console', monospace;
}
```

Nesse exemplo, a fonte 'Courier New' será usada se estiver disponível, caso contrário, o navegador tentará 'Courier' e, em seguida, 'Lucida Console'. O valor genérico `monospace` é usado como fallback, caso nenhuma das fontes específicas seja encontrada.

## `font-weight`

A propriedade `font-weight` define a espessura da fonte, que pode variar de `100` (mais leve) a `900` (mais pesada).

Exemplo:
```css
.font01 {
    font-weight: 800;
}
```

Neste caso, a fonte terá um peso de `800`, tornando-a bastante negrita.

## `font-style`

A propriedade `font-style` permite definir se a fonte deve ser normal (padrão) ou itálica.

Exemplo:
```css
.font01 {
    font-style: italic;
}
```

Aqui, a fonte será exibida em itálico.

## `font-variant`

A propriedade `font-variant` define se o texto deve ser exibido em maiúsculas e minúsculas normais ou em caixa alta.

Exemplo:
```css
.font01 {
    font-variant: normal;
}
```

Neste caso, o texto será exibido em maiúsculas e minúsculas normais.

## `font-size`

A propriedade `font-size` define o tamanho da fonte.

Exemplo:
```css
div {
    font-size: 25px;
}
```

Aqui, o texto dentro de um elemento `div` terá um tamanho de fonte de `25px`.

## Exemplo Completo

```css
.font04 {
    font: italic small-caps lighter 25px/30px 'Shadows Into Light', cursive;
}
```

Neste exemplo, a propriedade `font` combina várias propriedades em uma única declaração. A fonte será exibida em itálico, com letras pequenas em caixa alta, peso mais leve, tamanho de `25px`, altura de linha de `30px`, usando a fonte 'Shadows Into Light', e caso ela não esteja disponível, a fonte genérica `cursive` será usada como fallback.

Com certeza, é importante mencionar a possibilidade de importar fontes externas, como as oferecidas pelo Google Fonts. Aqui está a explicação adicionada ao texto:

## Importando Fontes Externas - Google Fonts

Além das fontes padrão, você pode importar fontes externas para seu site. Um serviço popular para isso é o Google Fonts. Ele oferece uma ampla variedade de fontes gratuitas que você pode incorporar facilmente ao seu CSS.

Exemplo de importação no `<head>` do HTML:
```html
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Roboto:wght@300&display=swap">
```

E então, você pode usar a fonte no seu CSS:
```css
.font02 {
    font-family: 'Roboto', sans-serif;
    font-weight: lighter;
}
```

Nesse exemplo, a fonte 'Roboto' é importada do Google Fonts e usada para o texto com peso mais leve.