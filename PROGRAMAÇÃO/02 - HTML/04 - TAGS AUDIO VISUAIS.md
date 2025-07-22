# Imagens

```html
<img 
	src="../000-Exercícios/assets/States_of_Brazil.png" 
	alt="Mapa do Brasil" 
	title="Mapa dos estados do brasil" 
	width="150" 
	height="150"
>
```

Neste trecho, estamos inserindo uma imagem usando a tag `<img>`. O atributo `src` especifica o caminho da imagem, `alt` define o texto alternativo para acessibilidade, `title` exibe uma dica ao passar o mouse sobre a imagem, e `width` e `height` definem as dimensões da imagem.

## Tipos de Imagem (jpeg, png, gif, svg, ico)

```html
<figure>
    <img 
	    src="assets/brazil-flag.png" 
	    alt="" 
	    width="100" 
	    title="Bandeira do Brasil"
	>
    <figcaption>Créditos: Algum Artista Qualquer</figcaption>
</figure>
```

Neste exemplo, usamos a tag `<figure>` para agrupar uma imagem e uma legenda relacionada. A imagem `<img>` é similar ao exemplo anterior. O `<figcaption>` contém o texto da legenda da imagem, que neste caso dá créditos ao artista.

# Vídeo (mp4, ogg, WebM)

```html
<video width="320" controls autoplay loop muted poster="caminho-da-imagem">
  <source src="assets/20230513_160933.mp4" type="video/mp4">
  <source src="assets/20230513_160933.ogg" type="video/ogg">
  <track src="assets/legenda.vtt" kind="captions" srclang="pt" label="Português">
  Seu navegador não é compatível com a tag vídeo.
</video>

```

Neste trecho, estamos incorporando um vídeo. O atributo `width` define a largura do vídeo em pixels. `controls` exibe os controles do player, `autoplay` faz o vídeo iniciar automaticamente, `loop` faz o vídeo repetir, e `muted` o torna sem som e `poster` será a imagem de poster do vídeo. Os elementos `<source>` especificam diferentes formatos do vídeo, que o navegador escolherá conforme a compatibilidade.

O elemento `<track>` adiciona legendas sincronizadas para melhorar a acessibilidade. O atributo `src` define o caminho do arquivo de legendas no formato `.vtt`. O `kind="captions"` indica que se trata de legendas com informações relevantes do áudio (como falas e sons). O `srclang="pt"` especifica o idioma das legendas como português, e o `label="Português"` define o nome visível no seletor de legendas do player. Esses atributos permitem que usuários escolham a legenda e compreendam o conteúdo mesmo sem som.

## Vídeo do Youtube

```html
<iframe 
	width="420" 
	height="315" 
	src="https://www.youtube.com/embed/SsqXAP0EeEI">
</iframe>
```

Aqui, estamos embutindo um vídeo do YouTube usando uma tag `<iframe>`. O atributo `src` especifica a URL do vídeo a ser incorporado, e `width` e `height` definem as dimensões do vídeo na página.

# Áudio

```html
<audio controls autoplay loop muted>
    <source src="assets/bad_to_the_bone.mp3" type="audio/mpeg">
    <source src="assets/bad_to_the_bone.ogg" type="audio/ogg">
    Seu Navegador não é compatível com a tag Audio
</audio>

<a href="caminho da musica" download>
	<p>Download</p>
</a>
```

Neste exemplo, estamos incorporando um elemento de áudio. Os atributos e as tags utilizadas são semelhantes aos do vídeo, mas adaptados para áudio. Os elementos `<source>` especificam os diferentes formatos do áudio. A tag `<p>` cria um link de "download" (embora ele não funcione no exemplo fornecido).
