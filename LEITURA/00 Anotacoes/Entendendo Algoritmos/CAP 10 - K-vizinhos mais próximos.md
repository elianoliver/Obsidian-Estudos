---
tags:
  - EntendendoAlgoritmos
---
---
## Entendendo o k-NN
Imagine que você está em uma cidade nova e quer saber se um bairro é seguro. Uma estratégia seria olhar para as k casas mais próximas e ver como elas são classificadas. Este é o princípio básico do k-NN!

## Como Funciona?
1. **Para Classificação**: A classe é definida por votação dos vizinhos
2. **Para Regressão**: O valor é a média (ou mediana) dos vizinhos

## Implementação Didática

```python
import numpy as np
from collections import Counter

class KNN:
    def __init__(self, k=3, tipo='classificacao'):
        """
        k: número de vizinhos
        tipo: 'classificacao' ou 'regressao'
        """
        self.k = k
        self.tipo = tipo
    
    def fit(self, X, y):
        """Memoriza os dados de treino"""
        self.X_treino = np.array(X)
        self.y_treino = np.array(y)
    
    def calcular_distancias(self, x):
        """Calcula distância euclidiana para todos os pontos"""
        return np.sqrt(np.sum((self.X_treino - x)**2, axis=1))
    
    def predict(self, X):
        X = np.array(X)
        predicoes = []
        
        for x in X:
            # 1. Calcula distâncias
            distancias = self.calcular_distancias(x)
            
            # 2. Encontra k vizinhos mais próximos
            k_indices = np.argsort(distancias)[:self.k]
            k_vizinhos = self.y_treino[k_indices]
            
            # 3. Faz a predição
            if self.tipo == 'classificacao':
                # Votação majoritária
                predicao = Counter(k_vizinhos).most_common(1)[0][0]
            else:
                # Média para regressão
                predicao = np.mean(k_vizinhos)
                
            predicoes.append(predicao)
            
        return np.array(predicoes)

```

## Exemplo de Classificação: Tipos de Flores

```python
# Dados de exemplo: comprimento da pétala e tipo de flor
X_flores = np.array([
    [1.0], [1.2], [2.5], [2.8], [4.0], [4.2]  # comprimento da pétala
])
y_flores = np.array([
    'iris_a', 'iris_a', 'iris_b', 'iris_b', 'iris_c', 'iris_c'
])

# Criando e treinando o modelo
knn_class = KNN(k=3, tipo='classificacao')
knn_class.fit(X_flores, y_flores)

# Nova flor para classificar
nova_flor = np.array([[2.6]])
predicao = knn_class.predict(nova_flor)
print(f"Tipo previsto da flor: {predicao[0]}")
```

## Exemplo de Regressão: Preços de Casas

```python
# Dados de exemplo: tamanho da casa e preço
X_casas = np.array([
    [50], [60], [80], [100], [120], [140]  # tamanho em m²
])
y_casas = np.array([
    200, 250, 300, 350, 400, 450  # preço em milhares
])

# Criando e treinando o modelo
knn_reg = KNN(k=3, tipo='regressao')
knn_reg.fit(X_casas, y_casas)

# Nova casa para prever o preço
nova_casa = np.array([[90]])
preco_previsto = knn_reg.predict(nova_casa)
print(f"Preço previsto: R$ {preco_previsto[0]:.2f} mil")
```

## Visualização dos Resultados

```python
def visualizar_knn_regressao():
    import matplotlib.pyplot as plt
    
    plt.figure(figsize=(10, 6))
    
    # Plotar dados de treino
    plt.scatter(X_casas, y_casas, color='blue', label='Dados de Treino')
    
    # Plotar previsões para vários pontos
    X_teste = np.linspace(40, 150, 100).reshape(-1, 1)
    y_pred = knn_reg.predict(X_teste)
    
    plt.plot(X_teste, y_pred, 'r-', label='Previsões k-NN')
    plt.xlabel('Tamanho da Casa (m²)')
    plt.ylabel('Preço (R$ mil)')
    plt.title('k-NN Regressão: Previsão de Preços de Casas')
    plt.legend()
    plt.grid(True)
    return plt

# Em ambiente com suporte a visualização:
# plt = visualizar_knn_regressao()
# plt.show()
```

## Técnicas Avançadas

### 1. Ponderação por Distância

```python
def predict_ponderado(self, X):
    predicoes = []
    for x in X:
        distancias = self.calcular_distancias(x)
        k_indices = np.argsort(distancias)[:self.k]
        
        # Calcula pesos (quanto mais próximo, maior o peso)
        pesos = 1 / (distancias[k_indices] + 1e-10)
        
        if self.tipo == 'regressao':
            predicao = np.average(self.y_treino[k_indices], weights=pesos)
        else:
            # Votação ponderada para classificação
            classes = self.y_treino[k_indices]
            voto_ponderado = {}
            for classe, peso in zip(classes, pesos):
                voto_ponderado[classe] = voto_ponderado.get(classe, 0) + peso
            predicao = max(voto_ponderado.items(), key=lambda x: x[1])[0]
            
        predicoes.append(predicao)
    return np.array(predicoes)
```

### 2. Normalização dos Dados

```python
def normalizar_dados(X):
    """Normaliza os dados para escala [0,1]"""
    min_vals = X.min(axis=0)
    max_vals = X.max(axis=0)
    X_norm = (X - min_vals) / (max_vals - min_vals)
    return X_norm, min_vals, max_vals
```

### 3. Validação Cruzada

```python
def validacao_cruzada(X, y, k_vizinhos, k_folds=5):
    """Realiza validação cruzada para encontrar melhor k"""
    n = len(X)
    tamanho_fold = n // k_folds
    scores = []
    
    for k in k_vizinhos:
        scores_k = []
        for i in range(k_folds):
            # Separa dados de teste
            inicio_teste = i * tamanho_fold
            fim_teste = (i + 1) * tamanho_fold
            X_teste = X[inicio_teste:fim_teste]
            y_teste = y[inicio_teste:fim_teste]
            
            # Dados de treino são o resto
            X_treino = np.concatenate([X[:inicio_teste], X[fim_teste:]])
            y_treino = np.concatenate([y[:inicio_teste], y[fim_teste:]])
            
            # Treina e avalia
            knn = KNN(k=k)
            knn.fit(X_treino, y_treino)
            pred = knn.predict(X_teste)
            
            # Calcula score
            if isinstance(y[0], (int, float)):
                # MSE para regressão
                score = np.mean((pred - y_teste) ** 2)
            else:
                # Acurácia para classificação
                score = np.mean(pred == y_teste)
            
            scores_k.append(score)
        
        scores.append(np.mean(scores_k))
    
    return k_vizinhos[np.argmax(scores)]
```

## Dicas Práticas

1. **Escolha do k**:
   - k pequeno: mais sensível a ruído
   - k grande: pode perder padrões locais
   - Use números ímpares para classificação binária

2. **Normalização**:
   - Sempre normalize features em diferentes escalas
   - Considere transformações logarítmicas para dados muito dispersos

3. **Performance**:
   - Use estruturas de dados eficientes (ex: KD-Trees) para grandes conjuntos
   - Considere redução dimensional para dados de alta dimensão

## Aplicações Práticas

1. **Classificação**:
   - Análise de risco de crédito
   - Diagnóstico médico
   - Reconhecimento de padrões

2. **Regressão**:
   - Previsão de preços
   - Estimativa de demanda
   - Análise de séries temporais
