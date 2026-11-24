## **Por que importar e exportar?**

Em projetos React, os **componentes são organizados em arquivos separados** para facilitar a manutenção e reutilização. Para usá-los em outros arquivos, é preciso **exportar o componente** onde ele foi criado e **importar** onde será utilizado.

## Exemplo de Componente `Cat` (em `Cat.jsx`)

```jsx
function Cat() {
  return (
    <div className="card">
      <h2>Mr. Whiskers</h2>
      <img
        src="https://cdn.freecodecamp.org/curriculum/cat-photo-app/running-cats.jpg"
        alt="Cute cats running in the grass."
      />
    </div>
  );
}
```

## **Exportando o componente**

#### Jeito 1: Exportação depois da definição (forma comum)

```jsx
function Cat() {
  // JSX do componente
}

export default Cat;
```

#### Jeito 2: Exportação direta (mais compacto)

```jsx
export default function Cat() {
  // JSX do componente
}
```

Usamos `export default` porque esse será **o principal item exportado** do arquivo.

## **Importando o componente**

Para usar o `Cat` em outro arquivo (por exemplo, em `App.jsx`), você faz:

```jsx
import Cat from "./Cat";
```

- O caminho `"./Cat"` se refere ao arquivo `Cat.jsx` (não precisa colocar a extensão).
    
- O nome `Cat` deve **bater com o nome do componente exportado**.
    
## **Usando o componente importado**

Dentro do componente principal (`App`), basta usar:

```jsx
import Cat from "./Cat";

export default function App() {
  return (
    <Cat />
  );
}
```

Assim, o componente `Cat` será renderizado na tela.

## **Organização de projeto**

- O componente `App` geralmente fica em `src/App.jsx`.
    
- Arquivos como `Cat.jsx` ficam dentro da pasta `src` ou dentro de uma subpasta `components/`, dependendo da organização.
    
- Cada componente pode ficar em seu próprio arquivo, facilitando a reutilização e legibilidade.

## Conclusão

Importar e exportar componentes em React permite **organizar melhor o código**, **reutilizar componentes** e **escalar aplicações com facilidade**. Com o tempo, você vai se acostumar a criar componentes separados e montá-los como peças de LEGO para construir interfaces completas.