
Sim, foram (e continuam sendo) desenvolvidas técnicas que visam sanar o problema de apresentar uma imagem que melhor condiz ao device que a pessoa usa ao visitar um site. Mas um passo anterior a isso é saber escolher qual tipo de imagem usar em qual situação.

| **Formato** | **Compressão** | **Transparência** | **Animação**   | **Tamanho do arquivo** | **Compatibilidade**     | **Uso principal**          | **Responsividade**                |
| ----------- | -------------- | ----------------- | -------------- | ---------------------- | ----------------------- | -------------------------- | --------------------------------- |
| **GIF**     | Sem perdas     | Sim (binária)     | Sim            | Grande (animações)     | Universal               | Animações simples          | Limitado, substituído por WebP    |
| **JPEG**    | Com perdas     | Não               | Não            | Médio a pequeno        | Universal               | Fotos                      | `srcset` para várias resoluções   |
| **PNG**     | Sem perdas     | Sim (alfa)        | Não            | Grande                 | Universal               | Gráficos, ícones           | `srcset`, mas tamanho é obstáculo |
| **SVG**     | Vetorial       | Sim               | Sim (CSS/SMIL) | Muito pequeno          | Universal               | Logotipos, ícones          | Escalável, sem `srcset`           |
| **WebP**    | Com/sem perdas | Sim (alfa)        | Sim            | Pequeno                | Quase universal         | Fotos, gráficos, animações | `<picture>`, `srcset`             |
| **AVIF**    | Com/sem perdas | Sim (alfa)        | Não            | Muito pequeno          | Alta, mas não universal | Fotos, gráficos            | `<picture>`, `srcset`             |
Escolha com sabedoria meu jovem gafanhoto