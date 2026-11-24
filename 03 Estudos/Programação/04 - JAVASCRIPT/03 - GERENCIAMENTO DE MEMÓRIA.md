# O que é gerenciamento de memória?

Quando seu código JavaScript roda (por exemplo, no navegador), ele **usa memória** para armazenar:

- Variáveis
- Objetos
- Funções  

Ou seja, tudo que o programa precisa para funcionar.

Gerenciar memória significa:
- Alocar memória quando algo novo é criado
- Liberar memória quando aquilo não é mais necessário

## Como o JavaScript faz isso?

Diferente de algumas linguagens em que o programador precisa **gerenciar a memória manualmente**, o JavaScript faz isso de forma **automática**. Esse processo é chamado de:

## Coleta de Lixo (Garbage Collection)

#### Como funciona?

1. Alocação automática  
    Sempre que você cria algo: O JavaScript reserva memória automaticamente.
    
```js
let nome = "Ana";
let user = { idade: 20 };
``` 
    
2. **Uso da memória**  
    Seu código usa esses dados enquanto precisa deles.
    
3. **Coleta de lixo (liberação)**  
    Quando nada mais faz referência a um valor, o JavaScript libera essa memória.  
    
```js
let x = { teste: 123 };
x = null; // o objeto anterior pode ser coletado
```

## Atenção: armadilhas comuns

Mesmo com garbage collection, você pode manter dados vivos sem querer, impedindo a liberação de memória.

Exemplo com _closure_: Uma **closure** é um conceito da linguagem JavaScript onde **uma função lembra e tem acesso ao escopo em que foi criada**, **mesmo depois que esse escopo já terminou de executar**.

```js
function criaArrayGrande() {
  let grandeArray = new Array(1000000);
  
  return function () {
    console.log(grandeArray.length);
  };
}

let funcao = criaArrayGrande();
```

A função interna ainda **acessa o array**, então a memória **não será liberada**, mesmo que você não precise mais dele.

## Dicas para evitar problemas:

- Evite usar variáveis globais desnecessárias.
- Cuidado com **closures** que mantêm referências grandes.
- Limpe **event listeners** ou **timers** quando não forem mais necessários.
- Trabalhe com estruturas de dados simples sempre que possível.

## Conclusão

|O que acontece|Quem faz?|
|---|---|
|Alocação de memória|JavaScript (automático)|
|Liberação de memória|Garbage Collector|
|Seu papel como dev|Evitar _retenções_ desnecessárias|

Você não precisa se preocupar com detalhes técnicos de memória logo no início, mas entender **como funciona por trás dos panos** te ajuda a escrever código **mais leve e eficiente**.

# O que são closures?

Closures são funções que **“lembram” o ambiente (escopo léxico)** em que foram criadas — ou seja, elas **continuam acessando variáveis da função externa mesmo depois que essa função já terminou de executar**.

### Exemplo simples

```js
function outerFunction(x) {
    let y = 10;
    function innerFunction(){
        console.log(x + y);
    }
    return innerFunction;
}

let closure = outerFunction(5);
closure(); // Saída: 15
```

Mesmo depois que `outerFunction` terminou, a função interna `innerFunction` ainda acessa `x` e `y`. Isso é um closure.

### Como funciona?

Quando uma função é criada, ela carrega consigo **uma referência ao escopo onde foi declarada**, e não apenas às variáveis em si. Isso significa que ela **mantém acesso às variáveis externas**, mesmo que a função externa já tenha sido finalizada.

### Usos práticos de closures:

1. Criar variáveis “privadas”: Aqui, `count` só pode ser acessada pela função retornada. Isso simula uma variável privada.

```js
function createCounter() {
    let count = 0;
    return function () {
        count++;
        return count;
    };
}

let counter = createCounter();
counter(); // 1
counter(); // 2
```


2. Gerar funções personalizadas: A função retornada “lembra” do valor `x = 2`, e sempre multiplica qualquer `y` por 2.

```js
function multiply(x) {
    return function(y) {
        return x * y;
    };
}

let double = multiply(2);
console.log(double(5)) // 10
```

### Importante:

Closures **capturam variáveis por referência**, não por valor. Então se o valor muda, o closure vê esse novo valor:

```js
function createIncrementer() {
    let count = 0;
    return function () {
        count++;
        console.log(count);
    };
}

let increment = createIncrementer();
increment(); // 1
increment(); // 2
```

### Em resumo:

- Closure = função + escopo em que foi criada.
- Permite acessar variáveis externas mesmo após a função externa ter acabado.
- Usado para **encapsulamento**, **funções personalizadas**, e preservação de estado
- Essencial para entender programação funcional e padrões avançados em JavaScript.
