---
description: Salva um prompt reutilizável em 05 Claude/Prompts
argument-hint: <nome do prompt> (ou deixe vazio para salvar o último prompt da conversa)
---
Salve um prompt reutilizável no vault. Nome ou instrução: $ARGUMENTS

1. Se eu não colar o prompt, use o último pedido meu nesta conversa que funcionou bem.
2. Generalize: troque o que muda a cada uso por `{{variáveis}}`.
3. Crie `05 Claude/Prompts/<Nome>.md` a partir de `90 Templates/Prompt.md` (data de hoje no lugar de `{{date}}`), preenchendo **Quando usar**, **Prompt** e **Variáveis**.
4. Se já existir um prompt parecido em `05 Claude/Prompts/`, mostre-o e pergunte se é para atualizar o existente.
