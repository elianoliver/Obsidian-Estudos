---
Livro: "[[Bhargava - Entendendo Algoritmos.pdf]]"
cssclasses:
  - rounded-images
tags:
  - EntendendoAlgoritmos
---
---

Tabelas hash são uma das estruturas de dados mais rápidas para operações de busca, inserção e remoção, alcançando complexidade de tempo **O(1)** no melhor caso. Em Python, as tabelas hash são implementadas através de dicionários (`dict`), onde cada chave é mapeada para um valor por meio de uma função de hash.

# Definição
Uma tabela hash usa uma **função de hash** para converter uma chave em um índice de um array, onde o valor associado àquela chave será armazenado. Isso permite um acesso quase instantâneo aos dados, já que, em vez de percorrer toda a estrutura, podemos ir diretamente à posição do array correspondente à chave.

```python
# Criando um dicionário (tabela hash em Python)
tabela_hash = {
    'chave1': 'valor1',
    'chave2': 'valor2'
}

# Acessando um valor usando uma chave
print(tabela_hash['chave1'], tabela_hash['chave2'])  # Saída: valor1 valor2
```

Aqui, `chave1` é processada por uma função de hash que a mapeia para uma posição no array interno do dicionário, permitindo acesso direto ao valor associado.

# Utilização
Tabelas hash são ideais para situações que requerem buscas rápidas, como implementações de dicionários (mapas), cache de dados e verificação de duplicatas. Suas operações principais (busca, inserção, remoção) podem ser realizadas em tempo constante **O(1)** no melhor caso.

Por exemplo, podemos usar uma tabela hash para contar a frequência de palavras em um texto:

```python
texto = "este é um exemplo de texto de exemplo"
palavras = texto.split()
frequencia = {}

# Contando a frequência de cada palavra
for palavra in palavras:
    if palavra in frequencia:
        frequencia[palavra] += 1
    else:
        frequencia[palavra] = 1

print(frequencia)
# Saída: {'este': 1, 'é': 1, 'um': 1, 'exemplo': 2, 'de': 2, 'texto': 1}
```

# Checagem de Duplicatas
Usando tabelas hash, a checagem de duplicatas pode ser feita de forma eficiente. Ao inserir um item, verificamos se ele já existe na tabela hash antes de prosseguir.

Exemplo de como verificar duplicatas em uma lista:

```python
numeros = [1, 2, 3, 2, 4, 5, 3]
tabela_hash = {}
duplicatas = []

# Verificando duplicatas
for num in numeros:
    if num in tabela_hash:
        duplicatas.append(num)
    else:
        tabela_hash[num] = True

print(duplicatas)  # Saída: [2, 3]
```

Aqui, verificamos rapidamente se um número já está presente no dicionário. Se estiver, ele é uma duplicata.

# Colisões
As **colisões** ocorrem quando duas chaves diferentes são mapeadas para o mesmo índice na tabela hash. Embora sejam raras com uma boa função de hash, existem mecanismos para lidar com elas. Uma abordagem comum é o **encadeamento**, onde cada bucket da tabela armazena uma lista de pares chave-valor.

Python lida com colisões automaticamente em seus dicionários, mas podemos ilustrar a ideia manualmente:

```python
tabela_hash = {
    0: [('chave1', 'valor1')],
    1: [('chave2', 'valor2')]
}

# Ao ocorrer uma colisão, simplesmente adicionamos o novo par chave-valor na lista
tabela_hash[1].append(('chave3', 'valor3'))
```

Aqui, `chave2` e `chave3` colidem, então armazenamos ambos na mesma posição como uma lista de pares.

```
{
	0: [('chave1', 'valor1')], 
	1: [('chave2', 'valor2'), ('chave3', 'valor3')]
}
```

# Desempenho (Comparação com Listas e Arrays)
Tabelas hash oferecem uma complexidade de **O(1)** no melhor caso para buscas, inserções e remoções, enquanto listas e arrays têm uma complexidade de **O(n)** para buscas e remoções, pois é necessário percorrer todos os elementos.

| Estrutura                 | Busca (Best Case) | Busca (Worst Case) | Inserção (Best Case) | Inserção (Worst Case) | Remoção (Best Case) | Remoção (Worst Case) |
| ------------------------- | ----------------- | ------------------ | -------------------- | --------------------- | ------------------- | -------------------- |
| **Tabela Hash**           | **O(1)**          | **O(n)**           | **O(1)**             | **O(n)**              | **O(1)**            | **O(n)**             |
| **Lista** (Não Ordenada)  | **O(n)**          | **O(n)**           | **O(1)**             | **O(n)**              | **O(n)**            | **O(n)**             |
| **Lista** (Ordenada)      | **O(n)**          | **O(n)**           | **O(n)**             | **O(n)**              | **O(n)**            | **O(n)**             |
| **Array** (Não Ordenado)  | **O(n)**          | **O(n)**           | **O(1)**             | **O(n)**              | **O(n)**            | **O(n)**             |
| **Array** (Ordenado)***** | **O(log n)**      | **O(n)**           | **O(n)**             | **O(n)**              | **O(n)**            | **O(n)**             |

Exemplo de busca em uma lista (ineficiente):

```python
numeros = [1, 2, 3, 4, 5]
# O(n) - percorre a lista até encontrar o número
print(3 in numeros)  # Saída: True
```

Busca em uma tabela hash (eficiente):

```python
tabela_hash = {1: 'um', 2: 'dois', 3: 'três', 4: 'quatro', 5: 'cinco'}
# O(1) - acesso direto pela chave
print(3 in tabela_hash)  # Saída: True
```

Em listas, a busca exige percorrer cada elemento até encontrar o alvo, resultando em tempo linear **O(n)**. Já em tabelas hash, acessamos o valor diretamente através da chave, com tempo constante **O(1)**.

# Fator de Carga
O **fator de carga** é a relação entre o número de elementos na tabela e o tamanho total da tabela. Ele afeta diretamente o desempenho da tabela hash. Se o fator de carga for muito alto, a chance de colisões aumenta, degradando o desempenho. Muitas implementações de tabelas hash redimensionam a tabela conforme o fator de carga cresce, mantendo um bom desempenho.

Exemplo de aumento de fator de carga:

```python
tabela_hash = {i: i for i in range(10)}
# Fator de carga inicialmente 10/16 (se a tabela tiver 16 buckets)
# Quando a tabela atinge um certo fator de carga (por exemplo, 75%), ela pode ser redimensionada.
```

Em Python, o dicionário internamente se redimensiona automaticamente para evitar que o fator de carga se torne muito alto.

# Conclusão
Tabelas hash são extremamente rápidas e eficientes, especialmente em situações onde é necessário acessar ou armazenar dados com tempo constante **O(1)**. Entretanto, é importante gerenciar colisões e o fator de carga adequadamente para garantir esse desempenho em grandes volumes de dados.