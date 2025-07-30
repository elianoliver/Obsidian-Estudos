## Sintaxe

`Number()` é uma função usada para **converter outros tipos de dados em número** (type coercion). Ela pode ser usada de duas formas:

### Com `new Number()` cria um objeto número

- **Evite usar assim.** Cria um objeto, não um valor primitivo.
- Usado raramente, mais útil em contextos específicos (ex: usar métodos do objeto).

```js
const numObj = new Number("34");
console.log(typeof numObj); // "object"
```

### Com `Number()` faz conversão de tipo (mais comum)

- Muito útil para converter valores recebidos como **string** (ex: input do usuário) para **número**.

```js
const num = Number("100");
console.log(num); // 100
console.log(typeof num); // "number"
```

### Regras de conversão (coerção de tipo):

#### Converte para número válido:

| Valor                      | Resultado |
| -------------------------- | --------- |
| `"123"` (string numérica)  | `123`     |
| `true`                     | `1`       |
| `false`                    | `0`       |
| `null`                     | `0`       |
| `""` (string vazia)        | `0`       |
| `[]` (array vazio)         | `0`       |
| `[7]` (array com 1 número) | `7`       |
#### Resulta em `NaN` (Not a Number):

| Valor                                  | Resultado |
| -------------------------------------- | --------- |
| `"abc"` (texto aleatório)              | `NaN`     |
| `undefined`                            | `NaN`     |
| `[1, 2, 3]` (array com vários valores) | `NaN`     |
| `["texto"]` (array com string)         | `NaN`     |
| `{}` (objeto)                          | `NaN`     |
