O `useOptimistic` é um hook introduzido em versões recentes do React para implementar **atualizações otimistas** na UI. Atualizações otimistas significam atualizar a interface imediatamente com o resultado esperado de uma ação assíncrona (como uma requisição ao servidor), antes mesmo de a ação ser concluída. Isso melhora a experiência do usuário, tornando a UI mais fluida e responsiva.

**Quando usar?**
- Principalmente em operações assíncronas, como envio de formulários ou requisições a APIs.
- Quando você quer mostrar feedback instantâneo ao usuário, mesmo antes de receber a resposta do servidor.

**Diferença de um estado de loading**:
- Um estado de *loading* mostra um indicador (ex.: "Carregando...") enquanto a ação está em andamento.
- O `useOptimistic` atualiza a UI imediatamente com o resultado esperado, sem esperar a conclusão da ação, e pode exibir indicadores como "Adicionando..." enquanto a operação real ocorre.

## Sintaxe do `useOptimistic`

A sintaxe básica é:

```javascript
const [optimisticState, addOptimistic] = useOptimistic(actualState, updateFunction);
```

- **`optimisticState`**: O estado temporário que reflete a atualização otimista na UI.
- **`addOptimistic`**: Função que aplica a atualização otimista antes que o estado real seja atualizado.
- **`actualState`**: O estado real, que será atualizado com o resultado final da ação (ex.: resposta do servidor).
- **`updateFunction`**: Função que define como o `optimisticState` deve ser atualizado com base no estado atual e na nova entrada.

## Como funciona?

O `useOptimistic` permite que você mostre uma mudança na UI imediatamente, assumindo que a operação assíncrona será bem-sucedida. Se a operação falhar, você pode tratar o erro. Se for bem-sucedida, o estado real substitui o estado otimista.

**Exemplo prático**: Adicionar uma tarefa a uma lista de tarefas.

Imagine um formulário onde o usuário adiciona uma tarefa, e a tarefa é enviada a um servidor (com um atraso simulado de 1 segundo). Queremos que a tarefa apareça na lista imediatamente, com um indicador de "Adicionando...", antes que o servidor confirme.

### Passo 1: Configurar a ação assíncrona
Aqui está uma função que simula o envio de uma tarefa ao servidor:

```javascript
export async function saveTask(task) {
	await new Promise((res) => setTimeout(res, 1000)); // Simula atraso de 1s
	return task;
}
```

### Passo 2: Usar o `useOptimistic` no componente
No componente `TaskList`, usamos o `useOptimistic` para gerenciar a lista de tarefas de forma otimista:

```javascript
"use client";
import { useOptimistic, startTransition } from "react";

export default function TaskList({ tasks, addTask }) {
	const [optimisticTasks, addOptimisticTask] = useOptimistic(
		tasks, // Estado real
		(state, newTask) => [...state, { text: newTask, pending: true }] // Atualiza otimistamente
	);

	async function handleSubmit(e) {
	    e.preventDefault();
	    const formData = new FormData(e.target);
	    const task = formData.get("task");

		startTransition(() => {
			addOptimisticTask(task); // Adiciona a tarefa otimistamente
		});
		
		await addTask(formData); // Envia ao servidor
		e.target.reset(); // Limpa o formulário
	}

	return (
		<div className="max-w-md mx-auto p-4">
			<h3 className="text-xl font-medium mb-3">Tasks</h3>
			<ul className="space-y-2 mb-4">
				{optimisticTasks.map((task, index) => (
					<li key={index} className="p-2 border-b">
					{task.text}
					{task.pending && <small className="ml-2 text-gray-500">Adding Task...</small>}
					</li>
				))}
			</ul>
			
			<form onSubmit={handleSubmit} className="flex gap-2">
				<input type="text" name="task" placeholder="Type in a task..." className="flex-1 p-2 border" />
				<button type="submit" className="bg-gray-200 px-3 py-2 cursor-pointer">Submit</button>
			</form>
		</div>
	);
}
```

**O que está acontecendo?**
- O `useOptimistic` cria um estado temporário (`optimisticTasks`) baseado no estado real (`tasks`).

- Quando o usuário envia o formulário, `addOptimisticTask` adiciona a nova tarefa à lista com `pending: true`, mostrando "Adding Task..." na UI.

- A função `addTask` (passada como prop) envia a tarefa ao servidor.

- Usamos `startTransition` para garantir que a atualização otimista seja tratada como uma transição de baixa prioridade, mantendo a UI fluida.

### Passo 3: Gerenciar o estado real
No componente pai `Tasks`, gerenciamos o estado real das tarefas e chamamos a ação `saveTask`:

```javascript
"use client";
import { useState } from "react";
import TaskList from "./TaskList";
import { saveTask } from "./actions";

export default function Tasks() {
	const [tasks, setTasks] = useState([]);

	async function addTask(formData) {
		const newTaskText = formData.get("task");
	    const tempTask = { id: Date.now(), text: newTaskText, pending: true };

	    // Adiciona tarefa temporária
	    setTasks((prev) => [...prev, tempTask]);

	    // Simula atraso de 3s antes de confirmar
	    setTimeout(async () => {
	      const savedTask = await saveTask(newTaskText);
	      setTasks((prev) =>
			prev.map((task) =>
			  task.id === tempTask.id ? { ...task, text: savedTask, pending: false } : task
	        )
	      );
	    }, 3000);
	}

  return <TaskList tasks={tasks} addTask={addTask} />;
}
```

**O que está acontecendo?**
- Adicionamos a tarefa temporária com `pending: true` ao estado real.
- Após um atraso simulado de 3 segundos, a tarefa é confirmada pelo servidor (`saveTask`), e atualizamos o estado real, removendo o `pending: true`.

## Por que usar o `useOptimistic`?

- **Feedback instantâneo**: A tarefa aparece na lista imediatamente, mesmo antes da resposta do servidor.
- **Melhor experiência do usuário**: A UI parece mais rápida e responsiva, pois não fica esperando a conclusão da operação.
- **Gerenciamento de erros**: Se o servidor falhar, você pode reverter a atualização otimista ou mostrar um erro.

## Resolvendo problemas comuns

1. **"Adding Task..." desaparece muito rápido**:
   - Isso acontece porque a ação assíncrona é rápida (ex.: 1 segundo). Para tornar o estado "pending" visível por mais tempo, usamos `setTimeout` no `addTask` para simular um atraso maior (ex.: 3 segundos).

2. **Erro ao adicionar a tarefa**:
   - Envolver `addOptimisticTask` em `startTransition` garante que a atualização otimista seja tratada de forma suave, sem bloquear a UI.

## Resumo Final

- **O que é?** O `useOptimistic` é um hook do React para atualizações otimistas, que atualiza a UI imediatamente com o resultado esperado de uma ação assíncrona.

- **Como funciona?** 
  - Usa um estado temporário (`optimisticState`) que reflete mudanças antes da confirmação do servidor.
  - A função `addOptimistic` aplica a atualização otimista, enquanto o estado real é atualizado após a ação assíncrona.

- **Quando usar?** Ideal para operações assíncronas (ex.: envio de formulários, chamadas a APIs) onde você quer feedback instantâneo.

- **Vantagens**:
  - UI mais fluida e responsiva.
  - Feedback visual imediato (ex.: "Adicionando...").
  - Fácil integração com ações assíncronas.

- **Cuidados**:
  - Use `startTransition` para atualizações suaves.
  - Gerencie o estado `pending` para indicar ações em andamento.
  - Trate erros para reverter atualizações otimistas, se necessário.

