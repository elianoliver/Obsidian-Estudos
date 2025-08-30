A programação funcional é uma abordagem para escrever código que busca torná-lo **mais limpo, previsível, fácil de testar e de corrigir (debugar)**. Ela se baseia em alguns princípios fundamentais, como o uso de **funções puras** e a **evitação de efeitos colaterais**. Vamos explorar esses conceitos de forma simples e com exemplos.

## 1. Funções Puras

Uma **função pura** é como uma máquina confiável: **dada a mesma entrada, ela sempre produz a mesma saída** e **não altera nada fora dela mesma**. Isso significa que ela não depende de variáveis externas nem modifica o estado do programa.

**Exemplo de função pura**:
```javascript
function add(a, b) {
  return a + b;
}
```
- **Por que é pura?**
  - Se você chamar `add(2, 3)`, o resultado será **sempre 5**.
  - A função não altera nada fora dela (como variáveis globais ou arquivos).
  - Ela é previsível e fácil de testar.

**Exemplo de função impura**:
```javascript
let total = 0;
function addToTotal(value) {
  total += value; // Modifica a variável externa "total"
  return total;
}
```
- **Por que é impura?**
  - O resultado de `addToTotal(5)` depende do valor de `total` antes da chamada.
  - Por exemplo, se `total` for 10, o resultado será 15; se for 20, o resultado será 25.
  - Essa dependência de algo externo torna a função **imprevisível** e difícil de testar.

## 2. Efeitos Colaterais

Um **efeito colateral** é qualquer mudança que uma função causa no **estado do programa** ou no **mundo externo** (como modificar uma variável externa, escrever em um arquivo, fazer uma chamada de API ou exibir algo no console).

- **Funções puras** não têm efeitos colaterais.
- **Funções impuras** têm efeitos colaterais, o que pode complicar o entendimento e manutenção do código.

**Exemplo de função com efeito colateral**:
```javascript
function greet(name) {
  console.log(`Hello, ${name}!`); // Interage com o console (mundo externo)
}
```
- Aqui, a função `greet` tem um efeito colateral porque **escreve no console**.
- Isso significa que ela não apenas retorna um valor, mas também causa uma mudança fora dela.

**Como torná-la pura**:
```javascript
function greet(name) {
  return `Hello, ${name}!`; // Apenas retorna o valor
}
console.log(greet("Alice")); // O console.log é separado
```
- Agora, `greet` é pura porque apenas retorna uma string, sem alterar nada fora.
치는
- O efeito colateral (exibir no console) é tratado fora da função, tornando o código mais previsível.

## 3. Princípios da Programação Funcional

A programação funcional incentiva práticas que tornam o código mais **modular** e **fácil de manter**. Aqui estão os principais pontos:

- **Funções que fazem uma coisa só**: Cada função deve ter uma única responsabilidade e fazer isso bem. Por exemplo, uma função que calcula algo não deve também exibir resultados no console.
  
- **Evitar efeitos colaterais**: Minimizar mudanças no estado do programa ou interações com o mundo externo ajuda a manter o código previsível.
  
- **Composição de funções**: O código é construído combinando funções puras, como peças de um quebra-cabeça. Isso torna o programa mais fácil de entender e testar.

## Por que isso é importante?

Quando usamos funções puras e evitamos efeitos colaterais:

- O código fica **mais previsível**: Você sabe exatamente o que uma função faz, sem surpresas.
  
- É **mais fácil de testar**: Como o resultado de uma função pura depende apenas de suas entradas, testar é simples.
  
- É **mais fácil de manter**: Funções pequenas e bem definidas são mais fáceis de corrigir ou reutilizar.

## Resumo Final

**Programação funcional** é um jeito de programar que foca em:

- **Funções puras**: Sempre retornam o mesmo resultado para as mesmas entradas e não alteram nada fora delas.
  
- **Evitar efeitos colaterais**: Reduzir mudanças no estado do programa ou interações com o mundo externo.
  
- **Código modular**: Dividir o programa em funções pequenas e previsíveis que podem ser combinadas.

**Exemplo prático**:
Em vez de escrever uma função que calcula e exibe um resultado ao mesmo tempo, separamos as responsabilidades:
```javascript
// Função pura para calcular
function calculateTotal(price, quantity) {
  return price * quantity;
}

// Função para exibir (com efeito colateral)
function displayTotal(total) {
  console.log(`Total: ${total}`);
}

const total = calculateTotal(10, 3); // 30
displayTotal(total); // Exibe "Total: 30"
```

Essa separação torna o código mais claro, reutilizável e fácil de testar.
