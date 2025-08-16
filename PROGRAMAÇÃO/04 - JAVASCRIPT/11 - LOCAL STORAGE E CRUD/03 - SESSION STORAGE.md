**sessionStorage** é uma parte da **Web Storage API**, assim como o **localStorage**. Ele permite armazenar dados no navegador no formato de pares **chave-valor**, mas com uma diferença importante: os dados no **sessionStorage** só existem enquanto a **aba ou janela do navegador** está aberta. Quando o usuário fecha a aba ou janela, todos os dados do **sessionStorage** são automaticamente apagados.

Isso o torna ideal para armazenar informações temporárias que só precisam durar durante uma **sessão** (ou seja, enquanto o usuário está interagindo com a página na mesma aba).

## Para que serve o sessionStorage?

O **sessionStorage** é usado para guardar dados que não precisam persistir após o usuário fechar a aba do navegador. Exemplos de uso incluem:

- **Formulários de várias etapas**: Armazenar dados inseridos em um formulário enquanto o usuário navega entre páginas, como em um processo de checkout.
  
- **Seleções temporárias**: Guardar preferências ou escolhas que só são relevantes durante a sessão atual, como a seleção de um item em um carrinho de compras.
  
- **Estado de aplicativos de página única (SPAs)**: Manter informações temporárias que não precisam ser salvas após o fechamento da aba.

## Diferença entre sessionStorage e localStorage

- **sessionStorage**:
  - Dados são apagados quando a aba ou janela do navegador é fechada.
  - Ideal para dados temporários.
    
- **localStorage**:
  - Dados persistem até serem explicitamente removidos.
  - Ideal para configurações ou informações que precisam ser mantidas entre sessões.

Os **métodos** usados no **sessionStorage** são **idênticos** aos do **localStorage**, mas o comportamento dos dados é diferente devido à sua natureza temporária.

## Métodos Comuns do sessionStorage

Os métodos do **sessionStorage** são os mesmos do **localStorage** e permitem gerenciar os dados de forma simples:

### 1. **`setItem(chave, valor)`**
Armazena um par chave-valor no **sessionStorage**.
Exemplo: Salvar o número de itens no carrinho.

### 2. **`getItem(chave)`**
Recupera o valor associado a uma chave.
Exemplo: Obter o número de itens salvos para exibi-lo.

### 3. **`removeItem(chave)`**
Remove um par chave-valor específico.
Exemplo: Deletar os dados do carrinho.

### 4. **`clear()`**
Remove **todos** os dados armazenados no **sessionStorage**.
Exemplo: Limpar todas as informações temporárias da sessão.

## Exemplo Prático em JavaScript

Aqui está um exemplo que mostra como usar o **sessionStorage** para gerenciar o nome de um usuário durante uma sessão:

```javascript
// Armazenar o nome do usuário atual
sessionStorage.setItem('currentUser', 'JohnDoe');

// Recuperar o nome do usuário
const user = sessionStorage.getItem('currentUser');
console.log(user); // 'JohnDoe'

// Remover o nome do usuário
sessionStorage.removeItem('currentUser');

// Limpar todos os dados do sessionStorage
sessionStorage.clear();
```

**Explicação do Código**:
- **Armazenar**: `setItem('currentUser', 'JohnDoe')` salva o nome do usuário como "JohnDoe".
- **Recuperar**: `getItem('currentUser')` obtém o valor associado à chave "currentUser" e exibe "JohnDoe".
- **Remover**: `removeItem('currentUser')` deleta a chave "currentUser" do **sessionStorage**.
- **Limpar tudo**: `clear()` remove todos os dados salvos no **sessionStorage**.
- **Importante**: Se a aba for fechada, todos esses dados serão automaticamente apagados.

## Resumo Visual

| Método             | Função                                    | Exemplo de Uso                              |
|--------------------|-------------------------------------------|---------------------------------------------|
| `setItem(chave, valor)` | Armazena um par chave-valor             | `sessionStorage.setItem('cart', '3 items')`  |
| `getItem(chave)`       | Recupera o valor de uma chave           | `sessionStorage.getItem('cart')`            |
| `removeItem(chave)`    | Remove um par chave-valor específico     | `sessionStorage.removeItem('cart')`         |
| `clear()`              | Remove todos os dados do sessionStorage  | `sessionStorage.clear()`                    |

## Por que o sessionStorage é Importante?

O **sessionStorage** é útil para gerenciar dados temporários que não precisam ser mantidos após o fechamento da aba. Ele é perfeito para cenários onde você quer garantir que as informações sejam descartadas automaticamente, como em formulários de várias etapas ou estados temporários de uma aplicação. Além disso, como o **sessionStorage** é específico para cada aba, ele evita conflitos entre diferentes abas abertas no mesmo site.

> **Nota de segurança**: Assim como o **localStorage**, o **sessionStorage** não é seguro para armazenar informações sensíveis, como senhas, pois os dados são armazenados em texto puro e podem ser acessados por scripts maliciosos.

## Conclusão

O **sessionStorage** é uma ferramenta da **Web Storage API** que permite armazenar dados temporários no navegador, usando pares chave-valor, mas apenas enquanto a aba ou janela está aberta. Seus métodos (`setItem`, `getItem`, `removeItem` e `clear`) são idênticos aos do **localStorage**, mas sua natureza temporária o torna ideal para dados que não precisam persistir entre sessões. Ele é amplamente usado para melhorar a experiência do usuário em formulários, carrinhos de compras ou estados temporários de aplicativos web.