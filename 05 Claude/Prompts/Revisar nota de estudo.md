---
tipo: prompt
uso: estudos
modelo: Claude
avaliacao: 
criado: 2026-11-19
tags: [prompt]
---
# Revisar nota de estudo

**Quando usar:** depois de escrever uma nota em `03 Estudos/`, para revisar e gerar questões.

## Prompt
```text
Leia a nota [[{{nota}}]]. Depois:
1. Aponte erros conceituais ou trechos desatualizados.
2. Sugira o que falta para a nota ficar completa.
3. Crie 5 questões no estilo {{banca ou "entrevista técnica"}}, com gabarito comentado.
Não edite a nota; só responda.
```

## Variáveis
- `{{nota}}`: nome da nota
- `{{banca}}`: ex.: CESPE, FGV, ou "entrevista técnica"
