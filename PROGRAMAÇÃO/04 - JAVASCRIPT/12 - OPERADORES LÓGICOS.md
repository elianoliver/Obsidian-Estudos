## Operadores Lógicos "E" (AND) e "OU" (OR)

No JavaScript, os operadores lógicos "E" (AND) e "OU" (OR) são usados para combinar condições e determinar o resultado de expressões booleanas. Vamos explorar esses operadores com exemplos:

### Operador Lógico "E" (AND) - &&

O operador `&&` verifica se **ambas as condições são verdadeiras** para que a expressão completa seja considerada verdadeira. Ele realiza **avaliação de curto-circuito**.

Exemplo:

```javascript
const x = 5;
const y = 10;

if (x > 0 && y < 15) {
  console.log("Ambas as condições são verdadeiras.");
} else {
  console.log("Pelo menos uma das condições é falsa.");
}
```

### Operador Lógico "E" (AND) - `&`

O operador `&` também verifica se **ambas as condições são verdadeiras**. No entanto, ele **executa ambas as condições**, independentemente do resultado da primeira.

Exemplo:

```javascript
const a = true; 
const b = false;  

if (a & b) {
	console.log("Ambas as condições são verdadeiras."); 
} else {   
	console.log("Pelo menos uma das condições é falsa."); 
}``` 

### Operador Lógico "OU" (OR) - ||

O operador `||` verifica se **pelo menos uma das condições é verdadeira** para que a expressão completa seja considerada verdadeira. Ele também realiza **avaliação de curto-circuito**.

Exemplo:

```javascript
const a = true;
const b = false;

if (a || b) {
  console.log("Pelo menos uma das condições é verdadeira.");
} else {
  console.log("Ambas as condições são falsas.");
}
```

### Diferenças entre `&&`, `&` e `||`

A diferença é que a quando usamos a versão dupla do operador (&& e ||), se a condição da operação for resolvida, ela não continua as avaliações das condições seguintes.

Imagine que você está executando uma operação **E**. Se a verificação da esquerda resultar **falso**, não é necessário verificar o teste do lado direito da operação, concorda? Independente do resultado da segunda parte da operação, o resultado final será **falso**.

O mesmo se aplica para a operação **OU**. Se a verificação da esquerda resultar **verdadeiro**, não é necessário verificar o teste do lado direito da operação. Independente do resultado da segunda parte da operação, o resultado final será **verdadeiro**.

Quando usamos os operadores duplos (&& e ||) o java não continua as verificações se o resultado já for conhecido. Já usando os operadores simples (& e |), ambos os lados da operação são **sempre** verificados.

## Formatos Numéricos em JavaScript

Além dos operadores lógicos, JavaScript permite representar números em diferentes formatos:

### Operadores Lógicos em Números Binários
Quando usamos os operadores lógicos `&` (AND) e `|` (OR) em números binários, estamos comparando os bits (0s e 1s) que compõem esses números. Cada bit de um número representa uma potência de 2 na base 2 (binária). 

**Operador `&` (AND):**
- Quando usamos `&`, estamos comparando cada par de bits dos números, um a um.
- Se ambos os bits comparados forem 1, o resultado desse bit na operação será 1. Caso contrário, será 0.

```javascript
var num = 9 & 3
console.log(num); // 1
```

Vamos usar seu exemplo, `9 & 3`:
- 9 em binário é `1001`.
- 3 em binário é `0011`.
  
- Ao comparar bit a bit: 
  - O primeiro bit: 1 & 0 é 0.
  - O segundo bit: 0 & 0 é 0.
  - O terceiro bit: 0 & 1 é 0.
  - O quarto bit: 1 & 1 é 1.

- O resultado é `0001` em binário, que representa 1 em decimal.

**Operador `|` (OR):**
- Quando usamos `|`, estamos comparando cada par de bits dos números, um a um.
- Se pelo menos um dos bits comparados for 1, o resultado desse bit na operação será 1.
```javascript
var num = 9 | 3
console.log(num); // 11
```

Vamos usar seu exemplo, `9 | 3`:
- 9 em binário é `1001`.
- 3 em binário é `0011`.
  
- Ao comparar bit a bit:
  - O primeiro bit: 1 | 0 é 1.
  - O segundo bit: 0 | 0 é 0.
  - O terceiro bit: 0 | 1 é 1.
  - O quarto bit: 1 | 1 é 1.

- O resultado é `1011` em binário, que representa 11 em decimal.

Em resumo, esses operadores lógicos bit a bit permitem comparar e combinar os bits de números binários, produzindo resultados em binário que podem ser convertidos para decimal.
### Número Binário
Os números binários são representados com o prefixo `0b`.

```javascript
const binario = 0b101; // Em decimal, é igual a 5.
console.log(binario);
```

### Número Octal
Os números octais são representados com o prefixo `0o`.

```javascript
const octal = 0o10; // Em decimal, é igual a 8.
console.log(octal);
```

### Número Hexadecimal
Os números hexadecimais são representados com o prefixo `0x`.

```javascript
const hexadecimal = 0x1F; // Em decimal, é igual a 31.
console.log(hexadecimal);
```

### Número Exponencial
Números podem ser representados em notação exponencial usando `e` ou `E`.

A notação exponencial, representada por `e` ou `E`, é uma maneira de escrever números em JavaScript usando potências de 10. Quando você vê algo como `2e3`, isso significa "2 vezes 10 elevado à potência de 3".

`2e3` é igual a 2 * 10^3, que é igual a 2 * 1000, que é igual a 2000.

```javascript
const exponencial = 2e3; // Igual a 2000.
console.log(exponencial);
```

Portanto, `2e3` é igual a 2000 em decimal. A notação exponencial é uma maneira conveniente de lidar com números grandes ou pequenos, usando potências de 10 como base. O `e` ou `E` representa a potência de 10 à qual o número deve ser elevado.