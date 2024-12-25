O `useState` em React funciona como uma "memória especial" para os componentes. Cada componente tem uma pequena área de armazenamento chamada estado (`state`), onde pode guardar informações importantes, como números, textos, ou até mesmo se algo está visível ou escondido.

No exemplo abaixo, ao utilizar `const [num, setNum] = useState(10)`, estamos dando ao componente uma caixinha de memória chamada `num` que começa com o valor 10. O `setNum` é como uma ferramenta para mudar o que está dentro dessa caixinha.

```jsx
// App.js
import React, { useState} from 'react';
import Numero from './components/Numero.js';

export default function App() {
    const [num, setNum] = useState(10);

    return (
        <>
            <p>Valor de num em App: {num}</p>
            <Numero num={num} setNum={setNum} />
        </>
    );
}
```

No componente `Numero`, quando clicamos no botão "Somar 10", estamos dizendo: "Ei, componente, use o `setNum` para mudar o valor da sua caixinha `num` adicionando 10 ao que já está lá dentro." Isso é ótimo porque, sempre que a caixinha `num` muda, o React entende que algo novo aconteceu e atualiza a parte da página que mostra esse número.

```jsx
// Numero.js
import React from 'react';

export default function Numero(props){
    return(
        <>
            <p>Valor de num em Numero: {props.num}</p>
            <button onClick={() => {props.setNum(props.num + 10)}}>Somar 10</button>
        </>
    );
}
```

Em resumo, o `useState` é uma memória especial que mantém o controle de informações importantes para o componente, e sempre que algo muda nessa memória, o React cuida automaticamente de mostrar essas mudanças na interface.