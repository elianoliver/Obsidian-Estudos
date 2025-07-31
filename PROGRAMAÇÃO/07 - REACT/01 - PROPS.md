## O que são props?

**Props** (abreviação de _properties_) são **valores que um componente pai envia para um componente filho**. Com elas, é possível **personalizar o comportamento e a exibição** de um componente sem alterar seu código interno.

## Exemplo básico sem props

```jsx
function Greeting() {
  const developerName = "Jessica";
  return <h1>Hi {developerName}!</h1>;
}

function App() {
  return <Greeting />;
}
```

Esse código exibe "Hi Jessica!", mas o nome está **fixo**, o que torna o componente pouco reutilizável.

## Usando props para tornar o componente flexível

### Passando dados para o componente

```jsx
// PAI
function App() {
  return <Greeting name="Jessica" />;
}
// FILHA
function Greeting(props) {
  return <h1>Hi {props.name}!</h1>;
}
```

- `props` é um **objeto** com as propriedades passadas.
- `props.name` acessa o valor enviado.
- Agora o nome pode ser alterado facilmente sem mudar o componente `Greeting`.

### Reutilizando o mesmo componente com dados diferentes

```jsx
function App() {
  return (
    <>
      <Greeting name="Naomi" />
      <Greeting name="Tom" />
      <Greeting name="Oliver" />
    </>
  );
}
```

- O mesmo componente `Greeting` é usado várias vezes com **valores diferentes**, graças ao uso de props.
    
## Desestruturação para facilitar a leitura

```jsx
function Greeting({ name }) {
  return <h1>Hi {name}!</h1>;
}
```

- Isso evita a repetição de `props.` e **torna o código mais limpo**.
    
## Passando várias props de uma vez com o operador spread

### Componente que recebe várias props

```jsx
function DeveloperCard({ name, age, country }) {
  return (
    <div className="developer-card">
      <h1>Developer: {name}</h1>
      <p>Age: {age}</p>
      <p>Country: {country}</p>
    </div>
  );
}
```

### Passando um objeto como props com spread

```jsx
function App() {
  const developerObj = {
    name: "Alice",
    age: 30,
    country: "USA",
  };

  return <DeveloperCard {...developerObj} />;
}
```

- O `...developerObj` **espalha as propriedades** do objeto como props individuais.
- Ideal quando se trabalha com **listas de objetos**, como arrays de usuários.


```ad-attention
title: Props são Imutáveis

- Props **não podem ser alteradas** dentro do componente que as recebe.

- Se você precisa de valores que **podem mudar** (como entradas do usuário), deve usar **state** — que será abordado em lições futuras.

```


## Conclusão

Props permitem que você:

- Torne seus componentes **mais dinâmicos e reutilizáveis**.
- **Compartilhe dados** entre componentes.
- Escreva menos código repetitivo e com mais organização.
    

São essenciais para **criar interfaces complexas**, mantendo seu código **limpo e modular**.