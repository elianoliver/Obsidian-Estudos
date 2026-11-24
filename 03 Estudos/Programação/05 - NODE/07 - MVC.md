Este é um exemplo de uma aplicação Node.js seguindo a arquitetura MVC (Model-View-Controller) para gerenciar uma lista de tarefas utilizando um banco de dados SQLite3.

#### Model (`model.js`):

O arquivo `model.js` define a classe `TaskModel`, que é responsável pela interação com o banco de dados SQLite3.

- `constructor`: Inicializa a instância da classe e cria o banco de dados SQLite3 em um arquivo chamado `tasks.db`. Ele também chama o método `initDatabase` para garantir que a tabela `tasks` seja criada se não existir.

- `initDatabase`: Define e executa uma instrução SQL para criar a tabela `tasks` no banco de dados, caso ela não exista.

- `getAllTasks`: Recupera todas as tarefas do banco de dados. O método aceita uma função de retorno de chamada que será chamada com os resultados.

- `addTask`: Adiciona uma nova tarefa ao banco de dados. Aceita a descrição e o status da conclusão da tarefa como parâmetros e uma função de retorno de chamada que será chamada com o ID da tarefa recém-inserida.

- `updateTask`: Atualiza uma tarefa existente no banco de dados com base no ID. Aceita o ID da tarefa, a nova descrição e o novo status de conclusão como parâmetros e uma função de retorno de chamada que será chamada com o número de linhas afetadas pela atualização.

- `deleteTask`: Exclui uma tarefa do banco de dados com base no ID. Aceita o ID da tarefa como parâmetro e uma função de retorno de chamada que será chamada com o número de linhas afetadas pela exclusão.
  
``` js
const sqlite3 = require('sqlite3').verbose();  

class TaskModel {
	constructor() {
		this.db = new sqlite3.Database('tasks.db');
		this.initDatabase();
	}  
	
	initDatabase() {
		const sql = `
	  CREATE TABLE IF NOT EXISTS tasks (
		id INTEGER PRIMARY KEY AUTOINCREMENT,
		description TEXT,
		completed BOOLEAN
	  )`;
		
		this.db.run(sql);
		}
	
	getAllTasks(callback) {
		const sql = 'SELECT * FROM tasks';
		this.db.all(sql, (err, rows) => {
		  callback(err, rows);
		});
	}
	
	addTask(description, completed, callback) {
		const sql = 'INSERT INTO tasks (description, completed) VALUES (?, ?)';
		this.db.run(sql, [description, completed], function(err) {
		  callback(err, this.lastID);
		});
	}
	
	updateTask(taskId, description, completed, callback) {
		const sql = 'UPDATE tasks SET description = ?, completed = ? WHERE id = ?';
		this.db.run(sql, [description, completed, taskId], function(err) {
		  callback(err, this.changes);
		});
	}
	
	deleteTask(taskId, callback) {
		const sql = 'DELETE FROM tasks WHERE id = ?';
		this.db.run(sql, [taskId], function(err) {
		  callback(err, this.changes);
		});
	}
}

module.exports = TaskModel;
```

#### Controller (`controller.js`):

O arquivo `controller.js` define a classe `TaskController`, que atua como um intermediário entre as rotas da aplicação e o modelo.

- `constructor`: Inicializa a instância da classe e cria uma instância da classe `TaskModel`.

- `getAllTasks`: Manipula a requisição para obter todas as tarefas chamando o método correspondente no `TaskModel`. Retorna as tarefas como uma resposta JSON.

- `addTask`: Manipula a requisição para adicionar uma nova tarefa chamando o método correspondente no `TaskModel`. Retorna os detalhes da tarefa recém-adicionada como uma resposta JSON.

- `updateTask`: Manipula a requisição para atualizar uma tarefa chamando o método correspondente no `TaskModel`. Retorna os detalhes da tarefa atualizada como uma resposta JSON.

- `deleteTask`: Manipula a requisição para excluir uma tarefa chamando o método correspondente no `TaskModel`. Retorna uma resposta JSON indicando o sucesso da exclusão.

``` js
const TaskModel = require('./model');

class TaskController {
  constructor() {
    this.taskModel = new TaskModel();
  }

  getAllTasks(req, res) {
    this.taskModel.getAllTasks((err, tasks) => {
      if (err) {
        return res.status(500).json({ error: 'Internal Server Error' });
      }
      res.json(tasks);
    });
  }

  addTask(req, res) {
    const { description, completed } = req.body;
    if (!description || typeof completed !== 'boolean') {
      return res.status(400).json({ error: 'Invalid input' });
    }

    this.taskModel.addTask(description, completed, (err, taskId) => {
      if (err) {
        return res.status(500).json({ error: 'Internal Server Error' });
      }
      res.json({ id: taskId, description, completed });
    });
  }

  updateTask(req, res) {
    const { id, description, completed } = req.body;
    if (!id || !description || typeof completed !== 'boolean') {
      return res.status(400).json({ error: 'Invalid input' });
    }

    this.taskModel.updateTask(id, description, completed, (err, affectedRows) => {
      if (err) {
        return res.status(500).json({ error: 'Internal Server Error' });
      }

      if (affectedRows === 0) {
        return res.status(404).json({ error: 'Task not found' });
      }

      res.json({ id, description, completed });
    });
  }

  deleteTask(req, res) {
    const taskId = req.params.id;
    if (!taskId) {
      return res.status(400).json({ error: 'Invalid input' });
    }

    this.taskModel.deleteTask(taskId, (err, affectedRows) => {
      if (err) {
        return res.status(500).json({ error: 'Internal Server Error' });
      }

      if (affectedRows === 0) {
        return res.status(404).json({ error: 'Task not found' });
      }

      res.json({ success: true });
    });
  }
}

module.exports = TaskController;
```

#### View (`app.js`):

O arquivo `app.js` configura e inicia o servidor Express, define rotas e lida com as solicitações HTTP.

- `app.get('/tasks', ...)`: Define uma rota para obter todas as tarefas. Chama o método `getAllTasks` no `TaskController` para processar a solicitação.

- `app.post('/tasks', ...)`: Define uma rota para adicionar uma nova tarefa. Chama o método `addTask` no `TaskController` para processar a solicitação.

- `app.put('/tasks', ...)`: Define uma rota para atualizar uma tarefa existente. Chama o método `updateTask` no `TaskController` para processar a solicitação.

- `app.delete('/tasks/:id', ...)`: Define uma rota para excluir uma tarefa com base no ID. Chama o método `deleteTask` no `TaskController` para processar a solicitação.

- `app.listen(...)`: Inicia o servidor Express na porta 3000.

```js
const express = require('express');
const bodyParser = require('body-parser');
const TaskController = require('./controller');

const app = express();
const port = 3000;

const taskController = new TaskController();

app.use(bodyParser.json());

app.get('/tasks', (req, res) => {
  taskController.getAllTasks(req, res);
});

app.post('/tasks', (req, res) => {
  taskController.addTask(req, res);
});

app.put('/tasks', (req, res) => {
  taskController.updateTask(req, res);
});

app.delete('/tasks/:id', (req, res) => {
  taskController.deleteTask(req, res);
});

app.listen(port, () => {
  console.log(`Server is running on port ${port}`);
});
```

### Observações Finais:

Este é um exemplo simplificado, e em uma aplicação real, você poderia adicionar mais validações, tratamentos de erros, autenticação, entre outros recursos, dependendo dos requisitos do projeto. Certifique-se de adaptar o código conforme necessário para atender aos requisitos específicos da sua aplicação.