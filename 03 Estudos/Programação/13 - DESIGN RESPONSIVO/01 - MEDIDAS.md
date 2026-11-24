---
Praticar: https://codepen.io/oliveryeahh/pen/YPyXGjM?editors=1100
---
vamos focar na resolução da tela para basearmos nossa escrita de código. focar em um único dispositivo para montar o site e utilizar os media queries para fazer as adaptações.

- ! não utilizar medidas absolutas no css - droga :FarFaceSadCry:
# TIPOS DE MEDIDAS EM CSS

Embora existam outros tipos de medidas em CSS, vamos basear esta explicação nas nas principais: 

| Tipo        | Medida | Categoria | Explicação                                                                                                                                                                                                                                                                                |
| ----------- | ------ | --------- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Pixels      | px     | Fixo      | É a unidade de medida fixa mais usada nas CSS. Comumente falando, um pixel é um ponto indivisível na tela de exibição de um dispositivo.                                                                                                                                                  |
| Points      | pt     | Fixo      | Pontos são tradicionalmente utilizados para CSSs de impres- são. Um ponto é igual a 1/72 polegadas (1in = 96px). Assim como os pixels, pontos são unidades de tamanho fixo.                                                                                                               |
| Ems         | em     | Relativo  | O “em” é uma unidade escalável. Quando se trata do tamanho da fonte, 1em é igual ao tamanho atual da fonte do elemento-pai. Por exemplo, se o tamanho da fonte do elemento é 12pt, 1em é igual a 12pt.                                                                                    |
| Porcentagem | %      | Relativo  | A unidade porcento é muito parecida com a unidade “em”, mas possui algumas diferenças fundamentais. Em primeiro lugar, o atual tamanho da fonte é igual a 100% (ou seja 12pt = 100%). Durante o uso da unidade porcento, o texto permanece totalmente escalável para dispositivos móveis. |

Portanto, apesar de ser possível usar qualquer um dos tipo de medidas relativas, é meio que consenso entre os desenvolvedores usar <mark style="background: #BBFABBA6;">porcentagem para lidar com tamanhos no layout</mark> (larguras, margens, espaçamentos, etc).

E usar <mark style="background: #BBFABBA6;">ems para lidar com fontes</mark>. em pode até ser usado fora de textos, mas vai ser sempre uma medida relativa ao font-size; já o porcento é relativo ao font-size quando usada em font-size, mas, quando usada com outras medidas, é relativa à largura do elemento-pai.

# CONVERSÃO DE UMA PARA OUTRA

Quando, desde sua concepção, um projeto tem por objetivo contar com design responsivo, é importante que os desenvolvedores envolvidos pensem de “forma relativa”, ou seja, em implementar este layout se valendo de medidas relativas no CSS.

Se, na “antiga maneira de pensar”, houvesse, por exemplo, um título com tamanho de fonte de 24px, então, seria preciso converter essa medida em em.
![[Pasted image 20250714170029.png]]
Então, agora fica simples descobrir qual a equivalência em ems de 24px. Basta aplicarmos a fórmula (existe uma certa convenção de que o tamanho padrão de fontes em browsers desktop é de 16px).

```
alvo/contexto = resultado
24/16 = 1,5
```

Ou seja, ao pegar nosso alvo (o título) de 24px e dividir pelo contexto (no caso, seu elemento-pai, que é body, possui tamanho fonte de 100%, ou, no caso, 16px), temos como resultado 1,5. Como estamos tratando de tamanho relativo de fontes em CSS, o resultado final é 1.5em.

---

Este é o momento para praticar. O link para um exercício com design fixo está no início deste texto.