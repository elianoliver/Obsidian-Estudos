Em JavaScript, os métodos `match()`, `replace()`, `matchAll()` e `replaceAll()` permitem encontrar (corresponder) ou substituir partes de uma string que correspondem a um padrão definido por uma **expressão regular (regex)**. Por padrão, esses métodos operam apenas na **primeira ocorrência**, mas com o modificador **global (`g`)** ou métodos específicos como `matchAll()` e `replaceAll()`, é possível processar **todas as ocorrências** do padrão.

**Analogia**: É como procurar todas as palavras "gato" em um texto e, se quiser, substituir todas por "felino". Sem configurações especiais, você só encontra ou substitui o primeiro "gato", mas com as ferramentas certas, pode processar todos.

## Métodos e o Papel do Modificador `g`

### 1. **Método `match()` sem e com `g`**

O método `match()` encontra correspondências de um regex em uma string. Sem o modificador `g`, ele retorna apenas a **primeira correspondência** com detalhes (índice, string original, etc.). Com o `g`, retorna um **array com todas as correspondências**, mas sem informações extras como índices.

**Exemplo sem `g`:** Apenas a primeira ocorrência de `"freecodecamp"` é retornada, com detalhes como `index: 0`.
```javascript
const regex = /freecodecamp/;
const str = "freecodecamp is the best we love freecodecamp";
const matched = str.match(regex);
console.log(matched);
// [
//   'freecodecamp',
//   index: 0,
//   input: 'freecodecamp is the best we love freecodecamp',
//   groups: undefined
// ]
```

**Exemplo com `g`:** Retorna um array com todas as correspondências, mas sem informações como `index` ou `input`.
```javascript
const regex = /freecodecamp/g;
const str = "freecodecamp is the best we love freecodecamp";
const matched = str.match(regex);
console.log(matched); // ['freecodecamp', 'freecodecamp']
```

**Analogia**: Sem `g`, é como encontrar apenas a primeira ocorrência de uma palavra em um livro e anotar sua página. Com `g`, você lista todas as ocorrências, mas sem as páginas.

### 2. **Método `replace()` sem e com `g`**

O método `replace()` substitui a parte de uma string que corresponde ao regex por um novo texto. Sem o `g`, substitui apenas a **primeira ocorrência**. Com o `g`, substitui **todas as ocorrências**.

**Exemplo sem `g`:** Apenas a primeira ocorrência é substituída.
```javascript
const regex = /freecodecamp/;
const str = "freecodecamp is the best we love freecodecamp";
const replaced = str.replace(regex, "freeCodeCamp");
console.log(replaced); // "freeCodeCamp is the best we love freecodecamp"
```

**Exemplo com `g`:** Todas as ocorrências são substituídas.
```javascript
const regex = /freecodecamp/g;
const str = "freecodecamp is the best we love freecodecamp";
const replaced = str.replace(regex, "freeCodeCamp");
console.log(replaced); // "freeCodeCamp is the best we love freeCodeCamp"
```

**Analogia**: Sem `g`, é como corrigir apenas o primeiro erro de ortografia em um texto. Com `g`, você corrige todos os erros iguais.

### 3. **Método `matchAll()`**

Introduzido no ECMAScript 2019, o `matchAll()` retorna um **iterador** com todas as correspondências de um regex, incluindo detalhes como `index` e `input`. Ele **exige** o modificador `g`, caso contrário, lança um erro.

**Exemplo:**
```javascript
const regex = /freecodecamp/g;
const str = "freecodecamp is the best we love freecodecamp";
const matched = str.matchAll(regex);
console.log(Array.from(matched));
// [
//   ['freecodecamp', index: 0, input: 'freecodecamp is the best we love freecodecamp', groups: undefined],
//   ['freecodecamp', index: 33, input: 'freecodecamp is the best we love freecodecamp', groups: undefined]
// ]
```

- O `matchAll()` retorna um iterador, que pode ser convertido em um array com `Array.from()` para ver todas as correspondências.

- Cada correspondência inclui detalhes como `index` (posição onde foi encontrada) e `input` (string original).

**Iterador com `next()`:** O método `next()` retorna cada correspondência uma a uma. Quando não há mais correspondências, `done: true` é retornado.
```javascript
const regex = /freecodecamp/g; 
const str = "freecodecamp is the best we love freecodecamp";
const matched = str.matchAll(regex);
console.log(matched.next().value); // ['freecodecamp', index: 0, ...]
console.log(matched.next().value); // ['freecodecamp', index: 33, ...]
console.log(matched.next()); // { done: true, value: undefined }
```

**Por que usar um iterador?**  
O iterador é "preguiçoso" (lazy), ou seja, só busca a próxima correspondência quando solicitado, economizando recursos em regex complexos.

**Analogia**: É como folhear um livro página por página, anotando cada ocorrência de uma palavra com sua localização, mas só procurando quando você pede.

### 4. **Método `replaceAll()`**

Também introduzido no ECMAScript 2019, o `replaceAll()` substitui **todas as ocorrências** de um padrão em uma string. Ele **exige** o modificador `g` quando usado com regex, senão lança um erro.

Exemplo: Substitui todas as ocorrências de `"freecodecamp"` por `"freeCodeCamp"`.
```javascript
const regex = /freecodecamp/g;
const str = "freecodecamp is the best we love freecodecamp";
const replaced = str.replaceAll(regex, "freeCodeCamp");
console.log(replaced); // "freeCodeCamp is the best we love freeCodeCamp"
```

**Exemplo sem `g` (erro):**
```javascript
const regex = /freecodecamp/;
const replaced = str.replaceAll(regex, "freeCodeCamp"); // Erro: TypeError
```

**Analogia**: É como usar o "substituir tudo" em um editor de texto, corrigindo todas as ocorrências de uma palavra de uma só vez.

## Resumo Geral

- **Sem o modificador `g`**:
  - `match()`: Retorna apenas a primeira correspondência com detalhes (`index`, `input`).
  - `replace()`: Substitui apenas a primeira correspondência.
    
- **Com o modificador `g`**:
  - `match()`: Retorna um array com todas as correspondências, mas sem detalhes extras.
  - `replace()`: Substitui todas as ocorrências.
    
- **Métodos modernos (ECMAScript 2019)**:
  - `matchAll()`: Retorna um iterador com todas as correspondências, incluindo detalhes. Use `Array.from()` para obter um array. Requer `g`.
  - `replaceAll()`: Substitui todas as ocorrências. Requer `g` com regex.
    
- **Analogia final**: É como procurar e substituir palavras em um documento. Sem `g`, você para na primeira ocorrência; com `g` ou `matchAll`/`replaceAll`, você lida com todas de uma vez, com opções para mais detalhes ou eficiência.

**Dica para iniciantes**: Teste esses métodos no console do navegador. Use `matchAll()` quando precisar de detalhes sobre todas as correspondências e `replaceAll()` para substituições simples. Sempre inclua o `g` com regex nesses métodos modernos para evitar erros.