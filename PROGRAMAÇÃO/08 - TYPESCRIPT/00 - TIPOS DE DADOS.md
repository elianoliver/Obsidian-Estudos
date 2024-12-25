No universo do desenvolvimento web, compreender os tipos de dados em TypeScript é fundamental para garantir a integridade e eficiência do código.

TypeScript, sendo um superset do JavaScript, introduz a tipagem estática, permitindo uma abordagem mais robusta na definição de tipos de variáveis. Neste contexto, exploraremos diversos exemplos práticos, analisando diferentes tipos de dados, como strings, números e arrays, além de entender as peculiaridades relacionadas a objetos do DOM. 

Através de exemplos concretos, veremos como operações comuns podem resultar em comportamentos inesperados e como o conhecimento sólido dos tipos em TypeScript pode prevenir erros e otimizar o desenvolvimento de aplicações web.

```js
const frase = 'Front End';
```
   - Tipo: string
   - Exemplo: `'Front End'`
   - Resultado de `frase.toLowerCase();`: `'front end'`
   - Resultado de `frase.toFixed();`: (Erro - `toFixed()` não é uma função de strings em TypeScript).

```js
const total = 100.05;
```
   - Tipo: number
   - Exemplo: `100.05`
   - Resultado de `total.toFixed();`: `'100'`
   - Resultado de 
     `total.toLowerCase();`
     (Erro - `toLowerCase()` não é uma função de números em TypeScript).

```js
const empresas = ['Apple', 'Microsoft'];
```
   - Tipo: string[]
   - Exemplo: `['Apple', 'Microsoft']`
   - Resultado de 
     `empresas.map((empresa) => empresa.toUpperCase());`
      `['APPLE', 'MICROSOFT']`
   - Resultado de 
     `empresas.toLowerCase();`
     (Erro - `toLowerCase()` não é uma função de arrays em TypeScript).

```js
const body = document.body;
```
   - Tipo: HTMLElement | null
   - Exemplo: (Depende do conteúdo do documento)
   - Resultado de 
     `body.style.background = '#000';`
     O plano de fundo do corpo do documento será definido como preto.
   - Resultado de
      `body.map((item) => item);`
      (Erro - `map()` não é uma função de HTMLElement em TypeScript).

```js
const button = document.querySelector('button');
```
   - Tipo: HTMLButtonElement | null
   - Exemplo: (Depende da existência do botão no documento)
   - Resultado de `console.log(button);`: O botão encontrado ou `null` se não existir.
   - Resultado de `button.click();`: Clicará no botão, se existir.

```js
const operacao = true + 'teste' - (4 * {}) / [];
```
   - Tipo: number (devido à operação matemática)
   - Resultado de `console.log(operacao);`: `NaN` (Not a Number), pois a operação não faz sentido.

```js
const strings = 'Front ' + 'End';
```
   - Tipo: string
   - Resultado de `console.log(strings);`: `'Front End'`

```js
const numbers = 100 + 200;
```
   - Tipo: number
   - Resultado de `console.log(numbers);`: `300`

Esses exemplos destacam a importância de entender os tipos de dados em TypeScript para evitar erros durante o desenvolvimento.

## Dica - @ts-check
O recurso `@ts-check` representa uma ferramenta valiosa nesse contexto. Ao adicionar o comentário `//@ts-check` no início de um arquivo JavaScript, o VS Code utiliza a verificação de tipo do TypeScript para identificar potenciais erros de maneira proativa. Isso significa que o editor fornece sugestões de métodos e propriedades mais precisas, destacando possíveis problemas que seriam capturados durante a compilação com TypeScript. Essa abordagem integrada simplifica o processo de desenvolvimento, permitindo aos programadores identificar e corrigir falhas de forma antecipada, promovendo assim um código mais robusto e livre de erros.

