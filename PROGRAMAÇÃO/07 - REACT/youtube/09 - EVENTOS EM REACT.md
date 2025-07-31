Em React, eventos são maneiras de interagir com os componentes, permitindo que a aplicação responda às ações do usuário, como cliques, teclas pressionadas, entre outros. No exemplo abaixo, vamos explorar como os eventos são utilizados para alternar entre as imagens de um LED vermelho e verde e para alterar o texto de um botão.

```jsx
// App.js
import React, { useState } from 'react';
import ledVermelho from './components/img/red.jpg'
import ledVerde from './components/img/green.png'

export default function App() {

    const [toggle, setToggle] = useState(false)
    
    return (
        <>
            <img style={{width:'50px'}} 
	            src={toggle ? ledVerde : ledVermelho} 
	            alt={toggle ? 'Led Verde' : 'Led Vermelho'} 
			/>
            <button onClick={() => setToggle(!toggle)}>
	            {toggle ? 'Desligar' : 'Ligar'}
            </button>
        </>
    )
}
```

No código acima, temos um componente funcional `App` que utiliza o `useState` para controlar o estado do LED (representado pelo estado `toggle`). A imagem do LED muda entre vermelho (`ledVermelho`) e verde (`ledVerde`) dependendo do valor de `toggle`. O botão também é um elemento interativo, e ao ser clicado, altera o valor de `toggle`, iniciando o processo de alternância entre ligado e desligado.

O evento principal aqui é o `onClick` associado ao botão. Quando o botão é clicado, a função `setToggle(!toggle)` é chamada. Esta função altera o estado do `toggle` para o seu oposto atual, iniciando a alternância. O React, em seguida, percebe essa mudança de estado e atualiza a interface automaticamente, refletindo a nova condição do LED e o texto do botão.

Assim, eventos em React oferecem uma maneira reativa e eficiente de lidar com as interações do usuário, permitindo que a interface da aplicação responda dinamicamente às ações do usuário.

### PASSANDO EVENTOS COMO PROPS
Neste tutorial, vamos explorar como controlar o estado de um componente em React usando eventos e comunicação entre componentes pai e filho. Abordaremos passo a passo o exemplo de um LED, detalhando o código e as funcionalidades para melhor compreensão.

**1.  Estrutura do Projeto**
Nosso projeto consiste em dois componentes:

- **Componente Pai (App.js):** Controla o estado geral do LED e o passa para o componente filho.
- **Componente Filho (Led.js):** Exibe a imagem do LED e controla o botão, atualizando o estado no componente pai.

**2. Componente Pai (App.js)**

- **Estado:** Usamos o hook `useState` para definir o estado inicial do LED como `desligado`.
- **Renderização:** A imagem do LED e o botão são renderizados de acordo com o estado atual.
- **Evento:** O clique no botão chama a função `setToggle` para atualizar o estado, alternando entre "ligado" e "desligado".

```jsx
// App.js
import React, { useState } from 'react';
import Led from './components/Led';

function App() {
	// Estado do LED (ligado/desligado)
	const [toggle, setToggle] = useState(false);
	
	return (
		<>
			<Led toggle={toggle} setToggle={setToggle} />
		</>
	);
}

export default App;
```

**3. Componente Filho (Led.js)**

- **Props:** Recebe `toggle` e `setToggle` do componente pai como props.
- **Imagem do LED:** Exibe a imagem do LED verde se `toggle` for `true` e a imagem vermelha se `false`.
- **Evento do Botão:** O clique no botão chama a função `setToggle` do componente pai, passando o valor negado de `toggle` para alternar o estado.

```jsx
// Led.js
import React from 'react';
import ledVermelho from './img/red.jpg';
import ledVerde from './img/green.png';

function Led({ toggle, setToggle }) {
	return (
	<>
		<img
			style={{ width: '50px' }}
			src={toggle ? ledVerde : ledVermelho}
			alt="Led"
		/>
		
		<button onClick={() => setToggle(!toggle)}>
			{toggle ? 'Desligar' : 'Ligar'}
		</button>
	</>
  );
}

export default Led;
```

**4. Vantagens e Considerações**

- **Controle centralizado:** O estado é gerenciado no componente pai, facilitando a manutenção e evitando código redundante.
- **Escalabilidade:** A estrutura é facilmente adaptável para componentes mais complexos com diversos estados e funcionalidades.
- **Comunicação clara:** O uso de props facilita a comunicação entre os componentes, definindo um canal claro para troca de informações.