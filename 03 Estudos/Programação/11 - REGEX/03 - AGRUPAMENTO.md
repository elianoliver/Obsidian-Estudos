
# Parênteses ( )

Podemos agrupar uma expressão e usar esses grupos para fazer referência ou impor algumas regras. Para agrupar uma expressão, a envolvemos () em parênteses. Por enquanto, apenas agrupamos haa abaixo.

![[Pasted image 20250609233641.png]]

# Referenciando um grupo

As palavras ha e haa são agrupadas abaixo. O primeiro grupo é usado escrevendo \1 para evitar reescrevê-lo. Aqui 1 denota a ordem do agrupamento. Escreva \2 no final de uma expressão para se referir ao segundo grupo.

![[Pasted image 20250609233800.png]]

# Parênteses (?: ): Agrupamento Não Capturado

Você pode agrupar uma expressão e garantir que ela não seja capturada por referências. Por exemplo, abaixo há dois grupos. No entanto, a primeira referência do grupo é denotada por \1 na verdade aponta para o segundo grupo, já que o primeiro é um grupo desconhecido.

(não entendi pq ele continuou pegando o primeiro grupo)
![[Pasted image 20250609234741.png]]

# Caractere Pipe |

Permite especificar que uma expressão pode estar em diferentes expressões. Portanto, todas as declarações possíveis são escritas separadas pelo caractere Pipe |. 

Isso difere do charset [abc], os charsets funcionam em nível de caractere. As alternativas estão em nível de expressão. 

Por exemplo, a seguinte expressão selecionaria tanto cat quanto rat. Adicione outro caractere pipe | no final de uma expressão e escreva dog para que todas as palavras sejam selecionadas.

![[Pasted image 20250609235608.png]]

# Caractere de Escape \

Existem caracteres especiais que usamos ao escrever Regex. { } [ ] / \ + * . $^ | ? Antes de podermos selecionar esses caracteres, precisamos usar um caractere de escape \. Por exemplo, para selecionar os caracteres ponto . e asterisco * no texto, adicionamos o caractere de escape \ antes deles.

![[Pasted image 20250609235724.png]]

# Sinal de Circunflexo ^: Seleção por Início de Linha

Estamos usando [0-9] para encontrar números. Para encontrar apenas números no início de uma linha, prefixamos essa expressão com o sinal de circunflexo ^.

![[Pasted image 20250609235913.png]]

# Sinal de Cifrão $: Seleção por Fim de Linha

Use o sinal de cifrão $ após o valor html para encontrar o texto html apenas no final da linha.

![[Pasted image 20250610000006.png]]

# Caractere de Palavra \w: Letras, Números e Sublinhado

A expressão \w é usada para encontrar letras, números e sublinhados. Vamos usar a expressão \w para encontrar o caractere de palavra no texto.

![[Pasted image 20250610000055.png]]

# Caractere Exceto Palavra \W

A expressão \W é usada para encontrar caracteres diferentes de letras, números e sublinhados.

![[Pasted image 20250610000206.png]]

# Caractere Numérico \d

\d é usado para encontrar apenas caracteres numéricos.

![[Pasted image 20250610000254.png]]

# Exceto Caracteres Numéricos \D

\D é usado para encontrar caracteres não numéricos.

![[Pasted image 20250610000334.png]]

# Caractere de Espaço \s

\s é usado para encontrar apenas caracteres de espaço.

![[Pasted image 20250610000408.png]]

# Exceto Caractere de Espaço \S

\S é usado para encontrar caracteres que não sejam de espaço.

![[Pasted image 20250610000517.png]]

