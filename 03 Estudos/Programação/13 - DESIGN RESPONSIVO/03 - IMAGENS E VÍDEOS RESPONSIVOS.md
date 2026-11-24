---
Praticar: https://codepen.io/oliveryeahh/pen/XJmbPvq?editors=1100
---
```ad-tip
Utilize <mark style="background: #FFF3A3A6;">max-width=100%</mark> para setar o tamanho das imagens e vídeos pois, utilizando porcentagem, que é uma medida relativa ao pai, o elemento sempre ocupará o tamanho máximo do container em que estiver

```

```css
img, iframe, object, embed, video{
  max-width: 100%;
  height: 100%; /* opcional
}
```

# O problema de imagens em layout fluidos

O problema é o mobile. Eles tem conexões mais lentas e telas menores. É preciso entregar imagens mais leves (kbs) para que não demore muito para essa imagem ser carregada para eles.

# Técnicas para burlar isso

- Riloadr - biblioteca javascript - ultrapassado
- jquery picture - plugin jquery - ultrapassado
- picturefill - polyfill JavaScript - ultrapassado
- adaptative images - solução em servidor - ultrapassado

**Ultrapassado**: Riloadr, jQuery Pictures (HiSRC) e Adaptive Images são considerados obsoletos porque dependem de JavaScript ou configurações específicas de servidor, que são menos eficientes e menos flexíveis que as soluções nativas. Picturefill é parcialmente ultrapassado, mas pode ser usado em casos raros de suporte a navegadores legados.

**Moderno**: Use <picture>, srcset, sizes, object-fit e formatos como WebP/AVIF para máxima eficiência. Combine com loading="lazy" para otimizar o carregamento e ferramentas como Imagemin ou CDNs para reduzir o tamanho dos arquivos.


