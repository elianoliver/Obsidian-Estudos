Um módulo em JavaScript é um arquivo que contém código reutilizável, como funções, variáveis ou classes, e que pode ser separado em partes menores para deixar o código mais **organizado, reutilizável e fácil de manter**.

## Por que usar módulos?

- Evitam conflitos de nomes entre variáveis/funções.
- Facilitam a manutenção, separando responsabilidades.
- Permitem reaproveitar código em diferentes arquivos.
 
## Como criar e exportar um módulo

Você escreve seu código em um **arquivo separado** (ex: `math.js`) e usa a palavra-chave `export` para disponibilizar funções, variáveis ou classes:

```js
// math.js
export function add(a, b) {
  return a + b;
}

export const PI = 3.14;
```

## Como importar um módulo

No outro arquivo (ex: `app.js`), use `import` para trazer o que foi exportado:

```js
// app.js
import { add, PI } from './math.js';

console.log(add(2, 3)); // 5
console.log(PI);        // 3.14
```

## Importar tudo de um módulo

Você pode importar tudo como um objeto:

```js
import * as Math from './math.js';

console.log(Math.add(2, 3)); // 5
console.log(Math.PI);        // 3.14
```

## Exportação e importação _default_

Quando o módulo exporta apenas **uma coisa principal**, você pode usar `export default`:

```js
// math.js
export default function multiply(a, b) {
  return a * b;
}
```

```js
// app.js
import multiply from './math.js';

console.log(multiply(4, 5)); // 20
```

```ad-hint
title: Dica
para `export default`, **não se usa chaves** na importação.

```

## Módulos no navegador

Para usar módulos no HTML, o `script` deve ter `type="module"`:

```html
<script type="module" src="app.js"></script>
```

## Resumo final

- `export` → Torna algo disponível para outros arquivos.
- `import` → Traz código de outro módulo para ser usado.
- `default` → Usado quando o módulo tem uma exportação principal.
- Módulos ajudam a dividir e organizar bem o projeto.
    
Usar módulos é essencial em projetos modernos com JavaScript.