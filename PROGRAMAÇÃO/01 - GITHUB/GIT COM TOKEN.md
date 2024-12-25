# Como Usar Tokens no Git

1. **Crie um Token**
   - Acesse as configurações de segurança do seu provedor de Git (por exemplo, GitHub).
   - Gere um novo token de acesso pessoal. Escolha as permissões apropriadas, como leitura/gravação de repositórios.

2. **Configuração Global**
   - Abra o terminal.
   - Configure o Git para usar o token como credencial global:
     ```shell
     git config --global credential.helper store
     ```
   - Isso armazenará suas credenciais, incluindo o token, em um arquivo local criptografado.

3. **Clone ou Configure um Repositório**
   - Clone um repositório existente ou crie um novo repositório local:
     ```shell
     git clone <URL do Repositório>
     cd <Nome do Repositório>
     ```

4. **Autenticação com Token**
   - Quando você realiza operações que exigem autenticação (como push ou pull), o Git solicitará suas credenciais.
   - Insira seu nome de usuário (geralmente seu email) e utilize o token como senha.

5. **Armazenamento em Cache Opcional**
   - Se desejar evitar inserir o token repetidamente, você pode usar um gerenciador de credenciais para armazenar em cache suas credenciais. Por exemplo, no Windows, você pode usar o "Credential Manager".

6. **Revogar Tokens (Opcional)**
   - Se em algum momento você quiser revogar o acesso do token, vá até as configurações de segurança do seu provedor de Git e desative ou delete o token gerado.

7. **Mantenha Seu Token Seguro**
   - O token é uma forma de autenticação poderosa. Mantenha-o em segurança e não compartilhe com outras pessoas.

8. **Outras Opções de Autenticação**
   - Além de tokens, você também pode usar chaves SSH para autenticação, dependendo do provedor de Git e das suas preferências.

