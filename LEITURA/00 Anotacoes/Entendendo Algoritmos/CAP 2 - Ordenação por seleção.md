---
Livro: "[[Entendendo Algoritmos.pdf]]"
cssclasses:
  - rounded-images
tags:
  - EntendendoAlgoritmos
---
---
# Como funciona a memória
O computador se parece com um grande conjunto de gavetas, e cada gaveta tem seu endereço.

![[Pasted image 20241006104452.png | center]]

**feØeeb** é o endereço de um slot na memória.

Cada vez que quer armazenar um item na memória, você pede ao computador um pouco de espaço e ele te dá um endereço no qual você pode armazenar o seu item. Se quiser armazenar múltiplos itens, existem duas maneiras para fazer isso: arrays e listas.

# Arrays
Pense em um array como uma fileira de gavetas organizadas uma ao lado da outra. Cada gaveta tem um endereço específico, e todas elas estão alinhadas em sequência. Quando você cria um array, reserva uma quantidade exata de gavetas, e todos os itens são armazenados de forma ordenada, um ao lado do outro.

## Exemplo:
Se você tem um array de 5 números, o computador irá reservar 5 espaços seguidos na memória. Cada posição terá um número, e para acessá-los, basta saber em qual posição o item está.

## Vantagens:
- **Acesso rápido**: Você pode pegar qualquer item rapidamente, já que sabe exatamente onde ele está na fileira.
- **Simplicidade**: Arrays são fáceis de usar quando você já sabe quantos itens quer armazenar.

## Desvantagens:
- **Tamanho fixo**: Depois de criar um array, não dá para aumentar ou diminuir seu tamanho sem criar um novo. Ou seja, se precisar armazenar mais itens, será necessário fazer mais trabalho.
- **Inserções e deleções**: Adicionar ou remover um item no meio do array pode ser complicado, porque é necessário reorganizar todos os itens que vêm depois.

```ad-tip
Arrays são ótimos se você deseja ler elementos aleatórios, pois pode encontrar qualquer elemento instantaneamente em uma array.

Todos os elementos de um array devem ser do mesmo tipo (todos ints, doubles, e assim por diante)

- Tempo de execução de leitura O(1) imediata.
- Tempo de execução de escrita O(n) linear.
- Tempo de execução de deleção O(n) linear.
```

# Listas Encadeadas
Uma lista encadeada é diferente. Em vez de ter uma fileira de gavetas todas seguidas, cada item da lista tem uma gaveta em qualquer lugar da memória. Para garantir que os itens da lista estejam conectados, cada gaveta tem um “bilhete” que aponta para a próxima gaveta (o ponteiro para o próximo item).

## Exemplo:
Imagine que você tem uma gaveta com o número 10. Dentro dessa gaveta, além do número, há um bilhete dizendo onde está o próximo número da lista, e assim por diante.

## Vantagens:
- **Tamanho dinâmico**: Você pode adicionar ou remover itens facilmente, pois cada item está "linkado" ao próximo. Não há necessidade de reservar um grande espaço de uma vez.
- **Inserções e deleções fáceis**: Como você só precisa alterar os bilhetes (ponteiros) para adicionar ou remover um item, isso pode ser feito rapidamente. O(1) em casos específicos.

## Desvantagens:
- **Acesso mais lento**: Se você quiser acessar o último item da lista, terá que ir de gaveta em gaveta seguindo os bilhetes, o que pode demorar mais O(n).
- **Mais memória usada**: Cada gaveta da lista precisa de espaço extra para guardar o bilhete que aponta para a próxima gaveta, consumindo mais memória do que um array.

```ad-tip
Listas encadeadas são ótimas se você quiser ler todos os itens, um de cada vez.

- Tempo de execução de leitura O(n) linear.
- Tempo de execução de escrita O(1) imediata.
- Tempo de execução de deleção O(1) imediata.
```

