## **O que é um Set em JavaScript?**

Um **Set** é um objeto nativo do JavaScript, introduzido no ES6 (ECMAScript 2015), que permite armazenar **valores únicos** de **qualquer tipo de dado** (como números, strings, objetos ou até tipos misturados). A característica principal de um Set é garantir que cada valor apareça apenas uma vez, eliminando duplicatas automaticamente.

### Principais Características do Set

- **Valores Únicos**: Se você tentar adicionar um valor que já existe, ele será ignorado.
  
- **Tipos de Dados Flexíveis**: Pode armazenar primitivos (números, strings, booleanos) e referências a objetos.
  
- **Iterável**: Você pode percorrer os valores com métodos como `forEach` ou um laço `for...of`.
  
- **Propriedade Size**: A propriedade `size` indica quantos itens estão no Set.
  
- **Referências Fortes**: Os valores em um Set são mantidos fortemente, ou seja, não são removidos automaticamente pelo coletor de lixo do JavaScript, mesmo que não sejam mais referenciados em outro lugar no código.

### Como Criar e Usar um Set
Você cria um Set usando o construtor `Set`. Ele pode ser inicializado vazio ou com valores:

```javascript
// Set vazio
const meuSet = new Set();

// Set com valores iniciais
const conjuntoArvores = new Set(['Baobá', 'Jaca', 'Mopane', 'Fruta-pão']);
```

Ao exibir um Set no console, ele aparece assim:
```javascript
const conjuntoArvores = new Set(['Baobá', 'Jaca', 'Mopane', 'Fruta-pão']);
console.log(conjuntoArvores);
// Saída: Set(4) {'Baobá', 'Jaca', 'Mopane', 'Fruta-pão'}
```

Você pode adicionar itens com o método `add()`:
```javascript
const conjuntoArvores = new Set(['Baobá', 'Jaca', 'Mopane', 'Fruta-pão']);
conjuntoArvores.add('Baobá'); // Ignorado, pois 'Baobá' já existe
console.log(conjuntoArvores);
// Saída: Set(4) {'Baobá', 'Jaca', 'Mopane', 'Fruta-pão'}
```

### Métodos Comuns do Set
Aqui está uma lista dos principais métodos para manipular um Set:

#### 1. `add(valor)`
Adiciona um valor ao Set (duplicatas são ignoradas).
```javascript
const conjuntoArvores = new Set(['Baobá', 'Jaca', 'Mopane', 'Fruta-pão']);
conjuntoArvores.add('Acácia');
```

#### 2. `delete(valor)`
Remove um valor específico.
```javascript
const conjuntoArvores = new Set(['Baobá', 'Jaca', 'Mopane', 'Fruta-pão']);
conjuntoArvores.delete('Fruta-pão');
console.log(conjuntoArvores); // Set(3) {'Baobá', 'Jaca', 'Mopane'}
```

#### 3. `has(valor)`
Verifica se um valor existe no Set.
```javascript
const conjuntoArvores = new Set(['Baobá', 'Jaca', 'Mopane', 'Fruta-pão']);
console.log(conjuntoArvores.has('Fruta-pão')); // false
```

#### 4. `clear()`
Remove todos os itens do Set.
```javascript
const conjuntoArvores = new Set(['Baobá', 'Jaca', 'Mopane', 'Fruta-pão']);
conjuntoArvores.clear();
console.log(conjuntoArvores); // Set(0) {}
```

#### 5. `forEach(callback)`: 
Itera sobre os valores do Set.
```javascript
const conjuntoArvores = new Set(['Baobá', 'Jaca', 'Mopane', 'Fruta-pão']);
conjuntoArvores.forEach(arvore => console.log(arvore));
// Saída:
// Baobá
// Jaca
// Mopane
```

#### 6. `entries()`
Retorna um iterador com arrays no formato `[valor, valor]`.
```javascript
const conjuntoArvores = new Set(['Baobá', 'Jaca', 'Mopane', 'Fruta-pão']);
console.log(conjuntoArvores.entries());
// Saída: SetIterator {['Baobá', 'Baobá'], ['Jaca', 'Jaca'], ['Mopane', 'Mopane']}
```

#### 7. `keys()` e `values()`
Ambos retornam um iterador com os valores do Set (são idênticos em Sets).
```javascript
const conjuntoArvores = new Set(['Baobá', 'Jaca', 'Mopane', 'Fruta-pão']);
console.log(conjuntoArvores.values());
// Saída: SetIterator {'Baobá', 'Jaca', 'Mopane'}
```

#### 8. `size`
Propriedade (não método) que retorna o número de itens no Set.
```javascript
const conjuntoArvores = new Set(['Baobá', 'Jaca', 'Mopane', 'Fruta-pão']);
console.log(conjuntoArvores.size); // 3
```

### **Casos de Uso do Set**

Remover duplicatas de um array:
```javascript
const arrayComDuplicatas = [1, 2, 2, 3, 3, 4];
const valoresUnicos = [...new Set(arrayComDuplicatas)]; // [1, 2, 3, 4]
```

- Gerenciar uma coleção de itens únicos, como IDs de usuários ou tags.
- Realizar operações de conjuntos (união, interseção, diferença) de forma eficiente.

```js
const displayPlantsSet = () => {
  const catalogSet = new Set();

  // Create an array of the common names from the catalog
  const commonNames = Array.from(catalog.keys()).map(plant => plant.commonName);

  // Create a set from the array of common names
  commonNames.forEach(name => catalogSet.add(name));

  return catalogSet;
};
```

## **O que é um WeakSet em JavaScript?**

Um **WeakSet** é uma versão especializada do Set, também introduzida no ES6, mas com diferenças importantes. Ele é projetado para armazenar **referências fracas a objetos** (e símbolos, embora sejam menos comuns). Isso significa que, se um objeto armazenado em um WeakSet não for mais referenciado em outro lugar no código, o **coletor de lixo** do JavaScript pode removê-lo para liberar memória.

### Principais Características do WeakSet

- **Apenas Objetos**: Só pode armazenar objetos (ou símbolos), não primitivos como números ou strings.
  
- **Referências Fracas**: Os objetos são mantidos de forma fraca, permitindo que sejam removidos pelo coletor de lixo se não houver outras referências a eles.
  
- **Não Iterável**: Não é possível percorrer os conteúdos com `forEach` ou `for...of`.
  
- **Métodos Limitados**: Suporta apenas `add()`, `delete()` e `has()`.
  
- **Sem Propriedade Size**: Não há como verificar quantos itens estão no WeakSet.
  
- **Conteúdo Opaco**: Você não pode inspecionar diretamente os itens de um WeakSet (exibir no console não mostra os valores).

### Como Criar e Usar um WeakSet

Você cria um WeakSet com o construtor `WeakSet`:
```javascript
const conjuntoFracoArvores = new WeakSet();
```

Você pode adicionar objetos (não primitivos) a ele:
```javascript
const conjuntoFracoArvores = new WeakSet();
const baoba = { nome: 'Baobá' };
const jaca = { nome: 'Jaca' };

conjuntoFracoArvores.add(baoba);
conjuntoFracoArvores.add(jaca);

console.log(conjuntoFracoArvores.has(baoba)); // true
console.log(conjuntoFracoArvores.has(jaca)); // true
```

Se tentar adicionar um primitivo, você receberá um erro:
```javascript
const conjuntoFracoArvores = new WeakSet();
conjuntoFracoArvores.add('Baobá'); // Erro: Invalid value used in weak set
```

Ao exibir um WeakSet no console, os conteúdos não são visíveis diretamente:
```javascript
const conjuntoFracoArvores = new WeakSet();
console.log(conjuntoFracoArvores);
// Saída: WeakSet {{…}, {…}}
```

Se os objetos não forem mais referenciados em outro lugar e forem coletados pelo garbage collector, eles serão automaticamente removidos do WeakSet.

### **Métodos do WeakSet**

WeakSets suportam apenas três métodos:

1. **`add(objeto)`**: Adiciona um objeto ao WeakSet.
2. **`delete(objeto)`**: Remove um objeto.
3. **`has(objeto)`**: Verifica se um objeto está no WeakSet.

Exemplo:
```javascript
const conjuntoFracoArvores = new WeakSet();
const baoba = { nome: 'Baobá' }; 
conjuntoFracoArvores.add(baoba);
console.log(conjuntoFracoArvores.has(baoba)); // true
```

### **Casos de Uso do WeakSet**

- **Gerenciamento de Memória**: Rastrear objetos sem impedir que sejam coletados pelo garbage collector (por exemplo, marcar objetos como “visitados” em um algoritmo de travessia de grafos).
  
- **Rastreamento Temporário de Objetos**: Associar metadados a objetos sem afetar seu ciclo de vida.
  
- **Prevenir Vazamentos de Memória**: Útil em cenários onde você deseja evitar manter objetos na memória desnecessariamente.

## **Diferenças Principais Entre Set e WeakSet**

Aqui está uma comparação clara para destacar as diferenças entre Set e WeakSet:

| **Característica**        | **Set**                              | **WeakSet**                          |
|---------------------------|--------------------------------------|--------------------------------------|
| **Tipos de Valores**      | Qualquer tipo de dado (primitivos, objetos) | Apenas objetos (e símbolos)         |
| **Referenciamento**       | Forte (impede coleta de lixo)        | Fraco (permite coleta de lixo)       |
| **Iteração**              | Suporta `forEach`, `for...of`, etc.  | Não iterável                         |
| **Métodos**               | `add`, `delete`, `has`, `clear`, `entries`, `keys`, `values`, `forEach` | Apenas `add`, `delete`, `has`        |
| **Propriedade Size**      | Sim (`size`)                        | Não                                  |
| **Conteúdo Visível**      | Sim (pode exibir ou iterar valores)  | Não (conteúdo opaco)                 |
| **Caso de Uso**           | Coleções gerais de valores únicos    | Rastreamento eficiente de objetos    |

### **Exemplo para Ilustrar a Diferença**
Imagine que você está rastreando árvores em uma floresta. Com um **Set**, você pode armazenar os nomes delas (strings) ou objetos e percorrê-los:

```javascript
const conjuntoArvores = new Set(['Baobá', 'Jaca']);
conjuntoArvores.forEach(arvore => console.log(arvore)); // Baobá, Jaca
```

Com um **WeakSet**, você só pode armazenar objetos de árvores, e se esses objetos não forem mais referenciados em outro lugar, eles serão removidos automaticamente:

```javascript
const conjuntoFracoArvores = new WeakSet();
let arvore = { nome: 'Baobá' };
conjuntoFracoArvores.add(arvore);
console.log(conjuntoFracoArvores.has(arvore)); // true
arvore = null; // Sem outras referências ao objeto
// O coletor de lixo pode remover o objeto do WeakSet
```

### **Quando Usar Set vs. WeakSet**

- Use um **Set** quando:
  - Você precisa armazenar valores únicos de qualquer tipo (por exemplo, strings, números, objetos).
  - Você quer iterar sobre a coleção ou verificar seu tamanho.
  - Você está removendo duplicatas de um array ou gerenciando uma coleção de itens distintos.
    
- Use um **WeakSet** quando:
  - Você só precisa armazenar objetos (ou símbolos) e quer que eles sejam coletados pelo garbage collector se não forem mais referenciados.
  - Você não precisa iterar ou inspecionar a coleção.
  - Você está rastreando objetos temporariamente, como em cenários de cache ou metadados.

## **Resumo**

- Um **Set** é uma coleção versátil para armazenar valores únicos de qualquer tipo, com métodos robustos para manipulação e iteração.
  
- Um **WeakSet** é uma coleção leve, apenas para objetos, com referências fracas, projetada para rastreamento eficiente de memória onde iteração e inspeção direta não são necessárias.
  
- A escolha entre eles depende se você precisa de flexibilidade (Set) ou eficiência de memória com objetos (WeakSet).

Compreendendo essas diferenças, você pode escolher a ferramenta certa para seu projeto em JavaScript, seja para gerenciar uma lista de itens únicos ou rastrear objetos sem se preocupar com vazamentos de memória.