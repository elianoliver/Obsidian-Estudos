
---
# Palavra Específica

O caractere ou palavra que queremos encontrar é escrito diretamente. É semelhante a um processo de busca normal. Por exemplo, para encontrar a palavra curioso no texto, escreva a mesma.

![[Pasted image 20250609230433.png]]

# Ponto . Qualquer caractere

O ponto . permite selecionar qualquer caractere, incluindo caracteres especiais e espaços.

![[Pasted image 20250609230857.png]]
# Conjuntos de caracteres [abc]

Se um dos caracteres em uma palavra pode ser vários caracteres, escrevemos dentro de colchetes [] com todos os caracteres alternativos. Por exemplo, para escrever uma expressão que pode encontrar todas as palavras no texto, escreva os caracteres a, e, i, o, u consecutivamente dentro dos colchetes [].

![[Pasted image 20250609231032.png]]

# Conjuntos de caracteres negados [^abc]

Para encontrar todas as palavras no texto abaixo, exceto ber e bor, escreva e e o lado a lado após o caractere circunflexo ^ dentro dos colchetes [].

![[Pasted image 20250609231312.png]]

# Intervalo de letras [a-z]

Para encontrar letras em um intervalo especificado, a letra inicial e a letra final são escritas dentro de colchetes [] com um hífen - entre elas. É sensível a maiúsculas e minúsculas. Escreva a expressão que selecionará todas as letras minúsculas entre e e o, incluindo elas.

![[Pasted image 20250609231414.png]]

# Intervalo de números [0-9]

Para encontrar números em um intervalo especificado, o número inicial e o número final são escritos dentro de colchetes [] com um hífen - entre eles. Escreva uma expressão que selecionará todos os números entre 3 e 6, incluindo eles.

![[Pasted image 20250609231506.png]]

# Correspondência Gananciosa

Regex faz uma correspondência gananciosa por padrão. Isso significa que a correspondência será o mais longa possível. Veja o exemplo abaixo. Ele se refere a qualquer correspondência que termine em r e pode ser qualquer caractere precedido por ela. Mas não para na primeira letra r.

![[Pasted image 20250610002421.png]]

# Correspondência Preguiçosa

A correspondência preguiçosa, ao contrário da correspondência gananciosa, para na primeira correspondência. Por exemplo, no exemplo abaixo, adicione um ? após * para encontrar a primeira correspondência que termine com a letra r e seja precedida por qualquer caractere. Significa que essa correspondência vai parar na primeira letra r.

![[Pasted image 20250610002555.png]]

