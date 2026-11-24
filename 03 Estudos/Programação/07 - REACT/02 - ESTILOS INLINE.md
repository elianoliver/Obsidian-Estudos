Estilos inline são uma forma de aplicar CSS diretamente nos elementos JSX, usando objetos JavaScript dentro do próprio componente React — **sem precisar de um arquivo `.css` separado**.

## Diferença entre CSS tradicional e estilo inline em React

|CSS Tradicional|Estilo Inline em React|
|---|---|
|Usa **kebab-case** (`font-size`)|Usa **camelCase** (`fontSize`)|
|Usa arquivos `.css`|Usa objetos JavaScript|
|Escrito como texto|Escrito como código JS|

## Exemplo básico

```jsx
function Button({ buttonText }) {
  const defaultStyles = {
    backgroundColor: "#007BFF",
    color: "white",
    border: "none",
    borderRadius: "4px",
    padding: "10px 20px",
    fontSize: "16px",
    fontWeight: "bold",
    cursor: "pointer",
  };

  return <button style={defaultStyles}>{buttonText}</button>;
}
```

Aqui criamos um objeto `defaultStyles` com propriedades CSS (em camelCase) e o aplicamos ao botão usando `style={defaultStyles}`.

## Passando o objeto direto (sem variável)

```jsx
<button style={{ backgroundColor: "#007BFF", color: "white" }}>
  Clique aqui
</button>
```

Isso funciona bem quando o estilo é pequeno e simples.

## Estilos dinâmicos com props ou estado

```jsx
function DynamicButton({ isActive }) {
  const buttonStyles = {
    backgroundColor: isActive ? "green" : "red",
    color: "white",
    padding: "10px 15px",
  };

  return <button style={buttonStyles}>Login</button>;
}
```

O botão muda de cor dependendo da prop `isActive`. Essa é uma grande vantagem dos estilos inline: **adaptam-se dinamicamente**.

## Resumo final

- Estilos inline em React são definidos com objetos JavaScript.
- As propriedades CSS devem usar camelCase.
- Eles são ideais para:
    - Estilos simples
    - Estilos dinâmicos baseados em estado ou props        
- Para estilos complexos ou reutilizáveis, é melhor usar CSS externo ou CSS-in-JS como `styled-components`.