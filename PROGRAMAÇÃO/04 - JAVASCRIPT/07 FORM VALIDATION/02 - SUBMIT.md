O evento `submit` é disparado quando um formulário HTML é enviado. Ele ocorre quando o usuário tenta enviar os dados preenchidos no formulário, e o comportamento do envio depende de atributos específicos do elemento `<form>`. O JavaScript pode ser usado para capturar esse evento e personalizar o que acontece, mas antes é importante entender como o envio funciona.

## Como um formulário é enviado?

Existem **três maneiras** de acionar o evento `submit`:
### 1. **Clicando em um botão de envio**:
   - Um botão com o atributo `type="submit"` dentro do formulário dispara o evento `submit` quando clicado.
   - Exemplo: `<button type="submit">Enviar</button>`.
### 2. **Pressionando a tecla Enter**:
   - Quando o usuário pressiona Enter em um campo editável (como `<input>` ou `<textarea>`), o formulário é enviado, desde que o campo esteja em foco.
### 3. **Chamando métodos via JavaScript**:
   - Os métodos `form.requestSubmit()` ou `form.submit()` podem ser usados para enviar o formulário programaticamente.
   - **Nota**: `submit()` não dispara o evento `submit`, enquanto `requestSubmit()` dispara.

## O que acontece quando o formulário é enviado?

Quando o evento `submit` é acionado, o navegador processa o formulário com base em seus atributos, enviando os dados para um destino específico. Os principais atributos que controlam esse comportamento são:

### 1. Atributo `action`
- Define **para onde** os dados do formulário serão enviados.
  
- Pode ser:
  - Uma URL completa (ex.: `https://freecodecamp.org`).
  - Um caminho relativo no domínio atual (ex.: `/data`, que pode ser algo como `http://127.0.0.1:5500/data`).
    
- **Padrão**: Se o atributo `action` não for definido, os dados são enviados para a URL da página atual.

```html
<form action="/data">
  <input type="number" name="number" placeholder="Enter a number" />
  <button type="submit">Submit</button>
</form>
```
Nesse caso, o formulário enviará os dados para o caminho `/data` no domínio atual.

### 2. Atributo `method`
- Define **como** os dados serão enviados, usando um método HTTP (Hypertext Transfer Protocol).
  
- Os métodos mais comuns são:
  - **GET**: Usado para buscar dados, sem alterá-los. Os dados do formulário são anexados à URL como uma **query string** (ex.: `http://127.0.0.1:5500/data?number=3342`).
    - Ideal para formulários de busca, onde os dados não modificam o servidor.
      
  - **POST**: Usado para enviar dados ao servidor para criar ou atualizar recursos. Os dados são incluídos no **corpo da requisição**, não na URL.
    - Ideal para formulários de registro ou envio de dados sensíveis.
      
- **Padrão**: Se o atributo `method` não for definido, o formulário usa GET.

**Exemplo com POST**:
```html
<form action="/data" method="POST">
  <input type="number" name="number" placeholder="Enter a number" />
  <button type="submit">Submit</button>
</form>
```
Os dados (ex.: `number=3342`) são enviados no corpo da requisição para `http://127.0.0.1:5500/data`, não na URL.

### 3. Atributo `enctype`
- Define o **formato de codificação** dos dados enviados no corpo da requisição (usado principalmente com `method="POST"`).
  
- Valores possíveis:
  - `application/x-www-form-urlencoded` (padrão): Os dados são codificados como pares `name=value`, com caracteres especiais convertidos (ex.: `name=John+Doe&email=john%40example.com`).
  - `text/plain`: Os dados são enviados como texto simples, com pares `name=value` separados por quebras de linha.
  - `multipart/form-data`: Usado para formulários com upload de arquivos, como imagens ou documentos.
    
- **Quando usar?** O padrão `application/x-www-form-urlencoded` é suficiente para a maioria dos casos, exceto quando há upload de arquivos, que exige `multipart/form-data`.

**Exemplo com codificação**:
```html
<form action="/data" method="POST" enctype="multipart/form-data">
  <input type="file" name="file" />
  <button type="submit">Submit</button>
</form>
```
Esse formulário permite enviar arquivos, como imagens, e os dados são codificados adequadamente para isso.

## Como capturar o evento `submit` com JavaScript?

Você pode usar o evento `submit` para executar código personalizado quando o formulário é enviado. Por exemplo, para validar os dados ou enviar via AJAX sem recarregar a página.

```javascript
const form = document.querySelector("form");

form.addEventListener("submit", (e) => {
  e.preventDefault(); // Impede o comportamento padrão (envio e recarregamento)
  console.log("Formulário enviado!");
  // Aqui você pode validar os dados ou enviá-los via AJAX
});
```

- O `e.preventDefault()` é usado para bloquear o comportamento padrão do envio (como recarregar a página), permitindo que você processe os dados com JavaScript.

## Resumo

O evento `submit` é acionado quando um formulário é enviado, seja por um botão `type="submit"`, pela tecla Enter ou por JavaScript (`requestSubmit()`). O comportamento do envio é controlado por:

- **action**: Define o destino dos dados (URL ou caminho relativo).
  
- **method**: Define o método HTTP (`GET` para buscar, `POST` para criar/atualizar).
  
- **enctype**: Define o formato dos dados no corpo da requisição (padrão é `application/x-www-form-urlencoded`).
  
Com JavaScript, você pode capturar o evento `submit`, usar `e.preventDefault()` para bloquear o comportamento padrão e implementar lógica personalizada, como validação ou envio assíncrono. Esses conceitos são a base para criar formulários interativos e funcionais!