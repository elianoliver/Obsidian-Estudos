Lookahead e lookbehind são tipos de assertions (afirmações) em expressões regulares que permitem verificar se um padrão é (ou não é) precedido ou seguido por outro padrão, **sem incluir esse padrão adicional no resultado da correspondência**. Eles são como "olhadelas" para frente (lookahead) ou para trás (lookbehind) no texto, ajudando a criar condições para a correspondência.

Existem **quatro tipos** de assertions:

1. **Positive Lookahead**: Verifica se um padrão é **seguido** por outro.
2. **Negative Lookahead**: Verifica se um padrão **não é seguido** por outro.
3. **Positive Lookbehind**: Verifica se um padrão é **precedido** por outro.
4. **Negative Lookbehind**: Verifica se um padrão **não é precedido** por outro.

Essas assertions são úteis porque permitem criar regras complexas para encontrar texto, mas apenas o padrão principal (e não a condição) é incluído no resultado da correspondência.

## 1. Positive Lookahead (?=)

O **positive lookahead** verifica se um padrão é imediatamente **seguido** por outro padrão. Ele é escrito como `(?=padrão)`.

```javascript
const regex = /free(?=code)/i;

console.log(regex.test("freeCodeCamp")); // true (free é seguido por code) 
console.log(regex.test("free code camp")); // false (há um espaço entre free e code) 
console.log(regex.test("I need someone for free to write code for me")); // false (free não é seguido imediatamente por code)
```

- Aqui, a regex procura pela palavra `free`, mas só considera uma correspondência válida se `free` for imediatamente seguida por `code`.
- O `i` torna a busca insensível a maiúsculas e minúsculas.

**Como funciona**:
- A regex verifica se `free` está presente e se `code` vem logo depois.
- Apenas `free` é considerado na correspondência, mas a condição (`code`) deve ser verdadeira.

## 2. Negative Lookahead (?!)

O **negative lookahead** verifica se um padrão **não é seguido** por outro. Ele é escrito como `(?!padrão)`.

```javascript
const regex = /free(?!code)/i;

console.log(regex.test("freeCodeCamp")); // false (free é seguido por code) 
console.log(regex.test("free code camp")); // true (free não é seguido por code) 
console.log(regex.test("I need someone for free to write code for me")); // true (free não é seguido por code)
```

Aqui, a regex procura por `free`, mas só considera uma correspondência válida se `free` **não for seguido** por `code`.

**Como funciona**:
- A regex verifica se `free` está presente e se **não** há `code` logo depois.
- O resultado é o oposto do positive lookahead.

## 3. Positive Lookbehind (?<=)

O **positive lookbehind** verifica se um padrão é **precedido** por outro. Ele é escrito como `(?<=padrão)`.

```javascript
const regex = /(?<=free)code/i;

console.log(regex.test("freeCodeCamp")); // true (code é precedido por free) 
console.log(regex.test("free code camp")); // false (code não é precedido imediatamente por free) 
console.log(regex.test("I need someone for free to write code for me")); // false (code não é precedido imediatamente por free)
```

Aqui, a regex procura pela palavra `code`, mas só considera uma correspondência válida se `code` for imediatamente precedido por `free`.

**Como funciona**:
- A regex verifica se `code` está presente e se `free` vem logo antes.
- Apenas `code` é incluído no resultado da correspondência.

## 4. Negative Lookbehind (?<!)

O **negative lookbehind** verifica se um padrão **não é precedido** por outro. Ele é escrito como `(?<!padrão)`.

```javascript
const regex = /(?<!free)code/i;

console.log(regex.test("freeCodeCamp")); // false (code é precedido por free) 
console.log(regex.test("free code camp")); // true (code não é precedido por free) 
console.log(regex.test("I need someone for free to write code for me")); // true (code não é precedido por free)
```

Aqui, a regex procura por `code`, mas só considera uma correspondência válida se `code` **não for precedido** por `free`.

**Como funciona**:
- A regex verifica se `code` está presente e se **não** há `free` logo antes.
- Apenas `code` é incluído no resultado.

## Como as Assertions Afetam o Resultado?

Um ponto importante é que **lookaheads e lookbehinds não aparecem no resultado da correspondência**. Eles apenas definem condições para a correspondência. Por exemplo:

```javascript
const regex = /(?<!free)code/i;
console.log("freeCodeCamp".match(regex)); // null (não corresponde)
console.log("free code camp".match(regex)); // ['code', index: 5, input: 'free code camp', groups: undefined]
console.log("I need someone for free to write code for me".match(regex)); // ['code', index: 33, input: 'I need someone for free to write code for me', groups: undefined]
```

- No resultado do método `.match()`, apenas `code` aparece, mesmo que a regex esteja verificando a ausência de `free`.
  
- Isso ocorre porque as assertions são usadas apenas para **condicionar** a correspondência, não para incluí-las no resultado.

## Por que usar Lookahead e Lookbehind?

Essas assertions são úteis quando você precisa:

- **Validar condições complexas**: Por exemplo, encontrar uma palavra apenas se ela estiver em um contexto específico.
  
- **Manter o resultado limpo**: Como as assertions não aparecem no resultado, você pode focar apenas no texto que realmente deseja capturar.
  
- **Criar regras avançadas**: Por exemplo, validar senhas que atendam a condições específicas (como conter um número após uma letra).

**Exemplo prático**:
Imagine que você quer encontrar todas as palavras `code` em um texto, mas apenas se elas não forem precedidas por `free`. Você pode usar um **negative lookbehind** (`(?<!free)code`) para garantir isso, e o resultado conterá apenas `code`, sem incluir `free`.

## Resumo Visual

| Tipo                | Sintaxe               | Descrição                                          | Exemplo         |
| ------------------- | --------------------- | -------------------------------------------------- | --------------- |
| Positive Lookahead  | `padrão(?=condição)`  | Verifica se o padrão é seguido pela condição       | `free(?=code)`  |
| Negative Lookahead  | `padrão(?!condição)`  | Verifica se o padrão não é seguido pela condição   | `free(?!code)`  |
| Positive Lookbehind | `(?<=condição)padrão` | Verifica se o padrão é precedido pela condição     | `(?<=free)code` |
| Negative Lookbehind | `(?<!condição)padrão` | Verifica se o padrão não é precedido pela condição | `(?<!free)code` |

## Dica Final

- **Use com cuidado**: Nem todos os mecanismos de regex suportam lookbehind (especialmente em navegadores antigos). Verifique a compatibilidade se estiver trabalhando com JavaScript em ambientes variados.
  
- **Teste bastante**: Regex pode ser complicada. Use ferramentas como regex101.com para testar suas expressões.