Nomear bem variáveis e funções é essencial para escrever **códigos claros, fáceis de entender e manter** — tanto para outras pessoas quanto para você no futuro.

### Use camelCase
    
```js
// Comece com minúscula e use maiúscula para separar palavras:
let userName = "Ana";
let totalAmount = 250;
```

### Prefixos úteis para variáveis booleanas
    
```js
// Use prefixos que deixam claro que o valor é verdadeiro ou falso: `is`, `has`, `can`
let isLoggedIn = true;
let hasAccess = false;
let canEdit = true;
```

### Funções: comece com verbos
    
```js
// Funções devem indicar claramente o que fazem, geralmente começando com um verbo:
function getUserData() {}
function calculateTotal() {}
function validateInput() {}
```

### Funções que retornam booleanos (predicados)

```js
// Use os mesmos prefixos de booleanos:
function isValidEmail(email) {}
function hasPermission(user) {}
function canSubmit(form) {}
```

### Padrão "get" e "set"

```js
// Para funções que pegam dados:
function getUserProfile(id) {}
```
    
```js
// Para funções que **definem** dados:
function setUserPreferences(prefs) {}
```

### Funções de evento

```js
// Use `handle` ou `on` como prefixo ou `Handler` como sufixo:
function handleClick() {}
function onSubmit() {}
function keyPressHandler() {}
```
### Iteradores (loops)
    
```js
// Para loops simples, letras como `i`, `j` são comuns:
for (let i = 0; i < items.length; i++) {}
```

```js
// Em loops mais complexos, use nomes mais descritivos:
for (let studentIndex = 0; studentIndex < students.length; studentIndex++) {}
```

### Use nomes no plural para arrays

```js
// Isso deixa claro que a variável contém múltiplos itens:
const users = ["Ana", "João"];
const products = ["Mouse", "Teclado"];
```

### A regra de ouro

```ad-important
title: Importante
Se você sente que precisa escrever um comentário para explicar o nome de uma variável ou função, talvez ela precise de um nome melhor.

```

### Seja consistente

- Siga os **padrões do seu time ou projeto**.
- A consistência é mais importante do que escolher “o nome perfeito”.

### Conclusão

Bons nomes deixam o código mais **autoexplicativo**, **fácil de manter** e **profissional**. Nomes ruins custam tempo e causam confusão — evite isso nomeando com clareza e intenção.