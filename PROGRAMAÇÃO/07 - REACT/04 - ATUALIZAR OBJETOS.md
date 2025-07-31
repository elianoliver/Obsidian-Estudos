Em React, o estado (**state**) é **imutável**. Isso significa que **você não pode alterar o objeto diretamente**. Em vez disso, deve **criar uma nova cópia do objeto** com os dados atualizados e usar o **setter** (`setUser`, por exemplo) para aplicar a mudança.

## ❌ O que NÃO fazer

```jsx
import { useState } from "react";

function Profile() {
  const [user, setUser] = useState({
    name: "John Doe",
    age: 31,
    city: "LA",
  });

  // Change user age directly ============
  const handleAgeChange = (e) => {
    user.age = e.target.value;
    console.log(user);
  };
  // =====================================
  
  return (
    <div>
      <h1>User Profile</h1>
      <p>Name: {user.name}</p>
      <p>Age: {user.age}</p>
      <p>City: {user.city}</p>

      <h2>Update User Age </h2>
      <input type="number" value={user.age} onChange={handleAgeChange} />
    </div>
  );
}

export default Profile;
```

- Isso **muda o objeto**, mas o React **não re-renderiza** o componente.
- O valor até muda no `console.log`, mas **a tela não atualiza**.

## ✅ Forma correta: criando um novo objeto

```jsx
const handleAgeChange = (e) => {
  setUser((prevUser) => {
    const updatedUser = { ...prevUser, age: e.target.value };
    return updatedUser;
  });
};
```

- Aqui, usamos a **função de atualização** (`prevUser => ...`) para garantir que pegamos o valor mais recente.
    
- O operador **spread (`...`)** copia as propriedades do objeto anterior.
    
- Só **a propriedade que você quer mudar é substituída**.

## Atualizando vários campos com um único handler

```jsx
const handleChange = (e) => {
	const { name, value } = e.target;
	
	// atualiza dinamicamente qualquer campo
	setUser((prevUser) => (
		{...prevUser, [name]: value,}
	));
};
```

Para isso funcionar, **os inputs precisam ter o atributo `name`**:

```jsx
<input name="age" value={user.age} onChange={handleChange} />
<input name="name" value={user.name} onChange={handleChange} />
<input name="city" value={user.city} onChange={handleChange} />
```

## Exemplo completo

```jsx
import { useState } from "react";

function Profile() {
  const [user, setUser] = useState({ name: "John Doe", age: 31, city: "LA" });

  const handleChange = (e) => {
    const { name, value } = e.target;

    setUser((prevUser) => ({...prevUser, [name]: value}));
  };

  return (
    <div>
      <h1>User Profile</h1>
      <p>Name: {user.name}</p>
      <p>Age: {user.age}</p>
      <p>City: {user.city}</p>

      <h2>Update User Age </h2>
      <input type="number" name="age" value={user.age} onChange={handleChange} />
      <h2>Update User Name </h2>
      <input type="text" name="name" value={user.name} onChange={handleChange} />
      <h2>Update User City </h2>
      <input type="text" name="city" value={user.city} onChange={handleChange} />
    </div>
  );
}

export default Profile;
```

## Conclusão

- Nunca altere objetos no state diretamente.
    
- Sempre crie uma **nova cópia** com as mudanças usando o **spread (`...`)**.
    
- Use a **função atualizadora** do `useState` para garantir consistência.
    
- Inputs com o atributo `name` permitem um **único handler genérico**.