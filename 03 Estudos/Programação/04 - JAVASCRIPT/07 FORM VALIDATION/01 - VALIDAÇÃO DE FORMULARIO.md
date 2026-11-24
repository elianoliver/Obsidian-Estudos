Validar formulários significa garantir que os dados inseridos pelos usuários atendam a certas regras antes de serem enviados. Embora o HTML ofereça validações básicas (como o atributo `required` ou `type="email"`), o JavaScript permite criar validações mais complexas e personalizadas, incluindo mensagens de erro específicas.

## Por que usar JavaScript para validação?

- **Mais controle**: Você pode personalizar mensagens de erro para orientar melhor o usuário.
  
- **Flexibilidade**: Permite validações mais específicas que o HTML sozinho não consegue, como verificar se um e-mail pertence a um domínio específico.
  
- **Interatividade**: Exibe mensagens de erro em tempo real, à medida que o usuário digita.

## Ferramentas principais: Constraint Validation API

O HTML oferece a **Constraint Validation API**, uma interface que elementos como `<input>` e `<textarea>` disponibilizam para verificar se os valores inseridos atendem às regras de validação definidas (como `required`, `pattern`, ou `minlength`). Com JavaScript, você pode usar métodos dessa API para criar validações avançadas.

## Exemplo prático: Validando um formulário

Imagine um formulário onde funcionários de uma empresa enviam feedback, com um campo de e-mail que só aceita endereços corporativos (terminando em `@sampleCompany.com`) e um campo de texto para feedback.

```html
<form>
  <label>Enter your email: </label>
  <input required placeholder="username@sampleCompany.com" type="email" pattern=".+@sampleCompany\.com" />

  <label>Enter your feedback: </label>
  <textarea required placeholder="Your feedback here..."></textarea>

  <button type="submit">Submit Feedback</button>
</form>
```

- **Atributos usados**:
  - `required`: Garante que o campo não seja deixado em branco.
  - `type="email"`: Verifica se o valor é um e-mail válido (contém `@`).
  - `pattern=".+@sampleCompany\.com"`: Exige que o e-mail termine em `@sampleCompany.com`.

Se o usuário inserir um e-mail inválido, como `exemplo@gmail.com`, o HTML exibirá uma mensagem padrão: "Please match the requested format." Mas essa mensagem é genérica. Vamos usar JavaScript para torná-la mais clara.

## Métodos da Constraint Validation API

Aqui estão os principais métodos e propriedades usados para validação com JavaScript:

### 1. checkValidity():
   - Verifica se o valor de um campo atende às regras de validação do HTML.
   - Retorna `true` se o valor for válido e `false` se for inválido.
   - Exemplo:
```javascript
const input = document.querySelector("input");

input.addEventListener("input", (e) => {
	console.log(e.target.checkValidity()); // true ou false
});
```

### 2. reportValidity():
   - Exibe a mensagem de erro padrão do navegador quando o valor é inválido.
   - Útil para mostrar erros imediatamente, sem esperar o envio do formulário.
   - Exemplo:
```javascript
const input = document.querySelector("input");

input.addEventListener("input", (e) => {
	if (!e.target.checkValidity()) {
		e.target.reportValidity(); // Mostra a mensagem padrão do navegador
	}
});
```

### 3. setCustomValidity():
   - Permite definir uma mensagem de erro personalizada.
   - Se a validação falhar, a mensagem customizada será exibida.
   - Exemplo:
```javascript
const input = document.querySelector("input");

input.addEventListener("input", (e) => {

	if (!e.target.checkValidity()) {
		 e.target.setCustomValidity("Você deve usar um e-mail corporativo que termine em @sampleCompany.com");
	} else {
		 e.target.setCustomValidity(""); // Limpa a mensagem se válido
	}
});
```

### 4. validity:
   - Propriedade que retorna um objeto `ValidityState` com informações detalhadas sobre o estado de validação.
     
   - Contém propriedades booleanas, como:
     - `valueMissing`: Verdadeiro se um campo `required` está vazio.
     - `patternMismatch`: Verdadeiro se o valor não corresponde ao padrão definido pelo atributo `pattern`.
     - `typeMismatch`: Verdadeiro se o valor não corresponde ao tipo (ex.: e-mail inválido em `type="email"`).
       
   - Exemplo:
```javascript
const input = document.querySelector("input");

input.addEventListener("input", (e) => {
	console.log(e.target.validity);
});
```
 Saída no console para um e-mail inválido:
```javascript
ValidityState {
	badInput: false,
	customError: false,
	patternMismatch: true, // Não corresponde ao padrão
	typeMismatch: true,    // Não é um e-mail válido
	valueMissing: false,
	valid: false
 }
```

## Passo a passo para validar um formulário

1. **Configure o HTML com validações básicas**:
   - Use atributos como `required`, `type`, e `pattern` para definir regras.
     
2. **Selecione o elemento com JavaScript**:
   - Use `document.querySelector` para acessar o `<input>` ou `<textarea>`.
     
3. **Adicione um evento de escuta**:
   - Use `addEventListener("input")` para verificar em tempo real enquanto o usuário digita.
     
4. **Use a Constraint Validation API**:
   - Verifique a validade com `checkValidity()`.
   - Mostre mensagens de erro com `reportValidity()` ou personalize com `setCustomValidity()`.
     
5. **Analise o estado de validade (opcional)**:
   - Use a propriedade `validity` para entender por que a validação falhou.

## Exemplo completo com validação personalizada
```javascript
const input = document.querySelector("input");

input.addEventListener("input", (e) => {
	if (!e.target.checkValidity()) {
	    e.target.setCustomValidity("Você deve usar um e-mail corporativo que termine em @sampleCompany.com");
	} else {
		e.target.setCustomValidity(""); // Limpa a mensagem se válido
	}
});
```

## Dicas finais

- **Teste diferentes cenários**: Experimente deixar o campo vazio, inserir um e-mail inválido ou um e-mail correto para ver como o formulário responde.
  
- **Explore o objeto ValidityState**: Use `console.log(input.validity)` para entender as diferentes propriedades, como `valueMissing` ou `patternMismatch`.
  
- **Melhore a experiência do usuário**: Combine mensagens personalizadas com estilos CSS para destacar campos inválidos.

