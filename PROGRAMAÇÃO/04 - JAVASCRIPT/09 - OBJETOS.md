## JavaScript Object

No JavaScript, os objetos são estruturas de dados que permitem armazenar informações de várias maneiras. Eles consistem em pares de chave-valor, onde cada chave é um nome e cada valor é o dado associado a essa chave.

**1. Criando Objetos em JavaScript:**
```javascript
let usuario = {
   userId: "User1", // Atributo
   password: "SohEuSei",
   nome: "Joao"
}
```
Aqui, criamos um objeto chamado `usuario` com três atributos: `userId`, `password` e `nome`. Os atributos são definidos com seus respectivos valores.

**2. Modificando Valores de Atributos:**
```javascript
usuario.userId = "XPTO";
console.log(usuario.userId);
```
Neste trecho, alteramos o valor do atributo `userId` do objeto `usuario` para "XPTO" e, em seguida, imprimimos o novo valor, que é "XPTO".

**3. Acessando Atributos de Objetos:**
```javascript
pessoa.nome = "Johan";
pessoa["nome"] = "Joana";
pessoa["idade"] = 26;
```
Aqui, estamos acessando os atributos do objeto `pessoa` e modificando seus valores usando duas notações diferentes. A primeira notação usa um ponto (.) para acessar o atributo, enquanto a segunda usa colchetes [] e uma string com o nome do atributo.

**4. Aninhamento de Objetos (Objeto dentro de Objeto):**
```javascript
const user = {
    id: "XPTO123",
    funcao: "Administrador",
    bloqueado: true,
    instancias: 2,
    navegadores: ["IE", "chrome", "edge"],
    pessoa1: {
        nome: "Joao",
        sobrenome: "Silva",
        idade: 25,
        sexo: "m",
        nomeCompleto: function() {
            return this.nome + " " + this.sobrenome;
        }
    }
}
```
Aqui, criamos um objeto chamado `user` que possui diversos atributos, incluindo um objeto aninhado chamado `pessoa1`. Este objeto aninhado tem seus próprios atributos, incluindo uma função `nomeCompleto` que concatena o nome e sobrenome.

**5. Acessando Atributos de Objetos Aninhados:**
```javascript
console.log(user.pessoa1.nomeCompleto()); // Saída: "Joao Silva"
console.log(user.pessoa1.nome + " " + user.pessoa1.sobrenome); // Saída: "Joao Silva"
console.log(user.navegadores[1]); // Saída: "chrome"
```
Neste trecho, demonstramos como acessar atributos de objetos aninhados, como o nome completo da pessoa, nome e sobrenome, bem como um elemento específico do array `navegadores`.