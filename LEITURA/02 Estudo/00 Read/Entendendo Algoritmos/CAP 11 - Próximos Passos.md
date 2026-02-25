---
tags:
  - EntendendoAlgoritmos
---
---
### 1) **Árvore Binária de Busca (Binary Search Tree - BST)**  
Uma árvore binária de busca é como uma árvore genealógica, onde cada "pai" tem no máximo dois "filhos". A principal regra é:  
- Todos os valores **à esquerda** do pai são **menores** que ele.  
- Todos os valores **à direita** são **maiores**.  

**Exemplo prático:**  
```
     8
   /   \
  3    10
 / \     \
1   6    14
```  
Se você quer encontrar o número **6**:  
1. Começa na raiz (**8**).  
2. Como **6 < 8**, vai para o lado esquerdo (**3**).  
3. Como **6 > 3**, vai para o lado direito.  
4. Encontrou o **6**!  

---

### 2) **Índice Invertido (Inverted Index)**  
O índice invertido é como o índice de um livro: ele conecta palavras às páginas onde elas aparecem. Assim, você encontra diretamente onde procurar, sem precisar folhear página por página.  

**Exemplo prático:**  
Documentos:  
- Doc1: "O gato pulou"  
- Doc2: "O cachorro correu"  
- Doc3: "O gato correu"  

**Índice invertido:**  
```
o: {Doc1, Doc2, Doc3}  
gato: {Doc1, Doc3}  
pulou: {Doc1}  
cachorro: {Doc2}  
correu: {Doc2, Doc3}  
```

---

### 3) **Transformada de Fourier**  
A Transformada de Fourier é uma técnica que decompõe um sinal complexo em ondas simples (senos e cossenos). É como separar uma música em suas notas individuais.  

**Exemplo prático:**  
Imagine uma música tocada ao piano. A Transformada de Fourier pode decompor a onda sonora em:  
- 440 Hz (Nota Lá)  
- 554 Hz (Nota Dó#)  
- 659 Hz (Nota Mi)  

Isso é essencial em processamento de áudio, imagens e compressão de dados.  

---

### 4) **Algoritmos Paralelos**  
Algoritmos paralelos permitem que uma tarefa seja dividida entre várias "pessoas" (processadores) trabalhando ao mesmo tempo, acelerando a execução.  

**Exemplo prático:**  
Ordenar 1000 números:  
- **Método tradicional:** Uma única pessoa ordena tudo sozinha.  
- **Método paralelo:**  
  1. Pessoa 1 ordena os números de 1 a 250.  
  2. Pessoa 2 ordena de 251 a 500.  
  3. Pessoa 3 ordena de 501 a 750.  
  4. Pessoa 4 ordena de 751 a 1000.  
  5. Os resultados são combinados no final.  

---

### 5) **Filtro de Bloom e HyperLogLog**  
**Filtro de Bloom:** É como uma lista de presença que pode ter falsos positivos (algo pode parecer presente, mas não está), mas **nunca falsos negativos** (se diz que algo não está, realmente não está).  

**Exemplo prático do Filtro de Bloom:**  
Verificar se um email já está cadastrado:  
- "joao@email.com" marca posições 1, 4 e 7 como usadas.  
- Se outro email marca essas mesmas posições, pode ser falso positivo.  
- Porém, se qualquer posição não está marcada, com certeza o email é novo.  

**HyperLogLog:** Estima o número de elementos únicos em um conjunto, usando pouquíssima memória.  

**Exemplo prático do HyperLogLog:**  
Contar usuários únicos em um site:  
- Em vez de armazenar todos os IDs (que ocupariam muito espaço), ele usa um "resumo probabilístico".  
- Resultado: "Aproximadamente 1 milhão de usuários", usando apenas alguns KB.  

---

### 6) **SHA e SimHash**  
**SHA (Secure Hash Algorithm):** Gera uma "impressão digital" única para dados. Uma pequena alteração no dado gera uma hash completamente diferente.  

**Exemplo prático do SHA:**  
```python
texto1 = "olá mundo" → SHA-256: "2ef7bde608ce5404e97d5f042f95f89f1c232871"  
texto2 = "olá Mundo" → SHA-256: "9d8def6337a93bf5c5bf50a1b3495927f6542934"  
```  

**SimHash:** Focado em encontrar documentos **similares** (não idênticos).  

**Exemplo prático do SimHash:**  
Dois textos:  
- "O gato pulou o muro" → hash1  
- "O gato pulou a cerca" → hash2  
SimHash gera valores próximos, indicando que os textos são semelhantes.  

---

### 7) **Troca de Chaves Diffie-Hellman**  
A troca de chaves Diffie-Hellman permite que duas pessoas (Alice e Bob) criem uma chave secreta compartilhada sem transmiti-la diretamente.  

**Como funciona:**  
1. Alice e Bob escolhem dois números públicos visíveis para todos (ex.: base \(7\) e módulo \(11\)).  
2. Cada um escolhe um número secreto (Alice: \(3\), Bob: \(6\)).  
3. Eles trocam cálculos baseados nesses números:  
   - Alice envia: \(7^3 \mod 11 = 2\).  
   - Bob envia: \(7^6 \mod 11 = 4\).  
4. Cada um usa o valor recebido para gerar a mesma chave secreta:  
   - Alice: \(4^3 \mod 11 = 9\).  
   - Bob: \(2^6 \mod 11 = 9\).  

A chave compartilhada \(9\) é gerada de forma segura, mesmo que os números públicos sejam conhecidos.  

---

### 8) **Programação Linear**  
É uma técnica matemática usada para encontrar a solução ideal (máxima ou mínima) para problemas com restrições.  

**Exemplo prático:**  
Uma fábrica de bolos:  
- Cada bolo de chocolate usa **2 ovos** e dá lucro de **R$10**.  
- Cada bolo de baunilha usa **3 ovos** e dá lucro de **R$12**.  
- Há apenas **24 ovos disponíveis**.  

A programação linear resolve quantos bolos de cada tipo fazer para **maximizar o lucro**, respeitando a restrição de ovos.  