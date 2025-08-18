Em JavaScript, **propriedades e métodos estáticos** pertencem à **própria classe**, e não aos objetos (instâncias) criados a partir dela. Isso significa que você pode acessá-los diretamente usando o nome da classe, sem precisar criar uma instância com `new`. Eles são úteis para funcionalidades que estão relacionadas à classe como um todo, e não a um objeto específico.

Por exemplo, se você tem uma classe `Filme`, um método estático pode comparar dois filmes sem depender de uma instância específica. Da mesma forma, uma propriedade estática pode armazenar informações que pertencem à classe, como o número total de objetos criados.

## **Como definir e usar métodos estáticos?**

Um **método estático** é definido usando a palavra-chave **`static`** antes do nome do método. Ele é chamado diretamente na classe, sem a necessidade de criar um objeto.

#### **Exemplo 1: Método estático para comparar filmes**

Aqui está uma classe `Filme` com um método estático para comparar filmes com base na pontuação:

```javascript
class Filme {
  constructor(titulo, pontuacao) {
    this.titulo = titulo;
    this.pontuacao = pontuacao;
  }

  static compararFilmes(filmeA, filmeB) {
    if (filmeA.pontuacao > filmeB.pontuacao) {
      console.log(`${filmeA.titulo} tem uma pontuação maior.`);
    } else if (filmeA.pontuacao < filmeB.pontuacao) {
      console.log(`${filmeB.titulo} tem uma pontuação maior.`);
    } else {
      console.log("Os filmes têm a mesma pontuação.");
    }
  }
}
```

- **O que está acontecendo?**
  - O método `compararFilmes` é estático porque é definido com `static` e pertence à classe `Filme`, não a uma instância específica.
  - Ele recebe dois objetos `filmeA` e `filmeB` como parâmetros e compara suas pontuações, exibindo uma mensagem.

Exemplo de uso:
```javascript
const filmeA = new Filme("Filme A", 80);
const filmeB = new Filme("Filme B", 45);
Filme.compararFilmes(filmeA, filmeB); // Exibe: Filme A tem uma pontuação maior.
```

- **Observação**: Note que chamamos `Filme.compararFilmes()` diretamente na classe `Filme`, sem criar um objeto. Isso é possível porque o método é estático.

### **Exemplo 2: Método estático como "fábrica"**

Métodos estáticos também são usados como **métodos de fábrica** (factory methods), que criam objetos com configurações predefinidas. Veja um exemplo com uma classe `Pizza`:

```javascript
class Pizza {
  constructor(tipo, preco) {
    this.tipo = tipo;
    this.preco = preco;
  }

  static criarMargherita() {
    return new this("Margherita", 6.99);
  }
}
```

- **O que está acontecendo?**
  - O método estático `criarMargherita` cria uma nova instância da classe `Pizza` com valores predefinidos (`tipo: "Margherita"`, `preco: 6.99`).
    
  - Dentro de um método estático, **`this`** se refere à própria classe (`Pizza`), permitindo criar uma nova instância com `new this`.

Exemplo de uso:
```javascript
const minhaPizza = Pizza.criarMargherita();
console.log(minhaPizza.tipo); // Exibe: Margherita
console.log(minhaPizza.preco); // Exibe: 6.99
```

- **Observação**: O método `criarMargherita` é chamado diretamente na classe (`Pizza.criarMargherita()`), e ele retorna um novo objeto `Pizza` pronto para uso.

## **Como definir e usar propriedades estáticas?**

Uma **propriedade estática** também pertence à classe, não às instâncias, e é definida com a palavra-chave `static`. Ela é útil para armazenar informações compartilhadas por todas as instâncias da classe.

### **Exemplo: Contador de pizzas vendidas**

```javascript
class Pizza {
  static numeroDePizzasVendidas = 0;

  constructor(tipo) {
    this.tipo = tipo;
    Pizza.numeroDePizzasVendidas++; // Incrementa a propriedade estática
  }
}
```

- **O que está acontecendo?**
  - A propriedade estática `numeroDePizzasVendidas` é inicializada com `0` e pertence à classe `Pizza`.
    
  - Toda vez que uma nova instância de `Pizza` é criada, o construtor incrementa essa propriedade estática.

Exemplo de uso:
```javascript
const pizza1 = new Pizza("Margherita");
const pizza2 = new Pizza("Napolitana");
console.log(Pizza.numeroDePizzasVendidas); // Exibe: 2
```

- **Observação**: A propriedade `numeroDePizzasVendidas` é acessada diretamente na classe (`Pizza.numeroDePizzasVendidas`), não em uma instância específica como `pizza1` ou `pizza2`.

## **Por que usar propriedades e métodos estáticos?**

1. **Pertencem à classe**: São úteis para funcionalidades que não dependem de uma instância específica, mas estão relacionadas à classe como um todo.
   
2. **Evitam repetição**: Agrupam lógica relacionada (como comparar filmes ou contar pizzas) dentro da própria classe, melhorando a organização e a manutenção do código.
   
3. **Métodos de fábrica**: Permitem criar objetos com configurações predefinidas, simplificando a criação de instâncias.
   
4. **Eficiência**: Como não exigem a criação de instâncias, economizam memória e tornam o código mais direto em alguns casos.

## **Resumo visual**

Pense em propriedades e métodos estáticos como **ferramentas da classe**:

- Imagine que a classe `Pizza` é uma pizzaria. Métodos estáticos (como `criarMargherita`) são como um menu fixo que a pizzaria oferece, disponível sem precisar de um pedido específico. Propriedades estáticas (como `numeroDePizzasVendidas`) são como um contador de vendas na parede da pizzaria, que pertence ao estabelecimento, não a uma pizza individual.
  
- Em contrapartida, propriedades e métodos normais (não estáticos) pertencem às pizzas individuais criadas (os objetos).

## **Pontos-chave**

- **Propriedades e métodos estáticos**: Pertencem à classe, não às instâncias, e são acessados diretamente com o nome da classe (ex.: `Classe.metodo()`).
  
- **Definição**: Usam a palavra-chave `static` antes do nome do método ou propriedade.
  
- **Uso de `this`**: Em métodos estáticos, `this` se refere à própria classe.
  
- **Métodos de fábrica**: Métodos estáticos podem criar instâncias com configurações predefinidas.
  
- **Vantagens**: Melhoram a organização, reutilização e eficiência do código.