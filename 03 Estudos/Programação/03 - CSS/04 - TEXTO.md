Neste exemplo, exploraremos diferentes propriedades de estilo de texto usando CSS. Vamos analisar cada propriedade com exemplos práticos:

## 1. `text-align`
A propriedade `text-align` define o alinhamento horizontal do texto dentro de um elemento. Os valores possíveis são:
- `left`: Alinha o texto à esquerda.
- `right`: Alinha o texto à direita.
- `center`: Centraliza o texto horizontalmente.
- `justify`: Justifica o texto, preenchendo o espaço horizontalmente.

Exemplo:
```css
h1 {
    text-align: center; /* Alinha o texto ao centro */
}
```

## 2. `text-decoration`

A propriedade `text-decoration` aplica decorações ao texto. Alguns valores que podem ser usados:
- `none`: Nenhuma decoração.
- `underline`: Sublinha o texto.
- `overline`: Coloca uma linha acima do texto.
- `line-through`: Adiciona uma linha no meio do texto.
- `wavy`: Torna a decoração ondulada.

Exemplo:
```css
h1 {
    text-decoration: underline red wavy 1px; /* Sublinha, vermelho, ondulado, espessura 1px */
}
```

## 3. `text-transform`

A propriedade `text-transform` modifica a capitalização do texto. Valores possíveis:
- `uppercase`: Transforma o texto em maiúsculas.
- `lowercase`: Transforma o texto em minúsculas.
- `capitalize`: Coloca a primeira letra de cada palavra em maiúscula.

Exemplo:
```css
h1 {
    text-transform: capitalize; /* Primeira letra de cada palavra em maiúscula */
}
```

## 4. `text-shadow`

A propriedade `text-shadow` adiciona sombras ao texto. Você pode especificar a posição horizontal, a posição vertical, o desfoque e a cor da sombra.

Exemplo:
```css
h2 {
    text-shadow: 0 0 3px #ff0000, 0 0 5px #0000ff; /* Duas sombras: vermelha e azul */
}
```

## 5. `text-indent`

A propriedade `text-indent` define a indentação da primeira linha do bloco de texto.

Exemplo:
```css
p {
    text-indent: 30%; /* Indenta a primeira linha em 30% da largura do bloco */
}
```

## 6. `letter-spacing` e `word-spacing`

Essas propriedades controlam o espaçamento entre letras e palavras, respectivamente.

Exemplo:
```css
p {
    letter-spacing: 3px; /* Espaçamento entre letras de 3 pixels */
    word-spacing: 15px; /* Espaçamento entre palavras de 15 pixels */
}
```

## 7. `line-height`

A propriedade `line-height` controla a altura da linha, afetando o espaçamento vertical entre as linhas de texto.

Exemplo:
```css
p {
    line-height: 20px; /* Altura da linha de 20 pixels */
}
```

## 8. `white-space`

A propriedade `white-space` controla o tratamento de espaço em branco no texto.

Exemplo:
```css
p {
    white-space: nowrap; /* Impede a quebra de linha */
}
```
