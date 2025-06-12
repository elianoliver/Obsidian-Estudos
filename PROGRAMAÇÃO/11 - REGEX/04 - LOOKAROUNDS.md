Se quisermos que a frase que estamos escrevendo venha antes ou depois de outra frase, precisamos de um "lookaround". Continue para aprender a usar "lookaround".

# Lookahead Positivo: (?=)

Por exemplo, queremos selecionar o valor da hora no texto. Portanto, para selecionar apenas os valores numéricos que têm PM depois deles, precisamos escrever o lookahead positivo (?=) após nossa expressão. Inclua PM após o sinal de igual = entre parênteses.

numero q vem antes do 'PM'
![[Pasted image 20250610000812.png]]

# Lookahead Negativo: (?!)

Por exemplo, queremos selecionar números diferentes do valor da hora no texto. Portanto, devemos escrever o lookahead negativo (?!) após nossa expressão para selecionar apenas os valores numéricos que não têm PM depois. Inclua PM após o sinal de exclamação ! entre parênteses.

numero que o 'PM' não vem dps
![[Pasted image 20250610000952.png]]

# Lookbehind Positivo: (?<=)

Por exemplo, queremos selecionar o valor do preço no texto. Portanto, para selecionar apenas os valores numéricos **<u>precedidos</u>** por $, precisamos escrever o lookbehind positivo (?<=) antes de nossa expressão. Adicione \$ após o sinal de igual = entre parênteses.

não entendi bem esse tmb
![[Pasted image 20250610001520.png]]

# Lookbehind Negativo: (?<!)

Por exemplo, queremos selecionar números no texto que não sejam o valor do preço. Portanto, para selecionar apenas valores numéricos que não sejam precedidos por $, precisamos escrever o lookbehind negativo (?<!) antes de nossa expressão. Adicione \$ após o sinal < entre parênteses.

![[Pasted image 20250610001813.png]]


