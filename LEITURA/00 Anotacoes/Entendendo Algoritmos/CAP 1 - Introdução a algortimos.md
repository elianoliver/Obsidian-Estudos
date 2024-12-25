---
Livro: "[[Entendendo Algoritmos.pdf]]"
Youtube: https://www.youtube.com/watch?v=zyj5vOPA1vA&list=PLx4x_zx8csUir5pbqRDgFbVS-2SG7JiOu
cssclasses:
  - rounded-images
tags:
  - EntendendoAlgoritmos
---
---
# Introdução
Um algoritmo é um conjunto de instruções que realizam uma tarefa.
O livro contém diferentes tipos de algoritmos e seus casos de aplicabilidade para maior desempenho.

# Pesquisa Binária
A pesquisa binária é um algoritmo eficiente para encontrar um item em uma lista ordenada. Ela funciona dividindo repetidamente a lista ao meio e descartando a metade que não contém o item procurado. A eficiência desse processo está diretamente relacionada ao **logaritmo de base 2** (log₂).

Suponha que você esteja procurando em um dicionário uma palavra que começa com a letra "o", neste caso, você começara a buscar pelo meio do dicionário pois sabe que a letra "o" começa mais ou menos a partir dali.

Isto é uma pesquisa binária. Sua entrada é uma lista **ordenada** de elementos.

Para exemplificar sua eficiência, vamos propor um exercício. Digamos que você precise adivinhar um número aleatório de 1 à 100. Na **pesquisa simples** eliminaríamos uma à um, oque levaria muito tempo.

![[Pasted image 20241002214543.png | center]]

Já na **pesquisa binária**, conseguiríamos eliminar sempre metade das possiblidades.

![[Pasted image 20241002215220.png | center]]

# Logaritmos
De maneira geral, para uma lista de n números, a pesquisa binária precisa de log₂n para retornar o valor correto, enquanto a pesquisa simples precisa de n etapas.

A expressão log₁₀100 basicamente diz:

```
Quantos 10's conseguimos multiplicar para chegar a 100?

A resposta é 2 (10 * 10 = 100).
```

O logaritmo de base 2 representa a quantidade de vezes que uma lista pode ser dividida ao meio até sobrar apenas um elemento. Em uma lista com n elementos, a pesquisa binária faz cerca de log⁡2(n) comparações para encontrar o item ou determinar que ele não está na lista.

**EXEMPLO PRÁTICO**

Imagine que você tem uma lista com 16 elementos, e deseja encontrar um número específico usando a pesquisa binária.

- Passo 1: Divida a lista em duas partes e compare o número do meio com o número procurado.
- Passo 2: Dependendo do resultado da comparação (se o número do meio é maior ou menor que o número procurado), descarte a metade que não contém o número e repita o processo na metade restante.

Esse processo de divisão pela metade continua até que você encontre o número ou até que a lista tenha sido completamente dividida.

**QUANTAS TENTATIVAS SERIAM NECESSÁRIAS?**

A fórmula é aproximadamente log⁡2(n), onde n é o número de elementos na lista. Vamos ver alguns exemplos com números comuns:

- Se n = 16
	- log⁡2(16) = 4. Portanto, serão necessárias no máximo 4 comparações para encontrar o número ou determinar que ele não está na lista.
- Se n = 1.000
	- log⁡2(1.000) ≈ 10. Seriam necessárias, no máximo, cerca de 10 comparações.
- Se n = 1.000.000
	- log⁡2(1.000.000) ≈ 20. No máximo 20 comparações seriam suficientes para encontrar o número ou concluir que ele não está presente.

Esse é o poder da pesquisa binária — ela reduz drasticamente o número de comparações necessárias, principalmente em listas grandes.

# Notação Big O
A notação Big O descreve o desempenho de um algoritmo em termos de tempo ou espaço, à medida que o tamanho da entrada aumenta. Ela nos dá uma ideia de como o tempo de execução ou o uso de memória de um algoritmo cresce em função do número de elementos (n) processados.

## PESQUISA SIMPLES (Big O(n))

A **pesquisa simples** (ou linear) verifica cada item de uma lista, um por um, até encontrar o elemento procurado ou terminar de percorrer todos os itens. No pior caso, se o elemento procurado for o último da lista ou não estiver nela, o algoritmo terá que verificar todos os elementos. Assim, o tempo de execução da pesquisa simples é proporcional ao número de elementos, o que resulta em um desempenho de **O(n)**, ou seja, o tempo de execução aumenta linearmente à medida que a lista cresce.

## Pesquisa Binária (Big O(log n))

A **pesquisa binária** é muito mais eficiente, mas só pode ser aplicada em listas ordenadas. O algoritmo funciona dividindo a lista ao meio repetidamente, descartando a metade que não contém o item procurado. No pior caso, a pesquisa binária continua dividindo a lista até que ela tenha apenas um elemento. Como o número de divisões necessárias é logarítmico, o tempo de execução desse algoritmo é **O(log n)**. Ou seja, para uma lista de tamanho n, o número de comparações necessárias será proporcional ao logaritmo de n.

Comparando os dois:
- Pesquisa simples: O(n) — verifica todos os elementos.
- Pesquisa binária: O(log n) — reduz a busca pela metade a cada iteração.

## Outros Exemplos de Notação Big O

**O(1)**: **Execução em tempo constante.** Um algoritmo com essa notação sempre leva a mesma quantidade de tempo, independentemente do tamanho da entrada. 
**Exemplo:** acessar um elemento específico em um array.

**O(n)**: **Execução em tempo linear.** O tempo de execução aumenta proporcionalmente ao tamanho da entrada. 
**Exemplo:** uma pesquisa simples (linear), que percorre todos os elementos de uma lista.

**O(log n)**: **Execução em tempo logarítmico.** Algoritmos que reduzem a entrada pela metade a cada iteração, como na pesquisa binária. O número de operações cresce mais lentamente em comparação com o tamanho da entrada.

**O(n * log n)**: **Execução em tempo quase linear.** Esse tipo de algoritmo realiza um número de operações que cresce mais rapidamente do que linearmente, devido ao fator logarítmico. 
**Exemplos:** algoritmos de ordenação eficientes, como Merge Sort e Quick Sort no caso médio.

**O(n²)**: **Execução em tempo quadrático.** Um algoritmo com essa notação realiza n * n operações no pior caso. 
**Exemplo:** Bubble Sort ou Insertion Sort, onde para cada elemento da lista, o algoritmo pode percorrer toda a lista novamente para fazer comparações.

**O(n!)**: **Execução em tempo fatorial.** Algoritmos que geram todas as permutações ou combinações de um conjunto de elementos. 
**Exemplo:** o problema do Caixeiro Viajante, onde a solução por força bruta examina todas as rotas possíveis para encontrar a melhor.

![[Pasted image 20241005231430.png | center ]]

Suponha que você esteja desenhando uma grade de 16 divisões e você possa escolher cinco algoritmos diferentes para fazer isso. Aqui está quanto tempo levaria para desenhar a grade com os algoritmos citados, do mais rápido ao mais lento:


