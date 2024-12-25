JavaScript é uma linguagem de programação versátil que oferece suporte a uma ampla gama de operações aritméticas. Neste exemplo, exploraremos as operações matemáticas mais comuns e como usá-las em JavaScript.

## Sumário
- [[#Operações Aritméticas]]
- [[#Incrementação e Decrementação]]
- [[#Radiciação e Porcentagem]]
- [[#Biblioteca Math]]

## Operações Aritméticas
1. **Declaração de Variáveis:**
Antes de realizar operações aritméticas, declaramos duas variáveis, `num1` e `num2`, e uma variável `resultado` para armazenar os resultados das operações.

```javascript
var num1 = 3;
var num2 = 2;
var resultado;
```

2. **Adição:**
A adição é representada pelo operador `+`. Você pode somar os valores diretamente ou atribuir o resultado a uma variável.

```javascript
resultado = num1 + num2;                  // armazena o resultado 5
console.log("resultado1: " + resultado); // resultado1: 5

console.log("resultado2: " + (num1 + num2)); // resultado2: 5
```

Há também a forma abreviada de adição, onde você pode usar o operador `+=` para atualizar o valor de uma variável.
```javascript
num1 += num2;                        // num1 = num1 + num2
console.log("resultado3: " + num1); // resultado3: 5
```

3. **Subtração:**
A subtração é realizada com o operador `-`. Da mesma forma que com a adição, você pode subtrair valores diretamente ou atribuir o resultado a uma variável.

```javascript
resultado = num1 - num2;                  // armazena o resultado 1
console.log("Subtração1: " + resultado); // Subtração1: 1

console.log("Subtração2: " + (num1 - num2)); // Subtração2: 1
```

E a forma abreviada usando `-=`:
```javascript
num1 -= num2;                        // num1 = num1 - num2
console.log("Subtração3: " + num1); // Subtração3: 1
```

4. **Multiplicação:**
Para multiplicação, usamos o operador `*`. Novamente, você pode multiplicar valores diretamente ou atribuir o resultado a uma variável.

```javascript
resultado = num1 * num2;                      //armazena o resultado 6
console.log("Multiplicação1: " + resultado); // Multiplicação1: 6

console.log("Multiplicação2: " + (num1 * num2)); // Multiplicação2: 6
```

Forma abreviada com `*=`:
```javascript
num1 *= num2;                            // num1 = num1 * num2
console.log("Multiplicação3: " + num1); // Multiplicação3: 6 
```

5. **Divisão:**
A divisão é feita com o operador `/`. Você pode dividir valores diretamente ou atribuir o resultado a uma variável.

```javascript
resultado = num1 / num2;                   // armazena o resultado 1.5
console.log("Divisão1: " + resultado);     // Divisão1: 1.5

console.log("Divisão2: " + (num1 / num2)); // Divisão2: 1.5
```

Forma abreviada com `/=`:
```javascript
num1 /= num2;                      // num1 = num1 / num2
console.log("Divisão3: " + num1);  // Divisão3 = 1.5 
```

6. **Resto da Divisão (Módulo):**
O operador `%` é usado para calcular o resto da divisão entre dois números.

```javascript
resultado = num1 % num2;                 // armazena o resultado 1
console.log("Resto1: " + resultado);     // Resto1: 1 

console.log("Resto2: " + (num1 % num2)); // Resto2: 1
```

Forma abreviada com `%=`:
```javascript
num1 %= num2;                   // num1 = num1 % num2
console.log("Resto3: " + num1); // Resto3: 1
```

7. **Potenciação:**
A potenciação é feita com o operador `**`. Você pode elevar um número a uma potência específica.

```javascript
resultado = num1 ** num2;                       // armazena o resultado 9
console.log("Potenciação1: " + resultado);      // Potenciação1: 9 

console.log("Potenciação2: " + (num1 ** num2)); // Potenciação2: 9
```

Forma abreviada com `**=`:
```javascript
num1 **= num2;                         // num1 = num1 ** num2
console.log("Potenciação3: " + num1); // Potenciação3: 9
```

Essas operações aritméticas são fundamentais na programação e são amplamente usadas para realizar cálculos e manipulações de dados em JavaScript. É importante entender como aplicá-las corretamente para resolver problemas e desenvolver aplicativos eficazes.

## Incrementação e Decrementação
Em JavaScript, os operadores de incremento e decremento são usados para aumentar ou diminuir o valor de uma variável em uma unidade. Eles podem ser usados tanto em uma forma "pós-processada" quanto em uma forma "pré-processada". Vamos entender como funcionam esses operadores e as diferenças entre eles.

1. **Incremento Pós-processado (Postfix Increment):**
No incremento pós-processado, o valor da variável é aumentado após a utilização do valor original em uma operação. Isso significa que a variável é usada em sua forma atual antes de ser incrementada.

```javascript
resultado = num1++; // num1 = num1 + 1
```

Nesse caso, `resultado` receberá o valor atual de `num1`, e somente depois disso, `num1` será incrementada em 1. Em outras palavras, o valor de `resultado` será igual ao valor original de `num1` antes do incremento.

2. **Decremento Pós-processado (Postfix Decrement):**
Da mesma forma, o decremento pós-processado diminui o valor de uma variável após a utilização do valor original.

```javascript
resultado = num1--;
```

Nesse caso, `resultado` receberá o valor atual de `num1`, e depois `num1` será decrementada em 1. O valor de `resultado` será igual ao valor original de `num1` antes do decremento.

3. **Incremento Pré-processado (Prefix Increment):**
No incremento pré-processado, o valor da variável é aumentado antes de ser usado em uma operação. Isso significa que a variável é incrementada em uma unidade e, em seguida, seu valor atual é usado na operação.

```javascript
resultado = ++num1; // num1 = num1 + 1
```

Nesse caso, `num1` é incrementada em 1 antes de seu valor ser atribuído a `resultado`. Portanto, `resultado` conterá o valor de `num1` após o incremento.

4. **Decremento Pré-processado (Prefix Decrement):**
O decremento pré-processado funciona da mesma forma que o incremento pré-processado, mas diminui o valor da variável antes de usá-lo em uma operação.

```javascript
resultado = --num1;
```

Nesse caso, `num1` é decrementada em 1 antes de seu valor ser atribuído a `resultado`. Portanto, `resultado` conterá o valor de `num1` após o decremento.

## Radiciação e Porcentagem
1. **Radiciação:** 
A radiciação é o processo de calcular a raiz de um número. No JavaScript, o operador `**` é usado para calcular raízes. No exemplo fornecido, temos um número `num1` igual a 25 e uma variável `raiz` igual a 3. Estamos calculando a raiz cúbica de 25, que é representada como 25^(1/3).
   
   ```javascript
num1 = 25;
raiz = 3;

resultado = num1 ** (1 / raiz); // armazena a raiz cúbica de 25 =~ 2.924
console.log("Raiz 'n'-ésima: " + resultado); // Raiz 'n'-ésima: 2.924
```

2. **Porcentagem:**
A porcentagem é uma maneira de expressar uma parte de um número como uma fração de 100. No exemplo fornecido, queremos calcular 10% de 640.

Para calcular uma porcentagem de um número, podemos usar a seguinte fórmula:

``` javascript
"x = (percentual * número) / 100" // fórmula padrão

x = (10 * 640) / 100              // No caso de calcular 10% de 640

x = (0.1 * 640)                   // Simplificado x = 64
```

A porcentagem é amplamente utilizada em muitos contextos, como descontos, cálculos de juros e representação de partes de um todo. Esses cálculos podem ser facilmente realizados em JavaScript usando a fórmula mencionada.

## Biblioteca Math
A biblioteca Math é um recurso fundamental do JavaScript que fornece funções matemáticas prontas para uso. Neste código, estão sendo utilizadas algumas dessas funções:

1. **Math.PI:** A constante `Math.PI` fornece o valor da constante matemática Pi (π), que é aproximadamente 3.14159.

```javascript
var pi = Math.PI;        // armazena o pi
console.log("PI " + pi); // PI 3.141592653589793
```

2. **Math.pow:** A função `Math.pow` é usada para calcular a potência de um número. No exemplo, estamos elevando 5 à sexta potência.

```javascript
resultado = Math.pow(5, 6);           // armazena a potencia de 5^6
console.log("Math.pow " + resultado); // Math.pow 15625
```

3. **Math.sqrt:** A função `Math.sqrt` calcula a raiz quadrada de um número. Estamos calculando a raiz quadrada de 25.

```javascript
resultado = Math.sqrt(25);             // armazena a raiz quadrada de ²√25
console.log("Math.sqrt " + resultado); // Math.sqrt 5
```

4. **Math.cbrt:** A função `Math.cbrt` é usada para calcular a raiz cúbica de um número. Estamos calculando a raiz cúbica de 27.

```javascript
resultado = Math.cbrt(27);             // armazena a raiz cubica de ³√27
console.log("Math.cbrt " + resultado); // Math.cbrt 3
```

5. **Math.random:** A função `Math.random` gera um número pseudoaleatório entre 0 (inclusive) e 1 (exclusivo). Para obter um número aleatório em um intervalo específico, multiplicamos o valor retornado por `Math.random` pelo intervalo desejado e, opcionalmente, convertemos para um número inteiro com `parseInt`. 

```javascript
var numRand = parseInt(Math.random() * 10); // entre 0 e 9
console.log("Num Randomico " + numRand);
```