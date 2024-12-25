React é uma biblioteca JavaScript popular para construir interfaces de usuário interativas. Uma parte crucial do desenvolvimento React é a manipulação de objetos, que permite armazenar e atualizar dados dinamicamente. Este guia irá te ensinar tudo que você precisa saber sobre manipulação de objetos em React, com foco em um exemplo prático.

### O que são Objetos em React?

Em React, os objetos são usados para armazenar coleções de dados relacionadas. Imagine que você está construindo um formulário de inscrição para um curso. Você precisaria armazenar informações como nome, curso e ano de inscrição. Em vez de criar variáveis separadas para cada informação, você pode usar um objeto para agrupar todas elas:

```jsx
const form = {
  nome: "",
  curso: "",
  ano: "",
};
```

Cada propriedade dentro do objeto representa um campo do formulário, como `nome` ou `curso`.

### Usando `useState` para Gerenciar Estado

O estado em React permite que você rastreie e atualize dados dinamicamente. Para gerenciar o estado de um objeto, você pode usar o hook `useState`. O hook retorna um array com duas posições:

1. **Estado Atual:** O valor atual do objeto.
2. **Função de Atualização:** Uma função para atualizar o estado do objeto.

No nosso exemplo, podemos usar `useState` para criar um estado para o objeto `form`:

```jsx
const [form, setForm] = useState({
  nome: "",
  curso: "",
  ano: "",
});
```

Aqui, `form` armazena o estado atual do objeto, enquanto `setForm` é a função que permite atualizar esse estado.

### Manipulando Valores com `handleChange`

Ao interagir com o formulário, você precisa atualizar os valores do objeto `form`. Para isso, você pode usar uma função `handleChange` que é chamada sempre que um campo do formulário é modificado.

A função `handleChange` recebe um evento como parâmetro, que contém informações sobre a mudança. Você pode usar essas informações para acessar o nome do campo que foi modificado e seu novo valor:

JavaScript

```jsx
const handleChange = (e) => {
	// Acessa o nome do campo
	const nomeCampo = e.target.name;
	
	// Acessa o novo valor do campo
	const novoValor = e.target.value;
	
	// Atualiza o estado do objeto
	setForm({
	...form,
	[nomeCampo]: novoValor,
	});
};
```

O código acima usa o operador spread (`...`) para criar uma cópia do objeto `form`. Em seguida, ele usa a chave dinâmica `[nomeCampo]` para atualizar a propriedade específica que foi modificada com o `novoValor`.

Vamos analisar a linha setForm({ ...form, [e.target.name]: e.target.value });: 

`{ ...form }`: Isso é chamado de spread operator. Ele cria uma cópia do estado atual do form. Isso é necessário porque em React, o estado é imutável, o que significa que você não deve alterar o estado diretamente.

`[e.target.name]: e.target.value`: Isso é chamado de propriedade computada. **e.target.name** retorna o nome do elemento de entrada (que é o mesmo que a chave no objeto de estado form), e **e.target.value** retorna o valor atual do elemento de entrada. Portanto, isso atualiza a propriedade do objeto form que corresponde ao nome do elemento de entrada com o valor atual do elemento de entrada. Então, quando o usuário digita em um campo de entrada, o evento **onChange** é disparado, e a função **handleChange** é chamada. Dentro dessa função, **setForm** é chamado para atualizar o estado form com o valor atual do campo de entrada. 

Isso funciona para todos os campos de entrada porque cada campo de entrada tem um atributo name que corresponde a uma propriedade no objeto form, e você está usando esse atributo name para determinar qual propriedade atualizar.

### Renderizando Valores Atualizados

Finalmente, você precisa renderizar os valores atualizados do objeto `form` na tela. Você pode fazer isso usando chaves dentro de elementos JSX:

```jsx
<p>Nome: {form.nome}</p>
<p>Curso: {form.curso}</p>
<p>Ano: {form.ano}</p>
```

**Exemplo Completo:**

```jsx
import React, { useState } from 'react';

export default function App() {
	
	const [form, setForm] = useState({
		nome: "",
		curso: "",
		ano: "",
	});
	
	const handleChange = (e) => {
		const nomeCampo = e.target.name;
		const novoValor = e.target.value;
		
		setForm({
			...form,
			[nomeCampo]: novoValor,
		});
	};
	
	return (
		<>
			<label>Nome:</label>
			<input 
				type="text" 
				name="nome" 
				value={form.nome} 
				onChange={handleChange} 
			/>
			
			<label>Curso:</label>
			<input 
				type="text" 
				name="curso" 
				value={form.curso} 
				onChange={handleChange}
			/>
			
			<label>Ano:</label>
			<input 
				type="text" 
				name="ano" 
				value={form.ano} 
				onChange={handleChange} 
			/>
			
			<p>Nome: {form.nome}</p>
			<p>Curso: {form.curso}</p>
			<p>Ano: {form.ano}</p>
		</>
	)
}
```