---
Praticar: https://codepen.io/oliveryeahh/pen/EaVjOoP?editors=1100
---
Os media queries no css são utilizados para adaptar o layout e o design de um site a diferentes dispositivos, resoluções e contextos. 

Com ele é possível especificar uma regra no css para, quando detectado que se esta acessando o site em um determinado dispositivo ou resolução, aplicar configurações específicas para ele.

```css
@media all and (min-width: 600px) {
  img { max-width: 50%; }
}
```

No contexto de media queries no CSS, os media types são categorias que definem o tipo de dispositivo ou mídia para o qual as regras de estilo serão aplicadas. Os mais comuns são:

| **Media Type**                              | **Descrição**                                                                                       | **Uso Principal**                                                                              | **Status**                               |
| ------------------------------------------- | --------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------- |
| **all**                                     | Aplica-se a todos os dispositivos e tipos de mídia. Padrão quando nenhum media type é especificado. | Estilizar layouts responsivos para todos os dispositivos, incluindo ajustes em imagens.        | Ativo, amplamente usado.                 |
| **screen**                                  | Aplica-se a dispositivos com tela (computadores, smartphones, tablets, TVs).                        | Ajustar imagens responsivas com `srcset`, `<picture>` ou CSS para diferentes tamanhos de tela. | Ativo, o mais comum para responsividade. |
| **print**                                   | Aplica-se a documentos em modo de impressão.                                                        | Otimizar ou ocultar imagens para impressão, economizando tinta ou simplificando layouts.       | Ativo, usado para impressão.             |
| **speech**                                  | Aplica-se a dispositivos de saída de voz, como leitores de tela.                                    | Fornecer conteúdo otimizado para acessibilidade, mas raramente usado para imagens.             | Ativo, mas raro.                         |
| <font color="#ff0000">**tty**               | Para dispositivos d</font>e texto com largura fixa, como terminais.                                 | Estilizar conteúdo para terminais antigos.                                                     | Obsoleto, não usado.                     |
| <font color="#ff0000">**tv**</font>         | Para dispositivos de televisão.                                                                     | Estilizar conteúdo para TVs.                                                                   | Obsoleto, substituído por `screen`.      |
| <font color="#ff0000">**projection**</font> | Para projetores.                                                                                    | Estilizar conteúdo para projeções.                                                             | Obsoleto.                                |
| <font color="#ff0000">**handheld**</font>   | Para dispositivos portáteis (ex.: celulares antigos).                                               | Estilizar para dispositivos móveis legados.                                                    | Obsoleto, substituído por `screen`.      |
| <font color="#ff0000">**braille**</font>    | Para dispositivos táteis de Braille.                                                                | Acessibilidade para dispositivos Braille.                                                      | Raro, pouco usado.                       |
| <font color="#ff0000">**embossed**</font>   | Para impressoras de Braille.                                                                        | Impressão em Braille.                                                                          | Raro, pouco usado.                       |
| <font color="#ff0000">**aural**</font>      | Antiga versão de `speech` para sintetizadores de voz.                                               | Acessibilidade para saída de voz.                                                              | Obsoleto, substituído por `speech`.      |
