- **Grupos de Captura**: São partes de uma regex que você "isola" usando parênteses `()` para capturar uma porção específica do texto correspondido. Essas partes podem ser usadas posteriormente, seja para substituições ou para referências dentro da própria regex.
  
- **Backreferences**: São referências a grupos de captura, permitindo reutilizar o texto capturado em substituições ou na própria regex. Eles são úteis para garantir consistência ou preservar partes do texto.

## 1. Grupos de Captura

Os **grupos de captura** são criados ao envolver um padrão em parênteses `()`. Eles permitem capturar uma parte específica do texto correspondido para uso posterior, como em substituições ou validações.

```javascript
const regex = /free(code)camp/i;
console.log("freecodecamp".match(regex)); 
// ['freecodecamp', 'code', index: 0, input: 'freecodecamp', groups: undefined]
```

- Aqui, `(code)` é um grupo de captura que isola a palavra `code` na string `freecodecamp`.
  
- O `i` torna a busca insensível a maiúsculas e minúsculas.

- O resultado do `.match()` inclui:
  - O primeiro elemento: a correspondência completa (`freecodecamp`).
  - O segundo elemento: o texto capturado pelo grupo (`code`).

**Por que usar?**
- Grupos de captura são úteis para extrair partes específicas de uma string ou para manipular o texto em substituições.

## 2. Usando Grupos de Captura em Substituições

Grupos de captura brilham em métodos como `.replace()`, onde você pode usar o texto capturado na substituição.

**Exemplo**:
Suponha que queremos transformar `freecodecamp` em `paidcodeworld`, preservando a parte `code`.
```javascript
const regex = /free(code)camp/i;
console.log("freecodecamp".replace(regex, "paidcodeworld")); // paidcodeworld
```

Agora, se `code` tiver um número variável de `o` (ex.: `coooode`), podemos capturar esse padrão dinâmico:
```javascript
const regex = /free(co+de)camp/i;
console.log("freecooooodecamp".replace(regex, "paidcodeworld")); // paidcodeworld
```

Mas e se quisermos preservar o número exato de `o`? É aí que entram os **backreferences**.

## 3. Backreferences

**Backreferences** permitem reutilizar o texto capturado por um grupo de captura. Eles podem ser usados:

- Em substituições, com `$n` (onde `n` é o número do grupo).
- Na própria regex, com `\n` (onde `n` é o número do grupo).

**Exemplo com Substituição**:
```javascript
const regex = /free(co+de)camp/i;
console.log("freecooooodecamp".replace(regex, "paid$1world")); // paidcoooooworld
```

- Aqui, `$1` refere-se ao texto capturado pelo grupo `(co+de)` (ex.: `cooooode`).
- O resultado preserva o número exato de `o` capturado.

**Exemplo com Backreference na Regex**:
Imagine que queremos garantir que `freecodecamp` apareça duas vezes na string, com o **mesmo número de `o`**:

```javascript
const regex = /free(co+de)camp.*free\1camp/i;
console.log(regex.test("freecooooodecamp is great i love freecooooodecamp")); // true 
console.log(regex.test("freecooooodecamp is great i love freecodecamp")); // false
```

- `(co+de)` captura `coode`, `coooode`, etc.
  
- `\1` é a backreference que exige que o mesmo texto capturado (ex.: `coooode`) apareça novamente.

- A primeira string passa porque ambas as instâncias têm o mesmo número de `o` (`cooooode`).
  
- A segunda falha porque os números de `o` são diferentes.

## 4. Grupos de Captura Nomeados

Para evitar confusão com múltiplos grupos, você pode dar **nomes** aos grupos de captura. A sintaxe é `(?<nome>padrão)`.

```javascript
const regex = /free(?<code>co+de)camp/i;
console.log("freecooooodecamp".replace(regex, "paid$<code>world")); // paidcoooooworld
```

- `(?<code>co+de)` nomeia o grupo como `code`.
- Em substituições, usamos `$<code>` para referenciar o grupo nomeado.

**Backreference com Nome na Regex**:
```javascript
const regex = /free(?<code>co+de)camp.*free\k<code>camp/i;
console.log(regex.test("freecooooodecamp is freecooooodecamp")); // true
```

- Aqui, `\k<code>` é a backreference ao grupo nomeado `code`, garantindo que o mesmo texto (`cooooode`) apareça novamente.

## 5. Grupos Não Capturadores

Às vezes, você quer agrupar um padrão sem capturá-lo (para economizar memória ou simplificar). Use **grupos não capturadores**, com a sintaxe `(?:padrão)`.

**Exemplo**:
Para corresponder a `freecodecamp` ou `freecandycamp`:
```javascript
const regex = /free(?:code|candy)camp/i;
console.log(regex.test("freecodecamp")); // true 
console.log(regex.test("freecandycamp")); // true
```

- `(?:code|candy)` agrupa `code` ou `candy` com o operador `|` (OU), mas não armazena o resultado como um grupo de captura.

- O resultado do `.match()` não incluirá `code` ou `candy` como um grupo separado, apenas a correspondência completa.

## Por que usar Grupos de Captura e Backreferences?

- **Extração de Dados**: Capturar partes específicas de uma string (ex.: extrair `code` de `freecodecamp`).
  
- **Substituições Dinâmicas**: Preservar partes do texto original (ex.: manter o número de `o` em uma substituição).
  
- **Validação de Consistência**: Garantir que um padrão se repita exatamente (ex.: mesmo número de `o` em duas partes da string).
  
- **Legibilidade**: Grupos nomeados tornam a regex mais clara, especialmente em padrões complexos.

## Resumo Visual

| Conceito                     | Sintaxe            | Descrição                                        | Exemplo                          |
| ---------------------------- | ------------------ | ------------------------------------------------ | -------------------------------- |
| Grupo de Captura             | `(padrão)`         | Captura uma parte do texto para uso posterior    | `(code)` captura `code`          |
| Backreference (Substituição) | `$n` ou `$<nome>`  | Reutiliza o texto capturado em substituições     | `free(code)camp` → `paid$1world` |
| Backreference (Regex)        | `\n` ou `\k<nome>` | Reutiliza o texto capturado na regex             | `free(co+de)camp.*free\1camp`    |
| Grupo Nomeado                | `(?<nome>padrão)`  | Atribui um nome ao grupo de captura              | `(?<code>co+de)`                 |
| Grupo Não Capturador         | `(?:padrão)`       | Agrupa sem capturar, para lógica ou alternativas | `(?:code\|candy)`                |

## Dica Final

- **Teste suas regex**: Use ferramentas como regex101.com para visualizar grupos capturados e backreferences.
  
- **Cuidado com complexidade**: Muitos grupos e backreferences podem tornar a regex difícil de entender. Use nomes para maior clareza.
  
- **Compatibilidade**: Backreferences e grupos nomeados são amplamente suportados, mas verifique em ambientes mais antigos (ex.: navegadores legados).