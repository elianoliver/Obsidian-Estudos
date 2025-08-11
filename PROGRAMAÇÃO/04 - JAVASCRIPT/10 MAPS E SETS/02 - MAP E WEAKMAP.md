## O que é um Map em JavaScript?

Um **Map** é um objeto nativo do JavaScript, introduzido no ES6 (ECMAScript 2015), que armazena pares **chave-valor**, semelhante a um objeto comum. No entanto, ele é mais flexível porque permite que **as chaves sejam de qualquer tipo de dado**, incluindo números, strings, objetos, funções ou até valores booleanos. Diferentemente de objetos regulares, que usam apenas strings ou símbolos como chaves, o Map é ideal para cenários onde você precisa de chaves mais variadas.

#### Principais Características do Map

- **Chaves de Qualquer Tipo**: As chaves podem ser primitivos (números, strings, booleanos) ou objetos (incluindo funções ou arrays).
  
- **Valores Únicos por Chave**: Cada chave está associada a um único valor, e se você definir um novo valor para uma chave existente, o valor antigo é substituído.
  
- **Iterável**: Você pode percorrer os pares chave-valor com métodos como `forEach`, `keys()`, `values()` ou `entries()`.
  
- **Propriedade Size**: A propriedade `size` indica quantos pares chave-valor estão no Map.
  
- **Referências Fortes**: As chaves e valores são mantidos fortemente, ou seja, não são removidos automaticamente pelo coletor de lixo, mesmo que não sejam mais referenciados em outro lugar no código.

### Como Criar e Usar um Map
Você cria um Map usando o construtor `Map`. Ele pode ser inicializado vazio ou com pares chave-valor:

```javascript
// Map vazio
const meuMap = new Map();

// Map com valores iniciais
const mapaArvores = new Map([
  [{ tipo: 'decídua' }, 'Bordo'],
  [['floresta', 'bosque'], 'Pinheiro'],
  [42, 'Carvalho'],
  [true, 'Bétula'],
  [function() { return 'Eu sou uma chave função'; }, 'Salgueiro'],
]);
```

Ao exibir um Map no console, ele aparece assim:
```javascript
console.log(mapaArvores);
/*
Saída:
Map(5) {
  {tipo: 'decídua'} => 'Bordo',
  ['floresta', 'bosque'] => 'Pinheiro',
  42 => 'Carvalho',
  true => 'Bétula',
  ƒ => 'Salgueiro'
}
*/
```

Você pode adicionar pares chave-valor com o método `set()`:
```javascript
const mapaArvores = new Map();
mapaArvores.set({ tipo: 'decídua' }, 'Bordo');
mapaArvores.set([1, 2], 'Pinheiro');
mapaArvores.set(42, 'Carvalho');
mapaArvores.set(true, 'Bétula');
mapaArvores.set(function() { return 'Eu sou uma chave função'; }, 'Salgueiro');
```

### Métodos Comuns do Map
Aqui estão os principais métodos para trabalhar com um Map:

#### 1. `set(chave, valor)`
Adiciona ou atualiza um par chave-valor.
```javascript
mapaArvores.set('novaChave', 'Acácia');
```

#### 2. `get(chave)`
Retorna o valor associado à chave especificada.
```javascript
console.log(mapaArvores.get(42)); // 'Carvalho'
```

#### 3. `has(chave)`
Verifica se uma chave existe no Map.
```javascript
console.log(mapaArvores.has(true)); // true
```

#### 4. `delete(chave)`
Remove um par chave-valor.
```javascript
mapaArvores.delete(true);
console.log(mapaArvores.has(true)); // false
```

#### 5. `clear()`
Remove todos os pares chave-valor.
```javascript
mapaArvores.clear();
console.log(mapaArvores); // Map(0) {}
```

#### 6. `forEach(callback)`
Itera sobre os pares chave-valor.
```javascript
mapaArvores.forEach((valor, chave) => console.log(`${chave}: ${valor}`));
// Saída:
// [object Object]: Bordo
// 1,2: Pinheiro
// 42: Carvalho
// true: Bétula
// function: Salgueiro
```

#### 7. `entries()`
Retorna um iterador com arrays no formato `[chave, valor]`.
```javascript
console.log(mapaArvores.entries());
// Saída: MapIterator {[{tipo: 'decídua'}, 'Bordo'], [['floresta', 'bosque'], 'Pinheiro'], ...}
```

#### 8. `keys()`
Retorna um iterador com as chaves do Map.
```javascript
console.log(mapaArvores.keys());
// Saída: MapIterator {{tipo: 'decídua'}, ['floresta', 'bosque'], 42, true, ƒ}
```

#### 9. `values()`
Retorna um iterador com os valores do Map.
```javascript
console.log(mapaArvores.values());
// Saída: MapIterator {'Bordo', 'Pinheiro', 'Carvalho', 'Bétula', 'Salgueiro'}
```

#### 10. `size`
Propriedade que retorna o número de pares chave-valor.
```javascript
console.log(mapaArvores.size); // 5
```

### Casos de Uso do Map

- Associar dados a chaves de qualquer tipo, como objetos ou funções.
  
- Gerenciar coleções de dados onde a ordem de inserção importa (os Maps mantêm a ordem dos pares).
  
- Substituir objetos regulares quando você precisa de chaves que não sejam strings ou símbolos.

## O que é um WeakMap em JavaScript?

Um **WeakMap** é uma coleção de pares chave-valor semelhante ao Map, mas com uma diferença crucial: **as chaves devem ser objetos** (ou símbolos, embora menos comum), e essas chaves são mantidas com **referências fracas**. Isso significa que, se uma chave não for mais referenciada em outro lugar no código, o coletor de lixo do JavaScript pode removê-la do WeakMap, liberando memória.

#### **Principais Características do WeakMap**

- **Apenas Objetos como Chaves**: As chaves devem ser objetos; primitivos como números ou strings não são permitidos.
  
- **Referências Fracas**: As chaves são mantidas de forma fraca, permitindo que sejam removidas pelo coletor de lixo se não houver outras referências a elas.
  
- **Não Iterável**: Não é possível percorrer os pares chave-valor com `forEach` ou laços.
  
- **Métodos Limitados**: Suporta apenas `set()`, `get()`, `has()` e `delete()`.
  
- **Sem Propriedade Size**: Não há como verificar quantos pares estão no WeakMap.
  
- **Conteúdo Opaco**: Você não pode inspecionar diretamente os itens de um WeakMap (exibir no console não mostra os pares).

### **Como Criar e Usar um WeakMap**
Você cria um WeakMap com o construtor `WeakMap`:

```javascript
const meuWeakMap = new WeakMap();
```

Você pode adicionar pares chave-valor com `set()`, desde que a chave seja um objeto:
```javascript
const mapaFracoArvores = new WeakMap();

mapaFracoArvores.set({ id: 1 }, 'Bordo');
mapaFracoArvores.set({ id: 2 }, 'Pinheiro');
mapaFracoArvores.set({ id: 3 }, 'Carvalho');
mapaFracoArvores.set({ id: 4 }, 'Bétula');
mapaFracoArvores.set({ id: 5 }, 'Salgueiro');

console.log(mapaFracoArvores);
/*
Saída:
WeakMap {{…} => 'Bordo', {…} => 'Pinheiro', {…} => 'Carvalho', {…} => 'Bétula', {…} => 'Salgueiro'}
*/
```

Se você tentar usar uma chave que não seja um objeto, receberá um erro:
```javascript
mapaFracoArvores.set(42, 'Carvalho'); // Erro: Invalid value used as weak map key
```

Você pode usar outros métodos como:
```javascript
const chave = { id: 1 };
console.log(mapaFracoArvores.get(chave)); // 'Bordo'
console.log(mapaFracoArvores.has(chave)); // true
mapaFracoArvores.delete(chave);
console.log(mapaFracoArvores.has(chave)); // false
```

Se a chave de um objeto for definida como `null` e não houver outras referências, o coletor de lixo pode remover o par do WeakMap:
```javascript
let chave = { id: 1 };
mapaFracoArvores.set(chave, 'Bordo');
chave = null; // Sem outras referências
// O coletor de lixo pode remover o par do WeakMap
```

### **Casos de Uso do WeakMap**

- **Gerenciamento de Memória**: Associar dados a objetos sem impedir que sejam coletados pelo garbage collector (por exemplo, armazenar metadados temporários).
  
- **Cache de Objetos**: Armazenar informações associadas a objetos que podem ser descartados quando não forem mais necessários.
  
- **Prevenir Vazamentos de Memória**: Ideal para cenários onde você quer evitar manter objetos na memória desnecessariamente.

## **Diferenças Principais Entre Map e WeakMap**

Aqui está uma comparação clara para destacar as diferenças entre Map e WeakMap:

| **Característica**        | **Map**                              | **WeakMap**                          |
|---------------------------|--------------------------------------|--------------------------------------|
| **Tipo de Chave**         | Qualquer tipo de dado (primitivos, objetos, funções, etc.) | Apenas objetos (e símbolos)         |
| **Referenciamento**       | Forte (impede coleta de lixo)        | Fraco (permite coleta de lixo)       |
| **Iteração**              | Suporta `forEach`, `keys()`, `values()`, `entries()` | Não iterável                         |
| **Propriedade Size**      | Sim (`size`)                        | Não                                  |
| **Métodos**               | `set`, `get`, `has`, `delete`, `clear`, `forEach`, `keys`, `values`, `entries` | Apenas `set`, `get`, `has`, `delete` |
| **Conteúdo Visível**      | Sim (pode exibir ou iterar pares)    | Não (conteúdo opaco)                 |
| **Caso de Uso**           | Associar dados a chaves de qualquer tipo | Associar dados a objetos com eficiência de memória |

### **Exemplo para Ilustrar a Diferença**
Com um **Map**, você pode usar qualquer tipo de chave e iterar pelos pares:

```javascript
const mapaArvores = new Map();
mapaArvores.set(42, 'Carvalho');
mapaArvores.set(true, 'Bétula');
mapaArvores.forEach((valor, chave) => console.log(`${chave}: ${valor}`));
// Saída:
// 42: Carvalho
// true: Bétula
```

Com um **WeakMap**, as chaves devem ser objetos, e não é possível iterar:
```javascript
const mapaFracoArvores = new WeakMap();
let chave = { id: 1 };
mapaFracoArvores.set(chave, 'Bordo');
console.log(mapaFracoArvores.get(chave)); // 'Bordo'
chave = null; // Sem outras referências
// O coletor de lixo pode remover o par do WeakMap
```

### **Quando Usar Map vs. WeakMap**

- Use um **Map** quando:
  - Você precisa associar valores a chaves de qualquer tipo (primitivos, objetos, funções, etc.).
  - Você quer iterar sobre os pares chave-valor ou verificar o tamanho da coleção.
  - Você está gerenciando dados onde a ordem de inserção ou a persistência dos dados é importante.
    
- Use um **WeakMap** quando:
  - Você só precisa associar dados a objetos e quer que esses objetos sejam coletados pelo garbage collector se não forem mais referenciados.
  - Você não precisa iterar ou inspecionar a coleção.
  - Você está lidando com cenários como cache ou metadados temporários, onde a eficiência de memória é prioritária.

## **Resumo**

- Um **Map** é uma coleção flexível de pares chave-valor que aceita chaves de qualquer tipo, com métodos robustos para iteração e manipulação.

- Um **WeakMap** é uma coleção restrita a chaves de objetos, com referências fracas, projetada para cenários onde a eficiência de memória é crucial e iteração não é necessária.
  
- A escolha entre Map e WeakMap depende se você precisa de flexibilidade para trabalhar com diferentes tipos de chaves (Map) ou eficiência de memória para rastrear objetos (WeakMap).

Compreendendo essas diferenças, você pode escolher a ferramenta certa para seu projeto em JavaScript, seja para gerenciar dados associados a chaves variadas ou para rastrear objetos de forma eficiente sem causar vazamentos de memória.