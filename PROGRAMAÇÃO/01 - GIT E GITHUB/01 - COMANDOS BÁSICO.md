---
Documentação: https://git-scm.com/docs; https://github.com/git-guides/
Testar: https://learngitbranching.js.org/?locale=pt_BR
Livro: obsidian://open?vault=LEITURA&file=02%20Estudo%2Fprogit.pdf
---
---

## 01 Verificando se o Git está Instalado
Para garantir que você possa executar os comandos Git no seu terminal.

```bash
git --version

#saída esperada:
#git version 2.47.1.Windows.2  # Sua versão pode ser mais recente
```

Se não estiver instalado:

| **Sistema Operacional** | **Comando/Instrução**                                                |
| ----------------------- | -------------------------------------------------------------------- |
| Windows                 | [Instalador Oficial](https://git-scm.com/download/win)               |
| Linux (Debian/Ubuntu)   | `sudo apt update && sudo apt install git`                            |
| MacOS                   | `brew install git` ou [Instalador](https://git-scm.com/download/mac) |

## 02 Configurando o Usuário e E-mail
Essas informações identificam suas contribuições nos projetos, como uma assinatura digital.

Use o e-mail cadastrado no GitHub/GitLab para vincular commits à sua conta

Configuração Global (Padrão para Todos Projetos)
```bash
git config --global user.name "Seu Nome"
git config --global user.email "example@mail.com"
```

Configuração Local (Específica para um Projeto)
```bash
cd meu-projeto-especial
git config --local user.name "Seu Nome"
git config --local user.email "example@mail.com"
```

Como Verificar:
```bash
git config user.name   # Mostra o nome configurado
git config user.email  # Mostra o e-mail atual
```

## 03 Iniciando um Repositório Local 
Um diretório onde o Git monitora todas as alterações nos arquivos.

Crie uma Pasta para o Projeto:
```bash
mkdir meu-primeiro-projeto
cd meu-primeiro-projeto
```

Inicialize o Repositório com git:
```bash
git init

#Resultado:
#Será criada uma pasta oculta `.git` que armazena todo o histórico e configurações.
```

Crie seu Primeiro Arquivo:
```bash
echo "# Meu Projeto Incrível" > README.md
```

## 04 Trabalhando com Alterações

Fluxo Básico do Git:
- Working Directory (Seus arquivos atuais)
- Stage Area (Preparação para commit)
- Repository (Histórico permanente)

```
Boas Práticas

- Mensagens claras e descritivas
- Use o modo imperativo: "Corrige erro de login" em vez de "Corrigindo erro"
- Limite a 50 caracteres no assunto
```

Verificando o Status
```bash
git status                # Para encontrarmos arquivos que estão ou não em stage
```

Adicionando Arquivos ao Stage
```bash
git add README.md            # Arquivo específico
git add *.js                 # Todos arquivos JavaScript
git add .                    # Tudo que foi modificado
```

Efetuando Commit (Registro Permanente)
```bash
git commit -m "Adiciona documentação inicial"
```

Visualizando Diferenças
```bash
git diff              # Modificações não stageadas
git diff --staged     # Modificações preparadas para commit
```

## 05 Visualizando o Histórico

Listagem Simplificada
```bash
git log --oneline --graph --decorate

# Exemplo de saída:
# 1a2b3c4 (HEAD -> main, origin/main) Adiciona sistema de pagamento
# 5d6e7f8 Implementa carrinho de compras
```

Detalhamento Completo
```bash
git show 1a2b3c4
```

Mostra:
- Autor e data
- Mensagem completa do commit
- Diferenças específicas nos arquivos (diff)

Dica de Filtragem:
```bash
git log --since="2023-01-01" --until="2023-12-31"  # Por data
git log --author="Elian"                           # Por autor
git log --grep="bug"                               # Busca em mensagens
```

## 6 Dicas Extras
Utilizado para ignorar pastas e arquivos e não enviá-los para o repositório remoto do Github.

Exemplos comuns incluem `node_modules`, `build`, `bin`, e outras pastas relacionadas à construção e execução do seu projeto.

Ignorar Arquivos (`.gitignore`)
```bash
# .gitignore
node_modules/  # Pasta completa
*.log          # Todos arquivos .log
.env           # Arquivo específico
```
