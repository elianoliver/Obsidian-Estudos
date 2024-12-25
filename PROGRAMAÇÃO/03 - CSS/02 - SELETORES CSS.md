## Sumário
- [[#Seletores de Tipo]]
- [[#Seletores de Classe]]
- [[#Seletores de ID]]
- [[#Seletores de Descendentes]]
- [[#Seletores de Filhos Diretos]]
- [[#Seletores de Atributo]]
- [[#Seletores de Pseudo classes]]
- [[#Seletores de Pseudo elementos]]
- [[#Seletores Universais]]
- [[#Seletores de Grupo]]
- [[#General Sibling Combinator (~)]]
- [[#Adjacent Sibling Combinator (+)]]
---
Os seletores CSS são usados para selecionar elementos HTML aos quais você deseja aplicar estilos. Eles permitem que você defina regras específicas para diferentes partes do seu documento HTML. Aqui estão alguns dos seletores mais comuns:

## Seletores de Tipo
Os seletores de tipo selecionam elementos com base em seu tipo HTML. Eles correspondem a elementos HTML específicos, como `<h1>`, `<p>`, `<div>`, etc.

Exemplo:
```css
h1 {
  color: blue;
}
```

## Seletores de Classe (.)
Os seletores de classe selecionam elementos que possuem um atributo `class` correspondente. Eles são precedidos por um ponto (`.`) seguido pelo nome da classe.

Exemplo:
```css
.button {
  background-color: green;
}
```

## Seletores de ID (#)
Os seletores de ID selecionam um único elemento com base em seu atributo `id`. Eles são precedidos por um hash (`#`) seguido pelo nome do ID.

Exemplo:
```css
#header {
  font-size: 24px;
}
```

## Seletores de Descendentes ( )
Os seletores de descendentes selecionam elementos que são descendentes de um elemento específico. Eles são separados por um espaço.

Exemplo:
```css
ul li {
  list-style: disc;
}
```

## Seletores de Filhos Diretos (>)
Os seletores de filhos diretos selecionam elementos que são filhos diretos de um elemento específico. Eles são separados por um sinal de maior (`>`).

Exemplo:
```css
nav > ul {
  margin: 0;
}
```

## Seletores de Atributo ([])
Os seletores de atributo selecionam elementos com base em seus atributos ou valores de atributos.

Exemplo:
```css
input[type="text"] {
  border: 1px solid gray;
}
```

## Seletores de Pseudo-classes (:)
Os seletores de pseudo-classes selecionam elementos em um estado específico, como `:hover`, `:active`, `:focus`, etc.

Exemplo:
```css
a:hover {
  color: red;
}
```

## Seletores de Pseudo-elementos (::)
Os seletores de pseudo-elementos selecionam partes específicas de um elemento, como `::before` e `::after`, para adicionar estilos.

Exemplo:
```css
p::first-line {
  font-weight: bold;
}
```

## Seletores Universais (`*`)
Os seletores universais selecionam todos os elementos no documento.

Exemplo:
```css
* {
  margin: 0;
  padding: 0;
}
```

## Seletores de Grupo (,)
Os seletores de grupo permitem agrupar seletores para aplicar as mesmas regras a vários elementos.

Exemplo:
```css
h2, h3, h4 {
  font-family: "Arial", sans-serif;
}
```

## General Sibling Combinator (~)
O seletor "General sibling combinator" (`~`) seleciona todos os elementos irmãos que compartilham o mesmo ancestral e vêm após o elemento de referência, não importando a quantidade de elementos entre eles.

Exemplo:
```css
p ~ span {
  color: red;
}
```
Nesse exemplo, todos os elementos `<span>` que são irmãos de elementos `<p>` (ou seja, têm o mesmo pai) e vêm após os elementos `<p>` terão a cor vermelha aplicada.

## Adjacent Sibling Combinator (+)
O seletor "Adjacent sibling combinator" (`+`) seleciona o elemento irmão imediatamente seguinte que compartilha o mesmo ancestral com o elemento de referência.

Exemplo:
```css
h2 + p {
  font-style: italic;
}
```
Nesse exemplo, o elemento `<p>` imediatamente após um elemento `<h2>` terá o estilo de fonte itálico aplicado.