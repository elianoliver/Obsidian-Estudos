## Media types

Desde muito tempo o CSS tem suporte para se definir regras que só valem em certo contexto. Os **media types** permitem que se use estilos diferentes em situações diferentes e sempre foram muito usados para distinguir a renderização na tela da impressão:

```
 <link rel="stylesheet" href="estilos.css" media="screen"> <link rel="stylesheet" href="impressao.css" media="print"> 
```

Todos os navegadores modernos suportam esse media type `print` que é aplicado apenas quando vamos imprimir uma página (útil para esconder o menu de navegação ou aumentar a fonte do texto, por exemplo).

Alguns celulares antigos suportavam também o tipo `handheld` para estilos específicos para sites mobile. Os smartphones modernos como iPhone e Android, porém, ignoram o media type `handheld` pois são capazes de renderizar sites completos e não apenas as versões simples feitas para os celulares antigos.

Como então escrever CSS específico para mobile pensando em smartphones e tablets que não se encaixam no media querie `handheld`? Novos media queries!

## CSS3 media queries
Melhor do que separar os dispositivos em desktop (`screen`) e mobile (`handheld`), os novos media queries permitem que foquemos principalmente no **tamanho da tela** onde vamos exibir o conteúdo.

É possível criar um CSS que só se aplique a tamanhos de tela de, no máximo, _320px_ por exemplo (como um iPhone em modo retrato):
```
 <link rel="stylesheet" href="iphone.css" media="screen and (max-width: 320px)"> 
```

Existem diversas opções de media queries com bastante suporte. Além da `max-width`, podemos usar `min-width`, `width` e `device-width` - e todas as variações delas com `height`.

A diferença entre `width` e `device-width` é se estamos pensando em [CSS pixels ou no tamanho do viewport](https://blog.caelum.com.br/pixels-pixels-ou-pixels-dicas-de-web-mobile-com-viewport/). Geralmente não é boa prática depender do tamanho físico do aparelho então não usamos tanto `device-width`.

Uma decisão que precisa ser tomada é de se usar `max-width` ou `min-width`. O _max_ é bom para quando temos um layout Desktop pronto e queremos adaptá-lo para dispositivos menores - vamos então definindo novas regras que se aplicam só aos dispositivos de no máximo certo tamanho. Já o _min_ pode ser útil quando criamos um site só mobile ou começamos pelo mobile - nesse caso, é mais fácil ter um layout base e ir customizando para dispositivos maiores, com no mínimo certo tamanho.

## Mais media queries
Além dos media queries de tamanho, aparelhos mais modernos suportam também um media querie que pega a orientação do dispositivo:

```html
 <link rel="stylesheet" href="phones.css" media="screen and (min-width: 320px) and (orientation: portrait)"> 
```

Isso pode ser útil para customizar a experiência do site de acordo com como o usuário está segurando o aparelho. É [sabido](http://www.netmagazine.com/features/designing-touch), por exemplo, que um celular em modo retrato é mais usável com navegação na parte de baixo à esquerda; e, no modo paisagem, com navegação no topo e nas laterais.

Além de declarar as media queries na tag `<link>` no HTML, podemos também fazer direto dentro do arquivo CSS (podemos juntar tudo num arquivo CSS só e economizar requests):

```css
 /* regra aplicada em todo lugar */ 
 body { background: blue; }

/* aplica somente a partir de 320px */ 
@media screen and (min-width: 320px) { 
	body { font-size: 80%; } 
}

/* aplica somente a partir de 480px em landscape */ 
@media screen and (min-width: 480px) and (orientation: landscape) { 
	nav { float: left; } 
} 
```

Há ainda como mirar dispositivos de alta resolução (como iPhones e iPads com Retina Display) com `device-pixel-ratio` para provermos imagens de melhor qualidade quando elas forem úteis. Ou ainda a opção `(color)` que permite distinguir entre dispositivos coloridos ou não (como um ereader ou Kindle).

## Media queries comuns
E quais valores usar no projeto para adaptar para diferentes larguras? O ideal seria fazer as adaptações conforme seu layout exige (seria até possível fazer um layout só com porcentagens e sem media querie nenhum que funcione em diversos tamanhos de tela).

Mas se você pensa nos dispositivos mais comuns de hoje, existem algumas combinações de media queries famosas. O projeto [320andup](https://github.com/malarkey/320andup/) por exemplo sugere que você faça um layout base pensando em 320px e depois adapte para outros tamanhos com:

```css
 @media print { }

@media only screen and (min-width: 480px) { } 

@media only screen and (min-width: 600px) { } 

@media only screen and (min-width: 992px) { } 

@media only screen and (min-width: 1382px) { }

@media only screen and (-webkit-min-device-pixel-ratio: 1.5), 
only screen and (min--moz-device-pixel-ratio: 1.5), 
only screen and (-o-min-device-pixel-ratio: 3/2), 
only screen and (min-device-pixel-ratio: 1.5) { } 
```

Há a regra para impressão e outras 4 pensando em tamanhos comuns de smartphones e tablets. A última regra foca em dispositivos com alta resolução como os Retina Display e Android modernos. (o uso da keyword `only` serve apenas para esconder essas regras de navegadores antigos que não suportem media queries mas suportam o media type `screen`)