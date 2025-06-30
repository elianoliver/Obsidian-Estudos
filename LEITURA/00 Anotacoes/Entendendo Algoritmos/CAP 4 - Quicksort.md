---
Livro: "[[Bhargava - Entendendo Algoritmos.pdf]]"
cssclasses:
  - rounded-images
tags:
  - EntendendoAlgoritmos
---
---

Para entender o algoritmo **Quicksort** e a técnica de **dividir para conquistar**, vamos explorar conceitos fundamentais, acompanhados de exemplos em Python.

## Dividir para Conquistar: Algoritmo de Euclides

O algoritmo de Euclides é um exemplo clássico de divisão e conquista, utilizado para calcular o máximo divisor comum (MDC) de dois números. A ideia é dividir o problema em subproblemas menores até chegar à solução.

### Exemplo do Algoritmo de Euclides

Aqui está uma implementação do algoritmo de Euclides em Python:

```python
def gcd(a, b):
    while b:
        a, b = b, a % b
    return a

# Exemplo de uso do algoritmo de Euclides
num1 = 48
num2 = 18
resultado = gcd(num1, num2)
print(f"O MDC de {num1} e {num2} é: {resultado}")
```

**Saída:**

```
O MDC de 48 e 18 é: 6
```

## Soma de um Array Usando Recursão

Outra aplicação da técnica de dividir para conquistar é na soma dos elementos de um array. Em vez de usar um loop, podemos dividir o array em duas metades e somar recursivamente.

### Exemplo da Soma Recursiva

Aqui está como implementar isso em Python:

```python
def soma_array(arr):
    if len(arr) == 0:
        return 0
    elif len(arr) == 1:
        return arr[0]
    else:
        mid = len(arr) // 2
        return soma_array(arr[:mid]) + soma_array(arr[mid:])

# Exemplo de uso da função recursiva para somar um array
array = [1, 2, 3, 4, 5]
resultado_soma = soma_array(array)
print(f"A soma do array {array} é: {resultado_soma}")
```

**Saída:**

```
A soma do array [1, 2, 3, 4, 5] é: 15
```

## O Que É Quicksort?

O **Quicksort** é um algoritmo eficiente para ordenar elementos que utiliza a estratégia de dividir para conquistar. Seu funcionamento é descrito a seguir:

1. **Escolher um pivô**: Um elemento do array é escolhido como pivô.
2. **Particionamento**: O array é reorganizado para que todos os elementos menores que o pivô fiquem à esquerda e todos os maiores à direita.
3. **Recursão**: O processo se repete nas sublistas.

### Exemplo do Quicksort

Aqui está uma implementação do Quicksort em Python:

```python
def quicksort(arr):
    if len(arr) <= 1:
        return arr
    else:
        pivot = arr[len(arr) // 2]
        left = [x for x in arr if x < pivot]
        middle = [x for x in arr if x == pivot]
        right = [x for x in arr if x > pivot]
        return quicksort(left) + middle + quicksort(right)

# Exemplo de uso do Quicksort
array_quick = [40, 21, 8, 17, 51, 34]
resultado_quick = quicksort(array_quick)
print(f"O array ordenado é: {resultado_quick}")
```

**Saída:**

```
O array ordenado é: [8, 17, 21, 34, 40, 51]
```

### Explicação do Quicksort

1. **Condição de Parada**:
   - `if len(arr) <= 1: return arr` Se o array tiver um ou nenhum elemento, ele já está ordenado.

2. **Escolha do Pivô**:
   - `pivot = arr[len(arr) // 2]` Escolhemos o elemento do meio como pivô.

3. **Particionamento**:
   - `left = [x for x in arr if x < pivot]` Criamos uma lista `left` com elementos menores que o pivô.
   - `middle = [x for x in arr if x == pivot]` Criamos uma lista `middle` com elementos iguais ao pivô.
   - `right = [x for x in arr if x > pivot]` Criamos uma lista `right` com elementos maiores que o pivô.

4. **Recursão e Combinação**:
   - `return quicksort(left) + middle + quicksort(right)` Chamamos recursivamente o Quicksort nas sublistas `left` e `right`, combinando os resultados com a lista `middle`.

## Quicksort vs Merge Sort

Ambos os algoritmos utilizam a abordagem de dividir para conquistar, mas têm diferenças importantes:

| Característica     | Quicksort                                         | Merge Sort                          |
| ------------------ | ------------------------------------------------- | ----------------------------------- |
| Tipo               | In-place (não requer espaço extra)                | Não in-place (requere espaço extra) |
| Complexidade Média | $$O(n \log n)$$                                   | $$O(n \log n)$$                     |
| Complexidade Pior  | $$O(n^2)$$ (caso pior se o pivô for mal escolhido)| $$O(n \log n)$$                     |
| Estabilidade       | Instável (pode mudar a ordem dos iguais)          | Estável (mantém a ordem dos iguais) |
| Uso de Memória     | Menos memória                                     | Mais memória devido às cópias       |

### Exemplo do Merge Sort

Aqui está uma implementação do Merge Sort:

```python
def merge_sort(arr):
    if len(arr) <= 1:
        return arr
        
    mid = len(arr) // 2
    left = merge_sort(arr[:mid])
    right = merge_sort(arr[mid:])
    
    sorted_array = []
    i = j = 0
    
    while i < len(left) and j < len(right):
        if left[i] < right[j]:
            sorted_array.append(left[i])
            i += 1
        else:
            sorted_array.append(right[j])
            j += 1
            
    sorted_array.extend(left[i:])
    sorted_array.extend(right[j:])
    
    return sorted_array

# Exemplo de uso do Merge Sort
array_merge = [40, 21, 8, 17, 51, 34]
resultado_merge = merge_sort(array_merge)
print(f"O array ordenado pelo Merge Sort é: {resultado_merge}")
```

**Saída:**

```
O array ordenado pelo Merge Sort é: [8, 17, 21, 34, 40, 51]
```

### Explicação do Merge Sort

1. **Condição de Parada**:
   - `if len(arr) <= 1: return arr`  
   Se o array tiver um ou nenhum elemento, ele já está ordenado.
   
1. **Divisão do Array**:
   - `mid = len(arr) // 2` Calculamos o índice médio para dividir o array em duas metades.
   - `left = merge_sort(arr[:mid])` Chamamos recursivamente o Merge Sort na metade esquerda.
   - `right = merge_sort(arr[mid:])` Chamamos recursivamente o Merge Sort na metade direita.

2. **Mesclagem das Sublistas**:
   - Inicializamos uma lista vazia `sorted_array` para armazenar os elementos ordenados.   
   - Usamos dois índices (`i` e `j`) para percorrer as listas `left` e `right`.   
   - O loop `while` compara os elementos das duas listas e adiciona o menor à lista ordenada.

4. **Adicionando Elementos Restantes**:
   - Após sair do loop, usamos `sorted_array.extend(left[i:])` e `sorted_array.extend(right[j:])` para adicionar quaisquer elementos restantes das listas esquerda ou direita.

5. **Retorno da Lista Ordenada**:
   - Finalmente, retornamos a lista completamente ordenada.

## Conclusão

Tanto o Quicksort quanto o Merge Sort utilizam a técnica de dividir para conquistar, mas com abordagens distintas. O Quicksort realiza partições baseadas em um pivô enquanto o Merge Sort divide o array em metades e mescla as sublistas ordenadas. Ambos são eficientes na ordenação de grandes conjuntos de dados e têm características que podem torná-los mais adequados para diferentes situações.