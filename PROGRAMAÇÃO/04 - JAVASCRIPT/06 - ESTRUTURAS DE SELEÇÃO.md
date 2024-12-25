As estruturas de seleção em JavaScript são utilizadas para controlar o fluxo do programa, permitindo a execução de diferentes blocos de código com base em condições específicas. 

**Estrutura de Seleção Simples:**
```javascript
var idade = 18;

if (idade > 18) {
    console.log("É maior de idade");
}
```

Nesse exemplo, usamos a estrutura `if` para verificar se a variável `idade` é maior que 18. Se a condição for verdadeira, o código dentro do bloco `if` é executado.

**Estrutura de Seleção Composta:**
```javascript
var num = 25;

if (num < 10 || (num > 23 && num < 50)) {
    console.log("O número é menor que 10 ou está no intervalo entre 23 e 50");
}
```

Aqui, usamos operadores lógicos (`||` para OR e `&&` para AND) para criar uma expressão condicional composta. O bloco de código é executado se uma das condições, **num<10** ou **(num>23 e num<50)** for verdadeira.

**Estrutura de Seleção Encadeada:**
```javascript
var menu = 3

if (menu == 0) {
	console.log("Opcao 0 selecionada");
} else {
	if (menu == 1) {
		console.log("Opcao 1 selecionada");
	else {
		if (menu == 2) {
			console.log("Opcao 2 selecionada");
		} else {
			if (menu == 3) {
				console.log("Opcao 3 selecionada");
			} else {
				console.log("Opção Inválida")
			}
		}
	}
}
```

Nesse caso, estamos usando múltiplos blocos `if else` aninhados para testar várias condições. A primeira condição verdadeira ativa o bloco correspondente e, se nenhuma for verdadeira, o bloco `else` final é executado.

**Estrutura de Seleção Encadeada usando IF-ELSE:**
Aqui, usamos uma estrutura mais limpa para a seleção encadeada, que é mais legível do que aninhar vários blocos `if-else`.

```javascript
if (menu == 0) {
    console.log("Opção 0 selecionada");
} else if (menu == 1) {
    console.log("Opção 1 selecionada");
} else if (menu == 2) {
    console.log("Opção 2 selecionada");
} else if (menu == 3) {
    console.log("Opção 3 selecionada");
} else {
    console.log("Opção Inválida");
}
```

**Switch-Case:**
```javascript
switch (menu) {
    case 0:
        console.log("Opção 0 selecionada");
        break;
    case 1:
        console.log("Opção 1 selecionada");
        break;
    case 2:
        console.log("Opção 2 selecionada");
        break;
    case 3:
        console.log("Opção 3 selecionada");
        break;
    default:
        console.log("Opção Inválida");
        break;
}
```

O `switch` é uma estrutura que permite comparar um valor a vários casos. Quando o valor se encaixa em um dos casos, o código desse caso é executado. O `default` é executado se nenhum caso for correspondido.

**Operador Ternário:**
```javascript
var opcao = (menu == 0) ? "ternário verdadeiro" : "ternário falso";
console.log(opcao);
```

O operador ternário é uma maneira concisa de realizar uma seleção. Se a condição entre parênteses for verdadeira, o primeiro valor após `?` é retornado; caso contrário, o segundo valor após `:` é retornado.

Essas estruturas de seleção permitem que você controle o fluxo do seu programa com base em condições específicas, permitindo a execução de blocos de código diferentes, dependendo das circunstâncias. São ferramentas fundamentais para criar lógica e interatividade em seus programas JavaScript.