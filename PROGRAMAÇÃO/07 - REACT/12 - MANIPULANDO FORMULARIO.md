Formulários são elementos essenciais em interfaces de usuário, permitindo que os usuários interajam com a aplicação e forneçam informações. No React, a manipulação de formulários é um processo intuitivo e eficiente. Este guia detalhado irá te mostrar como manipular formulários passo a passo, utilizando um exemplo prático.

O código abaixo demonstra como criar um formulário simples que coleta o nome do usuário e o exibe na tela em tempo real:

```jsx
import React, { useState } from 'react';

export default function App() {
	
	const [nome, setNome] = useState('');
	
	return (
		<>
			<h1>Olá, {nome}!</h1>
			
			<input
			type="text"
			name="nome"
			value={nome}
			onChange={(e) => setNome(e.target.value)}
			/>
		</>
	)
}
```

**Explicando o código:**

1. **Importando bibliotecas:** Importamos o React para construir a interface do usuário e o `useState` para gerenciar o estado do componente.
2. **Definindo o estado:** Criamos uma variável de estado `nome` que armazena o nome do usuário. O valor inicial da variável é uma string vazia.
3. **Renderizando o formulário:** Usamos o componente `input` para renderizar um campo de texto no formulário.
4. **Atributos do input:**
    - `type`: Define o tipo de campo de texto, neste caso "text".
    - `name`: Define o nome do campo de texto, neste caso "nome".
    - `value`: Define o valor inicial do campo de texto, que é a variável de estado `nome`.
    - `onChange`: Define uma função que será chamada quando o valor do campo de texto for alterado.
5. **Função onChange:** A função `onChange` recebe um evento como parâmetro e atualiza a variável de estado `nome` com o novo valor digitado no campo de texto.

**Detalhes importantes:**

- O `useState` é um hook que permite gerenciar o estado do componente.
- O estado do componente é um objeto que armazena dados que podem mudar ao longo do tempo.
- A função `onChange` é chamada sempre que o valor do campo de texto for alterado.
- A função `setNome` atualiza a variável de estado `nome` com o novo valor digitado.

### UTILIZANDO HANDLES
Os formulários são elementos essenciais em interfaces de usuário, permitindo que os usuários interajam com a aplicação e forneçam informações. No React, a manipulação de formulários é um processo intuitivo e eficiente. O uso de handles torna esse processo ainda mais organizado, reutilizável e facilita a leitura do código.

O código abaixo demonstra como criar um formulário simples que coleta o nome do usuário e o exibe na tela, utilizando um handle para a função `setNome`:

```jsx
import React, { useState } from 'react';

export default function App() {
	
	const [nome, setNome] = useState('');
	
	const handleChange = (e) => {
	setNome(e.target.value);
	};
	
	return (
		<>
			<h1>Olá, {nome}!</h1>
			
			<input
			type="text"
			name="nome"
			value={nome}
			onChange={handleChange}
			/>
		</>
	)
}
```

**Explicando o código:**

1. **Importando bibliotecas:** Importamos o React para construir a interface do usuário e o `useState` para gerenciar o estado do componente.
2. **Definindo o estado:** Criamos uma variável de estado `nome` que armazena o nome do usuário. O valor inicial da variável é uma string vazia.
3. **Criando o handle:** Criamos uma função `handleChange` que recebe um evento como parâmetro e atualiza a variável de estado `nome` com o novo valor digitado no campo de texto.
4. **Renderizando o formulário:** Usamos o componente `input` para renderizar um campo de texto no formulário.
5. **Atributos do input:**
    - `type`: Define o tipo de campo de texto, neste caso "text".
    - `name`: Define o nome do campo de texto, neste caso "nome".
    - `value`: Define o valor inicial do campo de texto, que é a variável de estado `nome`.
    - `onChange`: Define a função `handleChange` como a função a ser chamada quando o valor do campo de texto for alterado.

**O que são handles?**

Em resumo, handles são funções que servem como "atalhos" para outras funções. No contexto da manipulação de formulários em React, um handle é uma função que recebe um evento como parâmetro e geralmente é usado para atualizar o estado de um componente com base no valor digitado em um campo de texto.

**Vantagens de usar handles:**

- **Organização:** O código fica mais organizado e legível, pois as funções de manipulação do estado ficam separadas da renderização do componente.
- **Reutilização:** O handle pode ser reutilizado em outros componentes, facilitando o desenvolvimento e a manutenção do código.
- **Leitura:** O código fica mais fácil de ler e entender, pois as responsabilidades de cada função ficam mais claras.

**Conclusão:**

Utilizar handles para manipular formulários em React é uma boa prática para organizar o código, aumentar a legibilidade, facilitar a reutilização de funcionalidades e melhorar a leitura do código. Essa técnica permite que você crie formulários interativos e robustos com mais facilidade.

### MANIPULANDO UM SELECT COM HANDLE
Seletores (`select`) são elementos essenciais em interfaces de usuário, permitindo que os usuários escolham uma opção entre várias. No React, a manipulação de seletores é um processo intuitivo e eficiente. O uso de handles torna esse processo ainda mais organizado, reutilizável e facilita a leitura do código.

O código abaixo demonstra como criar um seletor que permite escolher um carro entre várias opções, utilizando um handle para a função `setCarro`:

```jsx
import React, { useState } from 'react';

export default function App() {
	
	const [carro, setCarro] = useState('volvo');
	
	const handleChange = (e) => {
		setCarro(e.target.value);
	};
	
	return (
		<>
			<label>Selecione um carro</label>
			
			<select value={carro} onChange={handleChange}>
				<option value="volvo">Volvo</option>
				<option value="saab">Saab</option>
				<option value="mercedes">Mercedes</option>
				<option value="audi">Audi</option>
			</select>
			
			<p>Carro selecionado: {carro}</p>
		</>
	)
	}
```

**Explicando o código:**

1. **Importando bibliotecas:** Importamos o React para construir a interface do usuário e o `useState` para gerenciar o estado do componente.
2. **Definindo o estado:** Criamos uma variável de estado `carro` que armazena a marca do carro selecionado. O valor inicial da variável é "volvo".
3. **Criando o handle:** Criamos uma função `handleChange` que recebe um evento como parâmetro e atualiza a variável de estado `carro` com a nova marca do carro selecionada no seletor.
4. **Renderizando o seletor:** Usamos o componente `select` para renderizar um seletor na tela.
5. **Atributos do select:**
    - `value`: Define a marca do carro selecionado, que é a variável de estado `carro`.
    - `onChange`: Define a função `handleChange` como a função a ser chamada quando a marca do carro selecionado for alterada.
6. **Renderizando o carro selecionado:** Usamos o componente `p` para renderizar a marca do carro selecionado.