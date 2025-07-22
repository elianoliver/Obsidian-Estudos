## Sumário
- [[#Estrutura Básica]]
- [[#Títulos e Parágrafos]]
- [[#Formatação em HTML]]
- [[#Citações e Elementos de Citação]]
- [[#Listas]]
- [[#Imagens e Links]]
- [[#Caminhos]]
## Estrutura Básica
```html
<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <link rel="icon" type="image/x-icon" href="../000-Exercícios/assets/rocket.gif">
</head>

<body>
    <!-- Seu conteúdo HTML aqui -->
</body>
</html>
```

- **Explicação:** A estrutura básica de um documento HTML contém as tags `<html>`, `<head>` e `<body>`. A tag `<html>` envolve todo o conteúdo, enquanto `<head>` contém metadados do documento, e `<body>` contém o conteúdo visível. 

### Um Pouco Mais sobre MetaTags

Qual é o papel do elemento meta description e como ele afeta o SEO?

```html
<meta
  name="description"
  content="Discover expert tips and techniques for gardening in small spaces, choosing the right plants, and maintaining a thriving garden."
/>
```

SEO, ou Otimização para Mecanismos de Busca, é uma prática que otimiza páginas da web para que elas se tornem mais visíveis e tenham uma classificação mais alta nos mecanismos de busca. Uma maneira de melhorar o SEO do seu site é fornecer uma breve descrição para a página usando o elemento meta. Aqui está um exemplo de uso do elemento meta para definir a descrição de uma página para um site de jardinagem:

## Títulos e Parágrafos

```html
<h1>Titulo h1</h1>
<h2>Titulo h2</h2>
<h3>Titulo h3</h3>
<h4>Titulo h4</h4>
<h5>Titulo h5</h5>
<h6>Titulo h6</h6>

<!-- ... -->
<p>Isso é um parágrafo...</p>
<p>Lorem <b>ipsum,</b> dolor sit amet <br> consectetur...</p>
```

- **Explicação:** As tags de título `<h1>` a `<h6>` são usadas para criar títulos de diferentes níveis. A tag `<p>` é usada para criar parágrafos. Tags de formatação como `<b>`, `<i>`, `<strong>`, `<em>` e `<br>` modificam o estilo do texto.

## Formatação em HTML

```html
<p><b>Negrito</b></p>
<p><strong>Enfase</strong></p>
<!-- ... -->
```

- **Explicação:** Tags como `<b>`, `<strong>`, `<i>`, `<em>`, `<mark>`, `<small>`, `<big>`, `<s>` e `<del>` são usadas para aplicar diferentes tipos de formatação ao texto.

## Citações e Elementos de Citação

```html
<p><q>Texto cotado</q></p>
<p><blockquote>Texto...</blockquote></p>
<!-- ... -->
```

- **Explicação:** A tag `<q>` é usada para indicar citações curtas. A tag `<blockquote>` é usada para citações longas ou blocos de texto.

## Listas

```html
<ul>
    <li>item 1</li>
    <li>item 2</li>
    <!-- ... -->
</ul>

<ol>
    <li>item A</li>
    <li>item B</li>
    <!-- ... -->
</ol>

<dl>
    <dt>Chrome</dt>
    <dd>o chrome foi desenvolvido pelo Google...</dd>
    <!-- ... -->
</dl>
```

- **Explicação:** As tags `<ul>` e `<ol>` são usadas para criar listas não ordenadas e ordenadas, respectivamente. A tag `<dl>` é usada para criar listas de definição.

## Imagens e Links

```html
<img src="../000-Exercícios/assets/States_of_Brazil.png" alt="Mapa do Brasil" title="Mapa dos estados do Brasil" width="150" height="150">

<p>O <a href="https://www.entra21.com.br/" target="_blank">Entra21</a> é um programa de empregabilidade e formação profissional.</p>

<p><a href="#titulo3">Link para o topo da página</a></p>
```

- **Explicação:** A tag `<img>` é usada para inserir imagens. A tag `<a>` é usada para criar links. O atributo `target="_blank"` abre o link em uma nova aba. O atributo `href="#titulo3"` cria um link interno para uma seção na mesma página.

## Caminhos
### Caminhos Relativos
Os caminhos relativos são usados para referenciar arquivos ou pastas em relação à localização atual do arquivo HTML. Existem três tipos básicos de caminhos relativos:
1. **Caminho para um Arquivo na Mesma Pasta**
   - Use apenas o nome do arquivo:
 ```html
     <a href="pagina.html">Link para Página</a>
 ```

2. **Caminho para um Arquivo em uma Pasta Subordinada**
   - Use o nome da pasta seguido pelo nome do arquivo:
     ```html
     <a href="subpasta/pagina.html">Link para Página em Subpasta</a>
     ```
3. **Caminho para um Arquivo em uma Pasta Superior**
   - Use `..` para indicar uma pasta superior e, em seguida, o caminho para o arquivo:
     ```html
     <a href="../outrapasta/pagina.html">Link para Página em Outra Pasta</a>
     ```

### Caminhos Absolutos

Caminhos absolutos especificam o caminho completo para um arquivo a partir da raiz do sistema de arquivos ou da raiz do servidor. Eles começam com uma barra (ou URL completa):
- **Caminho Absoluto para um Site Online**:
  ```html
  <a href="https://www.example.com/pagina.html">Link para Página Online</a>
  ```
- **Caminho Absoluto para o Sistema de Arquivos**:
  ```html
  <a href="/caminho/completo/para/pagina.html">Link para Página no Sistema de Arquivos</a>
  ```

### Links para Recursos Externos

Para vincular recursos externos, como imagens, folhas de estilo ou scripts, use caminhos relativos ou absolutos da mesma maneira:
- **Caminho Relativo para uma Imagem**:
  ```html
  <img src="imagens/imagem.jpg" alt="Minha Imagem">
  ```
- **Caminho Absoluto para um Script**:
  ```html
  <script src="https://www.example.com/scripts/meuscript.js"></script>
  ```
Lembre-se de adaptar os exemplos aos nomes de suas pastas, arquivos e URLs de recursos. A compreensão dos caminhos relativos e absolutos é crucial para organizar e acessar corretamente os recursos em seus projetos web.