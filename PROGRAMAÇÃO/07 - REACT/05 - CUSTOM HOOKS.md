Custom hooks são funções reutilizáveis que você cria para compartilhar lógica entre diferentes componentes no React. Eles permitem extrair funcionalidades comuns, como:

- Gerenciamento de estado (ex.: `useState`).
- Efeitos colaterais (ex.: buscar dados, verificar status online/offline).
- Lógica específica (ex.: debouncing, toggling).

Em vez de repetir a mesma lógica em vários componentes, você encapsula essa lógica em um *custom hook*, tornando o código mais limpo, reutilizável e fácil de manter.

**Por que usar custom hooks?**
- Reduz duplicação de código.
- Separa a lógica da renderização, deixando os componentes focados na interface.
- Facilita atualizações, já que a lógica está centralizada em um único lugar.

## Como criar um custom hook?

1. **Nomeação**:
   - Todo *custom hook* deve começar com **"use"** (ex.: `useFetch`, `useToggle`, `useDebounce`). Isso segue a convenção dos hooks do React.
   - O nome deve descrever claramente o que o hook faz.

2. **Estrutura**:
   - Um *custom hook* é uma função JavaScript que pode usar outros hooks internos do React (ex.: `useState`, `useEffect`).
   - Ele geralmente recebe parâmetros e retorna valores (ex.: estado, funções).

3. **Onde salvar**:
   - Crie um arquivo para o hook (ex.: `useDebounce.js`) e, por convenção, salve-o em uma pasta chamada `hooks`.

## Exemplo: Criando o `useDebounce`

Vamos criar um *custom hook* chamado `useDebounce`, que implementa **debouncing**. Debouncing é uma técnica que limita a frequência com que uma função é executada, esperando um tempo após uma ação (ex.: o usuário parar de digitar antes de fazer uma busca).

### Código do `useDebounce`:

```js
// hooks/Debounce.jsx
import { useState, useEffect } from 'react';

function useDebounce(value, delay) {
  const [debouncedValue, setDebouncedValue] = useState(value);

  useEffect(() => {
    // Define um temporizador para atualizar o valor após o atraso
    const handler = setTimeout(() => {
      setDebouncedValue(value);
    }, delay);

    // Função de limpeza: cancela o temporizador se value ou delay mudar
    return () => {
      clearTimeout(handler);
    };
  }, [value, delay]);

  return debouncedValue;
}

export { useDebounce };
```

**Explicação**:
- **Parâmetros**:
  - `value`: O valor que queremos "atrasar" (ex.: texto digitado pelo usuário).
  - `delay`: O tempo (em milissegundos) para esperar antes de atualizar o valor.
- **Estado**:
  - `debouncedValue`: Armazena o valor atrasado, que só é atualizado após o `delay`.
- **useEffect**:
  - Usa `setTimeout` para atualizar `debouncedValue` após o `delay`.
  - A função de limpeza (`clearTimeout`) cancela o temporizador se `value` ou `delay` mudar, evitando atualizações desnecessárias.
- **Retorno**:
  - O hook retorna `debouncedValue`, que os componentes podem usar.

## Como usar o `useDebounce` em um componente?

Aqui está um exemplo de um componente que usa o `useDebounce` para criar uma barra de busca que filtra uma lista de jogadores de futebol:

```javascript
import { useState, useEffect } from 'react';
import { useDebounce } from './hooks/useDebounce';
import footballers from './footballers';

function FootballerSearch() {
  const [query, setQuery] = useState('');
  const debouncedQuery = useDebounce(query, 1000); // Atraso de 1 segundo

  useEffect(() => {
    if (debouncedQuery) {
      const results = footballers.filter((footballer) =>
        footballer.toLowerCase().includes(debouncedQuery.toLowerCase())
      );
      console.log('Resultados da busca:', results);
    } else {
      console.log('Resultados da busca: []');
    }
  }, [debouncedQuery]);

  return (
    <div style={{ textAlign: 'center' }}>
      <h1>Footballer Search App</h1>
      <input
        style={{ padding: '0.5rem', width: '30%' }}
        type="text"
        value={query}
        onChange={(e) => setQuery(e.target.value)}
        placeholder="Pesquise um jogador..."
      />
    </div>
  );
}

export default FootballerSearch;
```

**Explicação**:
- **Estado `query`**:
  - Armazena o texto que o usuário digita na barra de busca.
- **Hook `useDebounce`**:
  - `debouncedQuery` recebe o valor de `query` com um atraso de 1 segundo (1000ms).
- **useEffect**:
  - Filtra a lista de jogadores (`footballers`) com base em `debouncedQuery` e exibe os resultados no console.
  - Só executa a busca quando `debouncedQuery` muda, evitando chamadas desnecessárias a cada tecla digitada.
- **Interface**:
  - Um campo de entrada simples onde o usuário digita o nome do jogador.

## Resumo das principais ideias:

1. **Custom hooks** são funções reutilizáveis que encapsulam lógica compartilhada entre componentes.
2. Devem começar com **"use"** e ser salvos em arquivos na pasta `hooks`.
3. Podem usar hooks internos do React (ex.: `useState`, `useEffect`) e recebem parâmetros para personalizar seu comportamento.
4. **Benefícios**:
   - Reduzem duplicação de código.
   - Separam lógica da interface, tornando os componentes mais simples.
   - Facilitam manutenção e atualizações.
5. Exemplo prático: O `useDebounce` atrasa a execução de uma ação (ex.: busca) até que o usuário pare de interagir por um tempo.

## Dica final para iniciantes:

- Comece criando *custom hooks* para lógicas que você repete em vários componentes (ex.: busca de dados, validação de formulários).
- Teste o hook em um componente simples para garantir que ele funciona como esperado.
- Use ferramentas como o *ESLint* com o plugin `react-hooks` para evitar erros comuns (ex.: dependências faltando no `useEffect`).