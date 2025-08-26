---
tags:
  - EntendendoAlgoritmos
---
---
## O que é Programação Dinâmica?
Imagine que você está montando um quebra-cabeça complexo. Em vez de tentar todas as peças aleatoriamente, você:
1. Separa por cores
2. Monta as bordas primeiro
3. Guarda as partes já montadas

Programação Dinâmica é exatamente isso: uma técnica onde dividimos um problema grande em partes menores, resolvemos cada parte uma única vez e guardamos as soluções para usar depois.

## Entendendo com uma História
Imagine que você está descendo uma escada e pode dar passos de 1 ou 2 degraus por vez. De quantas maneiras diferentes você pode chegar ao térreo?

```python
# Forma ruim (recursiva simples)
def descer_escada_ruim(n):
    if n <= 1:
        return 1
    return descer_escada_ruim(n-1) + descer_escada_ruim(n-2)

# Forma boa (com programação dinâmica)
def descer_escada_pd(n):
    if n <= 1:
        return 1
    
    # Criamos uma "memória" para guardar resultados
    memoria = [0] * (n + 1)
    memoria[0] = 1  # Base: tem 1 jeito de descer 0 degraus
    memoria[1] = 1  # Base: tem 1 jeito de descer 1 degrau
    
    # Para cada degrau, somamos as possibilidades
    for degrau in range(2, n + 1):
        memoria[degrau] = memoria[degrau-1] + memoria[degrau-2]
    
    return memoria[n]

# Testando
degraus = 5
print(f"Existem {descer_escada_pd(degraus)} maneiras de descer {degraus} degraus")
```

## Por que é melhor que Recursão Simples?

Vamos pensar no problema da escada com 5 degraus:
1. **Recursão Simples**: Recalcula os mesmos valores várias vezes
2. **Programação Dinâmica**: Calcula uma vez e guarda o resultado

```
Recursão (muitas repetições):
5 -> (4,3) -> (3,2,2,1) -> (2,1,1,1,1,0) ...

PD (calculamos cada número uma vez só):
1 -> 2 -> 3 -> 4 -> 5
```

## Exemplo Prático: Sequência de Fibonacci
Todo mundo já ouviu falar da sequência: 1, 1, 2, 3, 5, 8, 13...
Cada número é a soma dos dois anteriores.

```python
def fibonacci_pd(n):
    # Se n é pequeno, retornamos direto
    if n <= 1:
        return n
        
    # Criamos nossa "memória"
    memoria = [0] * (n + 1)
    memoria[1] = 1  # Definimos os casos base
    
    # Calculamos cada número uma única vez
    for i in range(2, n + 1):
        memoria[i] = memoria[i-1] + memoria[i-2]
        
    return memoria[n]

# Vamos ver funcionando
for i in range(10):
    print(f"Fibonacci({i}) = {fibonacci_pd(i)}")
```

## Exemplo do Mundo Real: Planejando uma Viagem
Imagine que você tem várias cidades para visitar e quer gastar o mínimo possível. Cada viagem entre cidades tem um custo:

```python
def menor_custo_viagem(custos):
    n = len(custos)
    # Criamos uma tabela para guardar os menores custos
    menor_custo = [float('inf')] * n
    menor_custo[0] = 0  # Começamos na primeira cidade
    
    # Para cada cidade
    for cidade_atual in range(n):
        # Olhamos para as próximas cidades possíveis
        for proxima_cidade in range(cidade_atual + 1, min(cidade_atual + 3, n)):
            # Atualizamos o custo se encontrarmos um caminho mais barato
            custo = menor_custo[cidade_atual] + custos[proxima_cidade]
            if custo < menor_custo[proxima_cidade]:
                menor_custo[proxima_cidade] = custo
    
    return menor_custo[-1]

# Exemplo de uso
custos_cidades = [0, 3, 2, 4, 6, 1, 2]
print(f"Menor custo da viagem: {menor_custo_viagem(custos_cidades)}")
```

## Quando Usar Programação Dinâmica?

Use quando seu problema tiver estas características:
1. **Subproblemas Repetidos**: Você precisa calcular a mesma coisa várias vezes
2. **Decisões Conectadas**: Cada decisão afeta as possibilidades futuras
3. **Resultado Ótimo**: Você quer encontrar a melhor solução possível

## Dicas para Resolver Problemas com PD

1. **Comece Pequeno**: 
   - Resolva primeiro para números pequenos
   - Procure padrões
   - Identifique os casos base

2. **Visualize**:
   - Faça desenhos
   - Use tabelas
   - Escreva os passos

3. **Guarde Resultados**:
   - Use uma lista ou dicionário como "memória"
   - Evite calcular a mesma coisa duas vezes

## Exercício Prático para Treinar
Vamos resolver o problema da "soma máxima contígua": dado um array de números, encontre a sequência contígua que soma o maior valor.

```python
def soma_maxima(array):
    n = len(array)
    # Para cada posição, guardamos a maior soma que termina ali
    maior_soma = [0] * n
    maior_soma[0] = array[0]
    
    # Para cada posição
    for i in range(1, n):
        # Decidimos se começamos uma nova sequência ou continuamos a anterior
        maior_soma[i] = max(array[i], maior_soma[i-1] + array[i])
    
    return max(maior_soma)

# Testando
numeros = [-2, 1, -3, 4, -1, 2, 1, -5, 4]
print(f"A maior soma possível é: {soma_maxima(numeros)}")
```

## Resumindo:
1. Dividimos o problema em partes menores
2. Resolvemos cada parte uma única vez
3. Guardamos os resultados para usar depois
4. Construímos a solução final usando esses resultados