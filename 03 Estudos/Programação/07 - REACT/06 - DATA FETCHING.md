**Data Fetching** é o processo de buscar dados de fontes externas, como APIs ou bancos de dados, para exibir conteúdo dinâmico em uma aplicação React. Como o React não impõe uma forma específica de fazer isso, você pode escolher entre várias técnicas, como:

1. **Fetch API** (nativa do navegador)
2. **Axios** (biblioteca baseada em promessas)
3. **SWR** (hook do Vercel para simplificar o fetching)

Essas ferramentas permitem buscar dados de APIs e gerenciar estados como **carregamento (loading)**, **dados (data)** e **erros (error)**.

## Como funciona o Data Fetching no React?

No React, o fetching de dados geralmente é tratado como um **efeito colateral** (side effect), pois envolve interações com o mundo externo (como APIs). Por isso, o hook `useEffect` é usado para executar o fetching quando o componente é montado ou quando alguma dependência muda.

Os estados principais que você gerencia ao buscar dados são:
- **loading**: indica se os dados estão sendo carregados.
- **data**: armazena os dados recebidos da API.
- **error**: captura erros que ocorrem durante o fetching.

## Exemplo 1: Usando a Fetch API

A **Fetch API** é uma ferramenta nativa do navegador para fazer requisições HTTP. Aqui está como usá-la em React com `useEffect` e `useState`:

### 1. **Configure os estados**:
```javascript
import { useState, useEffect } from "react";

const FetchPosts = () => {
	const [data, setData] = useState(null); // Armazena os dados
	const [loading, setLoading] = useState(true); // Controla o estado de carregamento
	const [error, setError] = useState(null); // Armazena erros
```

### 2. **Faça a requisição dentro de `useEffect`**:
   Usamos `useEffect` para executar o fetching quando o componente é montado. Para usar a sintaxe `async/await` (mais legível que `.then()`), criamos uma função assíncrona dentro do `useEffect`:

```javascript
useEffect(() => {
	const fetchData = async () => {
		try {
			const res = await fetch("https://jsonplaceholder.typicode.com/posts");
			if (!res.ok) throw new Error("Erro na rede");
			const data = await res.json();
			setData(data);
		} catch (err) {
			setError(err);
		} finally {
			setLoading(false); // Finaliza o carregamento
		}
	};
	fetchData();
	}, []); // Array vazio significa que só executa uma vez
```

### 3. **Renderize os dados**:
   Com base nos estados, você renderiza diferentes conteúdos:
```javascript
if (loading) return <p>Loading...</p>;
if (error) return <p>{error.message}</p>;
return (
	<ul>
		{data.map((post) => (
			 <li key={post.id}>{post.title}</li>
		))}
	</ul>
);
```

**Resumo do fluxo**:
- Enquanto `loading` é `true`, mostra "Loading...".
- Se houver um erro, exibe a mensagem de erro.
- Quando os dados chegam, renderiza a lista de posts.

## Exemplo 2: Usando Axios

**Axios** é uma biblioteca popular que simplifica requisições HTTP e automaticamente converte respostas JSON. Para usá-la:

### 1. **Instale o Axios**:
```bash
npm install axios
```

### 2. **Use Axios no `useEffect`**:
O código é semelhante ao da Fetch API, mas não precisamos chamar `res.json()`:
```javascript
import axios from "axios";
import { useState, useEffect } from "react";

const FetchUsers = () => {
const [data, setData] = useState(null);
const [loading, setLoading] = useState(true);
const [error, setError] = useState(null);

useEffect(() => {
	const fetchData = async () => {
		try {
		   const res = await axios.get("https://jsonplaceholder.typicode.com/users");
		   setData(res.data);
		 } catch (err) {
		   setError(err);
		 } finally {
		   setLoading(false);
		 }
   };
   fetchData();
 }, []);

if (loading) return <p>Loading...</p>;
if (error) return <p>{error.message}</p>;

return (
	<ul>
		{data.map((user) => (
			<li key={user.id}>{user.name}</li>
		 ))}
   </ul>
 );
};
```

**Vantagem do Axios**:
- Simplifica o parsing de JSON.
- Oferece mais funcionalidades, como interceptadores de requisições e respostas.

## Exemplo 3: Usando SWR

**SWR** é um hook do Vercel que simplifica o fetching, oferecendo cache, revalidação automática e gerenciamento de estados embutido. Para usá-lo:

### 1. **Instale o SWR**:
```bash
npm install swr
```

### 2. **Use o hook `useSWR`**:
Você cria uma função `fetcher` e passa o endpoint e o fetcher para o hook:
```javascript
import useSWR from "swr";

const fetcher = (url) => fetch(url).then((res) => res.json());

const FetchTodos = () => {
	const { data, error } = useSWR("https://jsonplaceholder.typicode.com/todos", fetcher);

if (!data) return <h2>Loading...</h2>;
if (error) return <h2>Error: {error.message}</h2>;

 return (
	<>
		<h2>Todos</h2>
		<div>
			{data.map((todo) => (
				<h3 key={todo.id}>{todo.title}</h3>
			))}
		</div>
	</>
 );
};
```

**Vantagens do SWR**:
- Código mais curto, pois gerencia `data` e `error` automaticamente.
- Oferece cache e revalidação automática (útil para dados que mudam frequentemente).
- Não precisa de `useState` para gerenciar estados.

## Exemplo 4: Criando um Hook Personalizado

Se você faz fetching em vários componentes, pode criar um **hook personalizado** para reutilizar a lógica. Aqui está um exemplo com SWR:

### 1. **Crie o hook `useFetch`**:
```javascript
import useSWR from "swr";

const fetcher = (url) => fetch(url).then((res) => res.json());

const useFetch = (url) => {
	const { data, error } = useSWR(url, fetcher);
	return {
		data,
		loading: !data && !error, // Loading é true se não há dados nem erro
		error,
	};
};

export default useFetch;
```

### 2. **Use o hook personalizado**:
```javascript
import useFetch from "./useFetch";

const FetchPosts = () => {
const { data, loading, error } = useFetch("https://jsonplaceholder.typicode.com/posts");

if (loading) return <h2>Loading...</h2>;
if (error) return <h2>{error.message}</h2>;

return (
	<>
		<h2>Posts</h2>
		<ul>
			{data.map((post) => (
				<li key={post.id}>{post.title}</li>
			))}
		</ul>
	</>
);
};
```

**Vantagem do hook personalizado**:
- Reutiliza a lógica de fetching.
- Reduz código repetitivo em vários componentes.

## Comparação das Técnicas

| Técnica       | Vantagens                                                                 | Desvantagens                                              |
|---------------|---------------------------------------------------------------------------|-----------------------------------------------------------|
| **Fetch API** | Nativa, não requer dependências externas                                  | Mais verbosa, exige parsing manual de JSON                |
| **Axios**     | Simplifica parsing de JSON, mais recursos (ex.: interceptadores)           | Requer instalação de biblioteca externa                   |
| **SWR**       | Código curto, cache e revalidação automática, gerenciamento de estados     | Requer instalação e aprendizado da API do SWR             |
| **Hook Personalizado** | Reutilização de lógica, modularidade                              | Exige criar e manter o hook                              |

## Resumo Final

- **O que é?** Data fetching é o processo de buscar dados de APIs ou bancos de dados para renderizar conteúdo dinâmico.
  
- **Como fazer?** Use `useEffect` para gerenciar efeitos colaterais e `useState` para estados de `loading`, `data` e `error`.
  
- **Técnicas**:
  - **Fetch API**: nativa, simples, mas mais verbosa.
  - **Axios**: biblioteca robusta, facilita parsing de JSON.
  - **SWR**: hook moderno com cache e revalidação automática.
  - **Hook personalizado**: ideal para reutilizar lógica de fetching.
    
- **Boas práticas**:
  - Sempre gerencie os estados de `loading` e `error`.
  - Use `async/await` para código mais legível.
  - Considere hooks personalizados para evitar repetição.