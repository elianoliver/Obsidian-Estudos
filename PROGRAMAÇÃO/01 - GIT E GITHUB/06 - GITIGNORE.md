## O que é e por que usar?

O `.gitignore` é um arquivo especial que **define quais arquivos/pastas o Git deve ignorar**. É essencial para:

- Evitar envio de arquivos temporários
- Proteger dados sensíveis (senhas, chaves)
- Otimizar o repositório (excluir dependências)
- Manter a organização do projeto

É como uma "lista negra" que diz ao Git: *"Não se preocupe com esses arquivos!"*

# 01 Criando o Arquivo .gitignore

No diretório do projeto:
```bash
type nul > .gitignore  # windows - cria o arquivo
```

Estrutura básica:
```gitignore
arquivo.txt       # Ignora arquivo específico
pasta/            # Ignora toda a pasta
*.log             # Ignora todos com extensão .log
```

# 02: Regras de Filtragem

Padrões essenciais:

| Padrão          | Exemplo        | Resultado                      |
|-----------------|----------------|--------------------------------|
| `*.ext`         | `*.tmp`        | Ignora todos .tmp             |
| `pasta/`        | `node_modules/`| Ignora a pasta inteira        |
| `!` (exceção)   | `!importante.tmp` | Mantém este .tmp específico |
| `**/` (aninhado)| `**/temp/`     | Ignora todas pastas 'temp'    |
# 03: Cenários Comuns

Ignorar arquivos do sistema:
```gitignore
# Sistemas operacionais
.DS_Store        # Mac
Thumbs.db        # Windows
Desktop.ini      # Windows

# Editores
.vscode/
.idea/
```

Ignorar dependências:
```gitignore
# Node.js
node_modules/
npm-debug.log

# Python
__pycache__/
*.pyc

# Java
target/
*.class
```

Dados sensíveis:
```gitignore
.env            # Variáveis de ambiente
config.ini      # Arquivos de configuração
*.key           # Chaves de segurança
```

# 04: Boas Práticas

- **Crie cedo:** Adicione o `.gitignore` no primeiro commit

- **Específico vs Genérico:**  
   ```gitignore
   # Bom
   /local.env      # Ignora apenas na raiz
   
   # Ruim
   *.env           # Pode ignorar acidentalmente outros
   ```

- **Valide com:**
   ```bash
   git status --ignored  # Mostra arquivos ignorados
   ```

- **Use templates prontos:** [github/gitignore](https://github.com/github/gitignore) tem modelos para +500 linguagens

# Passo 5: Casos Especiais

Arquivos já rastreados:
Se você adicionou algo ao .gitignore mas o Git já está rastreando:
```bash
git rm --cached arquivo.txt  # Remove do tracking, mantém local
git commit -m "Para de rastrear arquivo.txt"
```

Ignorar em todos projetos:
Crie um `.gitignore` global:
```bash
git config --global core.excludesfile ~/.gitignore_global
```

# ⚠️ Cuidados Importantes
- O `.gitignore` **não é segurança** - dados sensíveis já commitados precisam ser removidos do histórico
- Sempre **teste as regras** antes de commitar
- Mantenha o arquivo **organizado** com seções comentadas

# Exemplo Completo (Node.js + VSCode):
```gitignore
# Dependências
node_modules/
package-lock.json

# Ambiente
.env
.env.local

# Logs
*.log
logs/

# Editor
.vscode/
!.vscode/settings.json  # Exceto configurações específicas

# Sistema
.DS_Store
Thumbs.db
```

# Como Verificar se está Funcionando?
```bash
# Simula quais arquivos seriam ignorados
git check-ignore -v caminho/do/arquivo

# Exemplo:
git check-ignore -v node_modules/express/package.json
# Saída: .gitignore:1:node_modules/  node_modules/express/package.json
```

# Resumo de Comandos Úteis
```bash
# Cria .gitignore para uma linguagem específica
curl https://raw.githubusercontent.com/github/gitignore/main/Node.gitignore -o .gitignore

# Lista todos arquivos ignorados
git ls-files --others --ignored --exclude-standard
```
