Os formulários em HTML são uma parte fundamental da interação do usuário com as páginas da web. Eles permitem coletar informações dos visitantes e enviá-las para um servidor web ou processá-las no lado do cliente. Vamos explorar os conceitos essenciais relacionados aos formulários HTML.

## O que é um Formulário?

Um formulário HTML é um elemento `<form>` que cria uma área interativa onde os usuários podem inserir e enviar informações. Os formulários são usados para coletar dados como texto, seleções, opções múltiplas e muito mais. Eles são comumente usados para criar:

- Cadastros de usuário
- Pesquisas
- Caixas de comentários
- Configurações personalizadas

## Sumário
- [[#Estrutura `<form>`]]
- [[#Atributos `<form>`]]
	- [[#`action`]]
	- [[#`target`]]
	- [[#`method`]]
	- [[#`autocomplete`]]
	- [[#`novalidate`]]
	- [[#`accept-charset`]]
	- [[#`enctype`]]
	- [[#`name`]]
	- [[#`rel`]]

## Estrutura `<form>`
Para criar um formulário em HTML, você começa com o elemento `<form>`. Veja um exemplo básico:

```html
<form action="processar.php" method="POST">
    <!-- Conteúdo do formulário aqui -->
</form>
```

- `action`: O atributo `action` define para onde os dados do formulário serão enviados quando o usuário o submeter. Neste exemplo, os dados serão enviados para um arquivo chamado "processar.php". Isso geralmente é um script no servidor que processa os dados enviados.

- `method`: O atributo `method` define como os dados serão enviados para o servidor. Existem dois valores principais:

  - `GET`: Os dados do formulário são anexados à URL e visíveis na barra de endereço. É adequado para formulários que não enviam informações confidenciais e que podem ser acessadas via URL. Por exemplo, uma pesquisa.
  
  - `POST`: Os dados do formulário são enviados no corpo da solicitação HTTP, tornando-os menos visíveis e mais seguros. É adequado para formulários que enviam informações sensíveis, como senhas.
## Atributos `<form>`
O elemento `<form>` em HTML é usado para criar formulários web que permitem aos usuários inserir dados e enviá-los para um servidor para processamento. Ele suporta vários atributos para controlar o comportamento e a ação do formulário.

### `action`
O atributo `action` define para onde os dados do formulário serão enviados quando o formulário for submetido. Ele geralmente aponta para um URL onde um script ou página no servidor receberá e processará os dados do formulário.

```html
<form action="processar.php" method="POST">
    <!-- Conteúdo do formulário -->
</form>
```
Neste exemplo, os dados do formulário serão enviados para o arquivo "processar.php" no servidor quando o formulário for submetido.

### `target`
O atributo `target` controla onde o resultado do envio do formulário será exibido. Os valores comuns incluem `_self` (para abrir no mesmo quadro/janela) e `_blank` (para abrir em uma nova janela ou guia).

```html
<form action="processar.php" method="POST" target="_blank">
    <!-- Conteúdo do formulário -->
</form>
```
Neste exemplo, o resultado do envio do formulário será exibido em uma nova janela ou guia.

### `method`
O atributo `method` especifica o método HTTP a ser usado ao enviar os dados do formulário. Os valores comuns são "GET" e "POST". O método "GET" anexa os dados do formulário à URL, enquanto o método "POST" os envia no corpo da solicitação.

```html
<form action="processar.php" method="POST">
    <!-- Conteúdo do formulário -->
</form>
```
Neste exemplo, os dados do formulário serão enviados usando o método "POST".

### `novalidate`
O atributo `novalidate` é usado para desativar a validação HTML5 padrão do navegador para campos de formulário. Isso permite que você faça a validação personalizada no lado do servidor.

```html
<form action="processar.php" method="POST" novalidate>
    <!-- Conteúdo do formulário -->
</form>
```
Neste exemplo, a validação HTML5 padrão está desativada.

### `accept-charset`
O atributo `accept-charset` especifica o conjunto de caracteres que o navegador deve usar ao enviar os dados do formulário. Ele é útil quando você precisa garantir que os dados sejam interpretados corretamente no servidor.

```html
<form action="processar.php" method="POST" accept-charset="UTF-8">
    <!-- Conteúdo do formulário -->
</form>
```
Neste exemplo, o conjunto de caracteres UTF-8 é especificado para o envio de dados.

### `enctype`
O atributo `enctype` especifica como os dados do formulário devem ser codificados antes de serem enviados para o servidor. Isso é importante quando o formulário contém dados binários, como envio de arquivos. Os valores comuns incluem "application/x-www-form-urlencoded" (padrão) e "multipart/form-data" (para envio de arquivos).

```html
<form action="processar.php" method="POST" enctype="multipart/form-data">
    <!-- Conteúdo do formulário -->
</form>
```
Neste exemplo, o formulário é configurado para envio de arquivos.

### `name`
O atributo `name` define um nome para o formulário, que pode ser usado para identificá-lo no JavaScript ou no servidor. Ele não afeta o comportamento do formulário no navegador.

```html
<form action="processar.php" method="POST" name="meuFormulario">
    <!-- Conteúdo do formulário -->
</form>
```
Neste exemplo, o formulário é nomeado como "meuFormulario".

### `rel`
O atributo `rel` é usado para definir a relação entre o documento atual e o recurso apontado pelo atributo `action`. É geralmente usado para especificar a relação de um link com o formulário.

```html
<form action="processar.php" method="POST" rel="external">
    <!-- Conteúdo do formulário -->
</form>
```
Neste exemplo, o atributo `rel` define a relação "external" entre o formulário e o recurso apontado por "processar.php".


