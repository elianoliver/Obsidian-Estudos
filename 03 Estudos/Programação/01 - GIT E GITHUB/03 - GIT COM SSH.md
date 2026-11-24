# Como Usar Chaves SSH no Git

1. **Verifique se você possui uma chave SSH**
   - No terminal, verifique se você já possui uma chave SSH em seu diretório home:
     ```shell
     ls ~/.ssh
     ```
   - Se você vir arquivos como `id_rsa` e `id_rsa.pub`, você já possui uma chave SSH. Pule para a Etapa 3.

2. **Crie uma Chave SSH (caso necessário)**
   - Se você não possui uma chave SSH, crie uma nova:
     ```shell
     ssh-keygen -t rsa -b 4096 -C "seu-email@example.com"
     ```
   - Siga as instruções para escolher um nome para a chave e uma senha opcional.

3. **Copie a Chave Pública para a Área de Transferência**
   - Abra a chave pública em um editor de texto ou no terminal:
     ```shell
     cat ~/.ssh/id_rsa.pub
     ```
   - Copie todo o conteúdo da chave (começando com "ssh-rsa") para a área de transferência.

4. **Adicione a Chave SSH à sua Conta Git**
   - Acesse as configurações de segurança do seu provedor de Git (por exemplo, GitHub).
   - Adicione a chave pública à sua conta Git (geralmente encontrada em "SSH and GPG keys").

5. **Teste a Conexão SSH**
   - No terminal, teste a conexão SSH com o servidor Git (substitua `github.com` pelo host do seu provedor Git, se for diferente):
     ```shell
     ssh -T git@github.com
     ```
   - Se você receber uma mensagem de boas-vindas, a conexão SSH está funcionando.

6. **Clone ou Configure um Repositório**
   - Clone um repositório existente ou crie um novo repositório local:
     ```shell
     git clone git@github.com:seu-usuario/nome-do-repositorio.git
     cd nome-do-repositorio
     ```

7. **Autenticação com Chave SSH**
   - Ao usar comandos Git (push, pull, etc.), o Git usará automaticamente sua chave SSH para autenticação.

8. **Revogar Chaves (Opcional)**
   - Se necessário, você pode remover ou adicionar chaves SSH à sua conta Git a qualquer momento nas configurações de segurança.

9. **Mantenha suas Chaves Seguras**
   - Assim como com tokens, mantenha suas chaves SSH em local seguro e não compartilhe com outras pessoas.

