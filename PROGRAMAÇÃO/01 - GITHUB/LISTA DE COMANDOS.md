# Tutorial de Fundamentos do Git

Este tutorial fornecerá uma visão abrangente dos comandos essenciais do Git, explicando cada comando e seu uso prático.

## Git Básico - Comandos Fundamentais

1. **`git init`**: Inicializa um novo repositório Git no diretório atual.

2. **`git clone <URL>`**: Clona um repositório remoto em sua máquina local. Substitua `<URL>` pela URL do repositório.

3. **`git config user.name`**: Exibe o nome de usuário configurado no Git.

4. **`git add`**: Adiciona alterações no diretório de trabalho à área de staging.

5. **`git commit -m "<mensagem>"`**: Consolida as alterações adicionadas na área de staging com uma mensagem de commit.

6. **`git status`**: Mostra o status atual do repositório, indicando arquivos modificados, adicionados e não rastreados.

7. **`git log`**: Exibe o histórico de commits, incluindo hash, autor, data e mensagem.

8. **`git diff`**: Mostra as diferenças entre as alterações não consolidadas e o último commit.

## Ramificações no Git - Trabalhando com Branches

1. **`git branch`**: Lista todas as ramificações no repositório.

2. **`git checkout -b <nome-da-ramificacao>`**: Cria e muda para uma nova ramificação com o nome especificado.

3. **`git merge <nome-da-ramificacao>`**: Combina as alterações de uma ramificação específica na atual.

## Repositórios Remotos - Colaboração e Sincronização

1. **`git remote add <nome-remoto> <URL>`**: Adiciona um repositório remoto com um nome específico.

2. **`git fetch`**: Obtém as atualizações do repositório remoto sem aplicá-las.

3. **`git pull <nome-remoto> <nome-ramificacao>`**: Obtém e mescla alterações do repositório remoto na ramificação local.

4. **`git push <nome-remoto> <nome-ramificacao>`**: Envia as alterações locais para o repositório remoto.

## Desfazendo Alterações e Correções

1. **`git revert`**: Cria um commit que desfaz as alterações de um commit anterior.

2. **`git reset`**: Permite redefinir o estado do repositório para um commit específico.

3. **`git clean -n`**: Mostra os arquivos não rastreados que seriam removidos.

4. **`git restore "<nome-do-arquivo>"`**: Desfaz as alterações em um arquivo específico.

## Rebase e Correção do Histórico

1. **`git rebase -i`**: Inicia uma rebase interativa para reescrever o histórico de commits.

2. **`git commit --amend -m "<mensagem>"`**: Altera a mensagem do último commit.

3. **`git reflog`**: Exibe um registro de ações no repositório, útil para recuperar commits perdidos.

## Configurações e Personalização

1. **`git config --global user.name`**: Exibe ou define o nome de usuário global.

2. **`git config --global user.email`**: Exibe ou define o email do usuário global.

3. **`git config --global alias.<atalho> "<comando>"`**: Cria atalhos para comandos frequentes.

4. **`git config --system core.editor`**: Define o editor padrão para mensagens de commit.

5. **`git config --global --edit`**: Abre o arquivo de configuração global em um editor de texto.

Lembre-se de adaptar os exemplos e detalhes conforme necessário para atender às necessidades do seu público. Essas modificações visam tornar o tutorial mais claro e acessível para usuários de diferentes níveis de conhecimento em Git.