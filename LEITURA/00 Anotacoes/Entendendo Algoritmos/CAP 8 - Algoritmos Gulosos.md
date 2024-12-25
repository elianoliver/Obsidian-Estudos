---
tags:
  - EntendendoAlgoritmos
---
---
## O que é um Algoritmo Guloso?
Um algoritmo guloso é uma estratégia de resolução de problemas que faz a escolha localmente ótima em cada etapa, esperando encontrar uma solução global ótima. Em outras palavras, ele sempre escolhe a melhor opção disponível no momento, sem se preocupar com as consequências futuras.

## Analogia do Dia a Dia
Imagine que você está subindo uma montanha e em cada passo precisa escolher qual caminho seguir. A estratégia gulosa seria: "Sempre escolha o caminho que leva mais para cima". Parece bom, certo? Às vezes funciona, mas nem sempre esse é o melhor caminho para chegar ao topo!

## Exemplo 1: Problema do Troco
Vamos começar com um exemplo clássico: dar troco usando o menor número possível de moedas.

```python
def troco_guloso(valor, moedas):
    moedas = sorted(moedas, reverse=True)  # Ordena as moedas em ordem decrescente
    troco = []
    for moeda in moedas:
        while valor >= moeda:
            troco.append(moeda)
            valor -= moeda
    return troco

# Exemplo de uso
valor = 26
moedas_disponiveis = [1, 5, 10, 25]
resultado = troco_guloso(valor, moedas_disponiveis)
print(f"Para dar troco de {valor} centavos, use as moedas: {resultado}")
# Saída: Para dar troco de 26 centavos, use as moedas: [25, 1]
```

Neste exemplo, o algoritmo:
1. Sempre escolhe a maior moeda possível
2. Subtrai do valor total
3. Repete até zerar o valor

## Exemplo 2: Problema da Mochila Fracionária
Imagine que você tem uma mochila com capacidade limitada e vários itens com diferentes pesos e valores. Na versão fracionária, você pode levar frações dos itens.

```python
def mochila_fracionaria(capacidade, itens):
    # Calcula valor por unidade de peso
    itens_valor_peso = [(i, item[1] / item[0]) for i, item in enumerate(itens)]
    # Ordena por valor/peso
    itens_valor_peso.sort(key=lambda x: x[1], reverse=True)
    
    valor_total = 0
    mochila = [0] * len(itens)
    
    for i, valor_peso in itens_valor_peso:
        if capacidade <= 0:
            break
            
        peso_item = itens[i][0]
        valor_item = itens[i][1]
        
        if peso_item <= capacidade:
            # Pega o item inteiro
            mochila[i] = 1
            valor_total += valor_item
            capacidade -= peso_item
        else:
            # Pega fração do item
            fracao = capacidade / peso_item
            mochila[i] = fracao
            valor_total += valor_item * fracao
            capacidade = 0
            
    return valor_total, mochila

# Exemplo de uso
# Lista de tuplas (peso, valor)
itens = [(10, 60), (20, 100), (30, 120)]
capacidade_mochila = 50

valor, solucao = mochila_fracionaria(capacidade_mochila, itens)
print(f"Valor máximo obtido: {valor}")
print(f"Frações dos itens a serem levados: {solucao}")
```

## Características dos Algoritmos Gulosos

1. **Escolha Gulosa**: Faz a melhor escolha possível no momento atual
2. **Sem Volta Atrás**: Depois de fazer uma escolha, não reconsidera
3. **Subproblema**: Resolve o problema restante com as escolhas disponíveis

## Quando Usar?
Algoritmos gulosos são bons quando:
- O problema tem "propriedade gulosa" (escolhas locais levam à solução ótima)
- O problema pode ser dividido em subproblemas independentes
- A solução não precisa ser necessariamente ótima, mas "boa o suficiente"

## Vantagens e Desvantagens

**Vantagens:**
- Simples de implementar
- Geralmente rápidos
- Bons para soluções aproximadas

**Desvantagens:**
- Nem sempre encontra a solução ótima
- Pode falhar completamente em alguns casos
- Difícil provar se a solução é ótima

