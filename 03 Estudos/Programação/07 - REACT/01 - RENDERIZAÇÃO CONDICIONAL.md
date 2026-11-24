A **renderização condicional** em React permite que você **mostre ou oculte partes da interface** dependendo de condições específicas, como se o usuário está logado, se há uma mensagem para exibir, etc. Isso torna seus componentes mais dinâmicos e úteis.

## Usando `if` tradicional (fora do JSX)

Útil quando a lógica é mais complexa ou há vários retornos possíveis.

```jsx
function Greeting({ isLoggedIn }) {
  if (isLoggedIn) {
    return <h1>Welcome back!</h1>;
  }
  return <h1>Please sign in</h1>;
}
```

🔎 O componente mostra uma mensagem diferente dependendo do valor de `isLoggedIn`.

## Usando o operador ternário (`? :`) no JSX

Bom para **condições simples** diretamente no JSX:

```jsx
function Greeting({ isLoggedIn }) {
  return <h1>{isLoggedIn ? "Welcome back!" : "Please sign in."}</h1>;
}
```

O operador ternário avalia a condição e retorna um dos dois valores.

## Usando o operador lógico AND (`&&`)

Ideal quando você **só quer mostrar algo se a condição for verdadeira**, e nada caso contrário:

```jsx
function Notification({ message }) {
  return (
    <div>
      {message && <p>{message}</p>}
    </div>
  );
}
```

Aqui, `<p>` só aparece se `message` tiver algum valor (ou seja, for "truthy").

Esse é um padrão muito comum e idiomático no React para **renderização condicional**. É uma forma concisa de dizer: "Se `message` existe (e não é um valor falsy, como `false`, `0`, `null`, `undefined`, `NaN`, ou uma string vazia `''`), então renderize o parágrafo com a mensagem; caso contrário, não renderize nada aqui.

## Conclusão

Com essas 3 abordagens, você pode tornar seus componentes React **mais inteligentes e responsivos ao estado da aplicação**:

|Técnica|Quando usar|
|---|---|
|`if/else` tradicional|Condições mais longas ou múltiplos retornos|
|Operador ternário|Condições simples diretamente no JSX|
|Operador `&&`|Mostrar algo **ou nada**, sem `else`|

Essas técnicas são a base para criar interfaces que **reagem ao que o usuário faz** ou ao que está acontecendo na aplicação.