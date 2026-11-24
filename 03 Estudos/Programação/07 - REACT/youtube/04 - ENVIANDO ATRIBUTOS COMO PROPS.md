Ao desenvolver aplicações React, é comum a necessidade de transmitir dados entre componentes. Para facilitar essa comunicação, utilizamos `props` (propriedades). As `props` são mecanismos que permitem passar informações de um componente pai para um componente filho. No exemplo abaixo, o componente `Dados` recebe propriedades específicas, como `canal`, `youtube`, e `curso`, que são então utilizadas para renderizar informações dentro do componente.

```jsx
// App.js
import React from 'react';
import Dados from './components/Dados.js';

export default function App() {

    return (
        <>
            <Dados
                canal='CFB Cursos'
                youtube='youtube.com/cfbcursos'
                curso='React' />
        </>
    )
}
```

```jsx
// Dados.js
import React from 'react';

export default function Dados(props){
    return (
        <section>
            <p>Canal: {props.canal}</p>
            <p>Youtube: {props.youtube}</p>
            <p>Curso: {props.curso}</p>
        </section>
    )
}
```

No código acima, o componente `Dados` recebe as `props` `canal`, `youtube`, e `curso` de App.js, e as utiliza para exibir informações específicas na renderização. Dessa forma, o componente pai `App` pode fornecer dados dinâmicos para o componente filho `Dados`, permitindo a personalização e reutilização flexível do mesmo componente em diferentes contextos. O uso de `props` é fundamental para a construção de componentes React mais dinâmicos e adaptáveis, contribuindo para a flexibilidade e escalabilidade da aplicação.

### PASSANDO EXPRESSÕES COMO PROPS
Uma dica valiosa ao trabalhar com `props` no React é lembrar que você pode passar não apenas valores estáticos, mas também expressões e variáveis como propriedades. Isso proporciona uma flexibilidade significativa ao personalizar os componentes filhos com base em dados dinâmicos. No exemplo abaixo, uma constante `curso` é passada como propriedade `curso` para o componente `Dados` no arquivo `App.js`, ilustrando como você pode dinamicamente ajustar o conteúdo do componente filho com base em variáveis ou expressões.

```jsx
// App.js
import React from 'react';
import Dados from './components/Dados.js';

export default function App() {
    const canal = "CBF Cursos";
    const youtube = "youtube.com/cfbcursos";
    const curso = "React";

    return (
        <>
            <Dados
                canal={canal}
                youtube={youtube}
                curso={curso} />
        </>
    )
}
```

Dentro do componente `App`, as variáveis `canal`, `youtube`, e `curso` são passadas como `props` para o componente `Dados`. Isso permite que você adapte dinamicamente o conteúdo do componente filho com base nas variáveis declaradas no componente pai, tornando a aplicação mais dinâmica e fácil de manter. A utilização de expressões e variáveis como `props` é uma prática comum para transmitir dados entre componentes de maneira flexível e eficaz no React.