# Vault Obsidian: guia para o Claude

Este é o vault único do Obsidian do Elian. Ele junta estudos, leituras, diário, projetos e prompts.
Escreva sempre em **português do Brasil**, a menos que eu peça outro idioma.

## Quem sou eu

@.claude/contexto/sobre-mim.md

Para currículo, LinkedIn, entrevistas ou requisitos de edital, leia também `05 Claude/Contextos/Currículo.md`.

## Estrutura

| Pasta | O que vai nela |
|---|---|
| `00 Inbox/` | Notas novas e rascunhos ainda sem lugar. É o padrão do Obsidian para notas novas. |
| `01 Diário/` | Notas diárias `AAAA-MM-DD.md` (template `90 Templates/Diário`). **Privada** |
| `02 Projetos/` | Uma pasta por projeto ativo, com uma nota principal `<Projeto>.md` (template `Projeto`). |
| `03 Estudos/Concurso/` | Concurso público: `Conteúdo/` (Direito Constitucional, Português), `Editais/`, `Provas/`, `Legislação/`. |
| `03 Estudos/Programação/` | Notas de programação organizadas por tecnologia (`01 - GIT E GITHUB` … `13 - DESIGN RESPONSIVO`, `Excalidraw/`). |
| `03 Estudos/Livros técnicos/` | Fichamentos de livros técnicos (ex.: Entendendo Algoritmos). |
| `04 Leitura/Anotações/` | Anotações de livros pessoais (ex.: ReZero). |
| `04 Leitura/Biblioteca/` | PDFs e ebooks (`Pessoal/`, `Técnicos/`). **Somente leitura**: não renomear nem mover. |
| `05 Claude/Prompts/` | Prompts reutilizáveis, um por nota (template `Prompt`). |
| `05 Claude/Contextos/` | Contextos que eu colo ou peço para você ler antes de uma tarefa (sobre mim, trabalho, estilo). **Privada** |
| `90 Templates/` | Templates do Obsidian (plugin Templates nativo). |
| `98 Documentos/` | Documentos pessoais (RG, CPF, contratos, exames). **Proibido ler, listar ou citar.** |
| `99 Anexos/` | Imagens e anexos. Os de programação ficam em `99 Anexos/Programação/`. |

## Convenções

- **Links:** use wikilinks só com o nome da nota (`[[Nome da nota]]`), sem caminho. Imagens: `![[arquivo.png]]`.
- **Frontmatter:** notas novas começam com propriedades YAML (`tipo`, `status`, `criado`, `tags`), seguindo os templates em `90 Templates/`.
- **Nomes de arquivo:** mantenha o padrão da pasta. Em `Programação` é `NN - TÍTULO EM MAIÚSCULAS.md`; no diário, `AAAA-MM-DD.md`.
- **Callouts:** o vault usa o plugin Admonition e callouts nativos (`> [!note]`, `> [!tip]`, `> [!warning]`).
- Antes de criar uma nota, procure se já existe uma parecida e prefira editar a existente.
- Ao mover ou renomear notas, atualize os wikilinks que apontam para elas.
- Sem lugar óbvio para uma nota nova? Coloque em `00 Inbox/`.

## Privacidade e Git

- O vault faz backup num repositório **público** no GitHub, pelo plugin obsidian-git.
- `01 Diário/`, `05 Claude/Contextos/`, `98 Documentos/` e todos os PDF/epub/mobi estão no `.gitignore`. **Nunca** tire essas regras nem force a inclusão desses arquivos (`git add -f`).
- Não copie informação pessoal do diário ou dos contextos para notas que vão para o Git.
- Não faça commit nem push sem eu pedir.

## Como me ajudar

- **Estudos:** resumos, flashcards e questões no estilo de banca a partir das notas de `03 Estudos/`.
- **Projetos:** ao começar um projeto, crie `02 Projetos/<Nome>/<Nome>.md` a partir do template e registre ali as decisões e próximos passos.
- **Prompts:** quando um prompt funcionar bem, salve-o em `05 Claude/Prompts/` com o template `Prompt`.
