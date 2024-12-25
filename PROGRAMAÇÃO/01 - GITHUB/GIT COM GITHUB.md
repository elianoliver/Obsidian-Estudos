# 00 Sumário
- [[#01 Verificando se o Git está instalado]]
- [[#02 Configurando o usuário e o e-mail]]
- [[#03 Iniciando um Repositório Local]]
- [[#04 Iniciando um repositório Remoto]]

---
# 01 Verificando se o Git está instalado
Para verificar se o Git está instalado no seu computador, abra um terminal e execute o comando:
```shell
git --version
```

Se o Git estiver instalado, você verá uma saída semelhante à esta:
```shell
git version 2.33.1
```

Caso essa mensagem não apareça, significa que o Git não está instalado. Nesse caso, acesse o [site oficial do Git](https://git-scm.com/download) e siga as instruções para instalação conforme seu sistema operacional.

---
# 02 Configurando o usuário e o e-mail
O Git precisa saber seu nome de usuário e endereço de e-mail para rastrear suas alterações e enviar solicitações de pull para o GitHub. Para configurar essas informações, execute o comando:
```shell
git config --global user.name "Elian Oliveira"
git config --global user.email "elianoliveira234@gmail.com"
```
ou
```shell
git config --local user.name "Your Name"
git config --local user.email "you@example.com"
``` 
Para ver o e-mail e usuário utilizados no git sendo usados no momento, utilize o seguinte comando:
```shell
git config user.name
git config user.email
```

---
# 03 Iniciando um Repositório Local
### 1. Criando um Diretório para o Repositório

Primeiro, precisamos criar uma pasta onde nosso repositório será armazenado. Para isso, abra o terminal e digite os comandos abaixo:
```shell
mkdir meu-projeto cd meu-projeto
```
- **`mkdir meu-projeto`**: Cria uma nova pasta chamada `meu-projeto`.
- **`cd meu-projeto`**: Entra na pasta que acabamos de criar.

### 2. Inicializando o Repositório Git
Dentro da pasta do projeto, inicialize um novo repositório Git com o comando:
```shell
git init
```
- **`git init`**: Este comando cria um subdiretório oculto na pasta recém criada chamado `.git`, que contém todos os arquivos necessários para o controle de versão. Isso significa que agora, qualquer alteração feita dentro dessa pasta pode ser gerenciada pelo Git.

### 3. Criando um Arquivo de Exemplo
Agora que o repositório está inicializado, vamos criar um arquivo para começarmos a registrar nossas alterações.

Crie um arquivo chamado `README.md` e adicione o seguinte conteúdo:
```shell
# Meu projeto 
Este é um projeto de exemplo para aprender a usar o Git com o GitHub.
```    
Salve o arquivo. Esse arquivo serve como uma documentação inicial do projeto.

### 4. Adicionando Alterações ao Repositório
Para que o Git comece a acompanhar as alterações no arquivo que criamos, precisamos adicioná-lo ao "estágio" (stage), ou seja, à lista de arquivos que serão incluídos no próximo commit.

- Para adicionar apenas o `README.md`:    
```shell
git add README.md
```
   
- Para adicionar todos os arquivos na pasta do projeto:
```shell
git add .
```

- **`git add README.md`**: Adiciona o arquivo `README.md` ao estágio.
- **`git add .`**: Adiciona todos os arquivos e alterações na pasta atual ao estágio.

### 5. Commitando as Alterações
Após adicionar os arquivos ao stage, vamos criar um commit, que é uma espécie de "fotografia" das alterações no repositório naquele momento. Execute o comando:

```shell
git commit -m "Adicionando o README"
```

- **`git commit -m "Adicionando o README"`**: Cria um novo commit com uma mensagem descritiva (entre aspas), explicando o que foi alterado. Nesse caso, a mensagem indica que estamos adicionando o arquivo `README`.

---
# 04 Iniciando um Repositório Remoto

### 1. Criando um Novo Repositório no GitHub
Primeiro, precisamos criar um repositório no GitHub, onde nosso código será hospedado. Siga os passos abaixo:

1. Acesse o [GitHub](https://github.com) e faça login na sua conta.

2. No canto superior direito da página, clique no ícone de "+" e selecione "New repository" (Novo repositório) no menu suspenso.

3. Você será direcionado para uma página onde deve preencher algumas informações:
   - **Repository name** (Nome do repositório): Escolha um nome único e descritivo para o seu repositório. Esse será o nome que aparecerá na URL do seu projeto.
   - **Description** (Descrição - opcional): Escreva uma breve descrição do que o seu projeto faz ou o que ele representa.
   - **Visibility** (Visibilidade): Escolha se o repositório será "Public" (Público) ou "Private" (Privado). Um repositório público pode ser visto por qualquer pessoa, enquanto um repositório privado é visível apenas para você e para quem você autorizar.
   - **Initialize this repository with**: Você pode optar por adicionar um arquivo README, um arquivo `.gitignore` (para excluir arquivos específicos do controle de versão) e uma licença para o projeto. Isso é opcional, mas pode ajudar na organização inicial.

4. Depois de preencher todas as informações, clique no botão verde "Create repository" (Criar repositório).

```ad-hint
Inicialize o repoitório remoto sem README caso queira fazer o push do seu repositório local. 
```

Agora você criou um repositório remoto no GitHub, mas ele ainda está vazio.

### 2. Enviando o Código Local para o Repositório Remoto
Agora que temos um repositório remoto no GitHub, vamos enviar o código que está no nosso computador (repositório local) para lá.

#### 2.1 Navegar até o Diretório do Projeto
Abra o terminal e navegue até a pasta do seu projeto local usando o comando `cd`:
```shell
cd /caminho/para/seu/projeto
```
Substitua `/caminho/para/seu/projeto` pelo caminho da pasta onde seu projeto está armazenado no seu computador.

#### 2.2 Inicializar um Repositório Git Local
Caso ainda não tenha feito isso, inicialize o repositório local com o comando:
```shell
git init
```
Isso vai criar uma estrutura básica de repositório no seu projeto local.

#### 2.3 Adicionar Arquivos ao Controle de Versão
Adicione os arquivos do projeto ao controle de versão do Git. Para isso, você pode adicionar arquivos específicos ou todos os arquivos da pasta:

- Para adicionar apenas o arquivo `README.md`:
```shell
git add README.md
```
- Para adicionar todos os arquivos do diretório:
```shell
git add .
```

#### 2.4 Criar o Primeiro Commit
Um commit é como tirar uma "foto" das alterações que você fez até o momento. Para criar um commit, execute o comando:
```shell
git commit -m "Primeiro commit"
```
A mensagem `"Primeiro commit"` descreve as mudanças feitas. É importante ser claro e específico nas mensagens de commit para facilitar o histórico do projeto.

#### 2.5 Definir a Branch Principal
A branch principal é onde o histórico principal do seu projeto será mantido. Defina a branch principal como `main` (ou outro nome de sua preferência) com o comando:
```shell
git branch -M main
```

#### 2.6 Conectar ao Repositório Remoto no GitHub
Agora, precisamos informar ao Git que o nosso repositório local deve se conectar ao repositório remoto que criamos no GitHub. Faça isso com o comando:
```shell
git remote add origin https://github.com/seu-usuario/seu-repositorio.git
```
Substitua `https://github.com/seu-usuario/seu-repositorio.git` pela URL do repositório que você acabou de criar no GitHub.

#### 2.7 Enviar o Código para o Repositório Remoto
Finalmente, vamos enviar (fazer o *push*) nosso código para o GitHub com o comando:
```shell
git push -u origin main
```
Isso enviará todo o histórico do repositório local para o repositório remoto na branch `main`. Agora, seu código estará disponível no GitHub.

---

Parabéns! Você criou e enviou seu projeto para um repositório remoto no GitHub. A partir de agora, você pode compartilhar o link do seu repositório com outras pessoas e colaborar com desenvolvedores de todo o mundo.