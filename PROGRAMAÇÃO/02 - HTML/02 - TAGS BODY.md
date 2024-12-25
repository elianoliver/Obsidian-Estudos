# Tutorial de Uso das Tags HTML

Este tutorial apresentará as tags HTML mais comuns usadas para estruturar o conteúdo **dentro do `<body>`** de uma página web. Você aprenderá sobre as tags `<header>`, `<main>`, `<footer>`, `<nav>`, `<aside>`, `<section>`, `<article>`, `<figure>`, e outras tags relevantes.

## Cabeçalho - `<header>`

A tag `<header>` é usada para representar o cabeçalho ou o topo de uma seção. Geralmente contém elementos de identificação, como logotipos, títulos e informações de navegação.

Exemplo:
```html
<header>
  <h1>Meu Site Incrível</h1>
  <nav>
    <ul>
      <li><a href="#">Início</a></li>
      <li><a href="#">Sobre</a></li>
      <li><a href="#">Contato</a></li>
    </ul>
  </nav>
</header>
```

## Conteúdo Principal - `<main>`

A tag `<main>` é usada para envolver o conteúdo principal da página. Deve conter o conteúdo principal que é exclusivo para essa página.

Exemplo:
```html
<main>
  <h2>Bem-vindo ao Meu Site</h2>
  <p>Este é o conteúdo principal da página.</p>
</main>
```

## Rodapé - `<footer>`

A tag `<footer>` é usada para representar o rodapé da página. Pode conter informações de contato, direitos autorais e links relacionados.

Exemplo:
```html
<footer>
  <p>&copy; 2023 Meu Site Incrível. Todos os direitos reservados.</p>
  <nav>
    <a href="#">Política de Privacidade</a>
    <a href="#">Termos de Uso</a>
  </nav>
</footer>
```

## Navegação - `<nav>`

A tag `<nav>` é usada para agrupar links de navegação. É apropriada para menus de navegação.

Exemplo:
```html
<nav>
  <ul>
    <li><a href="#">Início</a></li>
    <li><a href="#">Produtos</a></li>
    <li><a href="#">Serviços</a></li>
    <li><a href="#">Contato</a></li>
  </ul>
</nav>
```

## Conteúdo Secundário - `<aside>`

A tag `<aside>` é usada para envolver conteúdo que é secundário ou tangencial ao conteúdo principal. Pode conter informações adicionais, como anúncios ou widgets.

Exemplo:
```html
<aside>
  <h3>Artigos Relacionados</h3>
  <ul>
    <li><a href="#">Dicas para o Sucesso Online</a></li>
    <li><a href="#">Melhores Práticas de Design</a></li>
  </ul>
</aside>
```

## Seção - `<section>`

A tag `<section>` é usada para criar seções de conteúdo dentro do `<main>`. Ela ajuda a estruturar e organizar o conteúdo.

Exemplo:
```html
<section>
  <h2>Notícias</h2>
  <article>
    <h3>Novo Produto Lançado</h3>
    <p>Apresentamos o nosso mais novo produto inovador!</p>
  </article>
  <article>
    <h3>Parceria com Empresa XYZ</h3>
    <p>Anunciamos nossa emocionante parceria com a Empresa XYZ.</p>
  </article>
</section>
```

## Artigo - `<article>`

A tag `<article>` é usada para envolver conteúdo autônomo e significativo, como postagens de blog ou notícias. Deve ser capaz de ser lido e compreendido por si só.

Exemplo:
```html
<article>
  <h2>Título do Artigo</h2>
  <p>Este é um artigo interessante sobre um tópico importante.</p>
</article>
```

## Figura - `<figure>`

A tag `<figure>` é usada para envolver conteúdo de mídia, como imagens ou gráficos, juntamente com sua legenda usando a tag `<figcaption>`.

Exemplo:
```html
<figure>
  <img src="imagem.jpg" alt="Descrição da Imagem" title="">
  <figcaption>Uma foto incrível capturada em algum lugar.</figcaption>
</figure>
```

Lembre-se de que estas são apenas algumas das muitas tags HTML disponíveis para estruturar o conteúdo da página. O uso adequado dessas tags ajuda a criar uma estrutura clara e semântica para o seu site. Personalize os exemplos de acordo com suas necessidades específicas.