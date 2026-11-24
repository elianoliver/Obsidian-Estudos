Quando se trata de adicionar funcionalidades dinâmicas e interatividade às páginas da web, a tag `<script>` desempenha um papel fundamental ao permitir a incorporação de código JavaScript. 

No entanto, essa tag oferece uma variedade de atributos que podem afetar o comportamento e o carregamento dos scripts. Neste guia, exploraremos de forma didática os principais atributos da tag `<script>` em HTML, apresentando exemplos práticos para cada um deles, a fim de compreender como podem ser usados para controlar a execução de scripts e otimizar a experiência do usuário.

## Atributos da Tag Script
1. **async**: O atributo `async` é usado quando você deseja que um script seja carregado de forma assíncrona. Isso é útil para scripts que não dependem do carregamento de outros recursos na página.

   ```html
   <script async src="meu-script-async.js"></script>
   ```

   Neste exemplo, o script "meu-script-async.js" será carregado e executado de forma assíncrona, sem bloquear o carregamento da página.

2. **charset**: O atributo `charset` permite definir o padrão de caracteres usado no script. Isso pode ser útil quando você está trabalhando com caracteres especiais, como caracteres acentuados em JavaScript.

   ```html
   <script charset="UTF-8" src="meu-script-charset.js"></script>
   ```

   Neste caso, o script "meu-script-charset.js" é carregado com o conjunto de caracteres UTF-8.

3. **defer**: O atributo `defer` é usado para indicar que o script será executado após a página ser completamente carregada. Isso evita que o script bloqueie o carregamento da página.

   ```html
   <script defer src="meu-script-defer.js"></script>
   ```

   O script "meu-script-defer.js" será carregado enquanto a página é carregada, mas sua execução aguardará até que a página esteja pronta.

4. **src**: O atributo `src` é usado para definir a fonte externa do script, permitindo carregar código JavaScript a partir de um arquivo externo.

   ```html
   <script src="meu-script-externo.js"></script>
   ```

   Neste caso, o código JavaScript contido em "meu-script-externo.js" será carregado e executado na página.

5. **type**: O atributo `type` define o tipo de mídia do script, que geralmente é "text/javascript" para código JavaScript.

   ```html
   <script type="text/javascript">
       // Seu código JavaScript aqui
   </script>
   ```

   Este exemplo define explicitamente o tipo do script como "text/javascript" para indicar que o conteúdo do `<script>` é código JavaScript.
## Async Vs Defer
O problema de scripts bloqueadores é uma preocupação fundamental ao desenvolver páginas da web. Quando um navegador encontra uma tag `<script>` em um documento HTML, ele interrompe o processo de renderização da página para carregar e executar esse script. Isso significa que, por padrão, o JavaScript é considerado um "bloqueador de recursos", atrasando a exibição de conteúdo na página até que o script seja totalmente baixado e executado. Isso pode ser especialmente problemático em páginas com vários arquivos JavaScript, pois atrasa o primeiro evento que desenha a página web, mesmo quando o HTML não depende dos scripts.

Para resolver esse problema, temos duas opções: `async` e `defer`. Ambos permitem gerenciar a ordem de busca e execução de scripts externos, tornando o trabalho com scripts não bloqueadores uma opção viável.

- **async**:
  - O atributo `async` permite que o navegador faça o download do script de forma assíncrona, ou seja, em paralelo com a análise do HTML. Isso significa que o bloqueio ocorre apenas durante a execução do script, após o download ser concluído.

- **defer**:
  - O atributo `defer` também permite o download assíncrono do script, mas a execução do script é adiada até que o documento seja totalmente analisado, antes do evento `DOMContentLoaded`. O uso de `defer` é ideal quando o script requer que o DOM esteja totalmente carregado.

Então, quando e qual atributo usar depende da situação:
- Se o elemento `<script>` está declarado no início ou no final do documento.
- Se o script é autônomo e não depende de outros scripts ou do DOM.
- Se o script precisa que o DOM esteja totalmente carregado.

A escolha entre `async` e `defer` depende desses fatores e do comportamento desejado para o seu script. Essas opções proporcionam flexibilidade no controle do carregamento e da execução de scripts, permitindo que você otimize o desempenho das suas páginas web de acordo com suas necessidades específicas.

![[async defer.png]]