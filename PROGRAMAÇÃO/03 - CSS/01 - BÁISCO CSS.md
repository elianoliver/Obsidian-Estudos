## CSS Inline

A abordagem **CSS inline** envolve a aplicação direta de estilos em um elemento HTML específico, usando o atributo `style`. Aqui está um exemplo:

```html
<p style="color: blue; font-size: 16px;">Este é um parágrafo estilizado inline.</p>
```

Neste exemplo, o estilo (cor do texto e tamanho da fonte) está diretamente inserido no elemento `<p>`. Embora seja útil para alterações rápidas, essa abordagem pode se tornar difícil de gerenciar em projetos maiores, pois mistura a estrutura HTML com os estilos.

## CSS Interno

A abordagem **CSS interno** envolve a inclusão das regras de estilo diretamente na seção `<style>` da mesma página HTML. Aqui está um exemplo:

```html
<!DOCTYPE html>
<html>
<head>
    <title>Exemplo de CSS Interno</title>
    <style>
        p {
            color: red;
            font-size: 18px;
        }
    </style>
</head>
<body>
    <p>Este é um parágrafo estilizado internamente.</p>
</body>
</html>
```

Nesse caso, o estilo é definido dentro da tag `<style>` no cabeçalho HTML. As regras de estilo são aplicadas aos elementos correspondentes na página. Essa abordagem permite um melhor gerenciamento dos estilos em comparação com o CSS inline, mas ainda limita a reutilização em várias páginas.

## CSS Externo

A abordagem **CSS externo** envolve a criação de um arquivo separado com extensão `.css` que contém todas as regras de estilo. Esse arquivo é então vinculado ao HTML usando a tag `<link>`. Aqui está um exemplo:

Suponha que temos um arquivo `estilos.css`:

```css
/* estilos.css */
p {
    color: green;
    font-size: 20px;
}
```

E o arquivo HTML vinculado a esse arquivo de estilo:

```html
<!DOCTYPE html>
<html>
<head>
    <title>Exemplo de CSS Externo</title>
    <link rel="stylesheet" type="text/css" href="estilos.css">
</head>
<body>
    <p>Este é um parágrafo estilizado externamente.</p>
</body>
</html>
```

Neste caso, o arquivo CSS está separado do HTML. Isso facilita a manutenção e o reuso de estilos em várias páginas, tornando o código mais organizado.