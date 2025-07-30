- [ ] ## O que é gerenciamento de memória?

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

É como se a função **“guardasse uma mochila” com as variáveis** do ambiente onde ela foi criada — e pudesse usar essas variáveis mesmo mais tarde.

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