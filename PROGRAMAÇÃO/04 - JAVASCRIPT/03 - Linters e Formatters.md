Em desenvolvimento de software, manter o código **limpo, padronizado e sem erros** é essencial. Para isso, usamos duas ferramentas importantes: **linters** e **formatters**.

## O que é um Linter?

Um **linter** é uma ferramenta que **analisa o código automaticamente** (sem executá-lo) para encontrar:

- Erros de sintaxe ou lógica
- Más práticas
- Problemas de estilo (como falta de ponto e vírgula ou indentação errada)

```js
function soma(x) {
  return x + z // z não está definido
}

// Um linter como o **ESLint** vai avisar que a variável `z` não existe e que está faltando `;`.
```
### Vantagens:

- Evita bugs antes da execução
- Garante boas práticas
- Mantém o código consistente, mesmo com várias pessoas no projeto

## O que é um Formatter?

Um **formatter** é uma ferramenta que **reorganiza automaticamente** seu código para seguir um estilo visual padrão.

antes:

```js
function soma(
  a, 
  b, 
  c
) {return a + b + c;}
```

depois com Prettier:

```js
function soma(a, b, c) {
  return a + b + c;
}
```

### Vantagens:

- Código sempre formatado do mesmo jeito
- Reduz discussão sobre estilo em code reviews
- Economiza tempo (você não precisa alinhar tudo manualmente)

## Usando os dois juntos

- **ESLint** pode encontrar erros e sugerir correções.
- **Prettier** formata o código automaticamente.
- Ambos podem ser integrados ao seu editor de texto (ex: VS Code) ou configurados para rodar **antes de cada commit**.

## Conclusão

|Linter|Formatter|
|---|---|
|Aponta erros e más práticas|Organiza visualmente o código|
|Ex: ESLint|Ex: Prettier|
|Ajuda a evitar bugs|Garante estilo padronizado|

Juntos, **linters e formatters** ajudam a manter seu código **padronizado, limpo e livre de erros**, liberando você para focar no que realmente importa: **resolver problemas**.

