## Tabela de Estrutura Mínima

```html
<table border="1">
    <tr>
        <th>Coluna 1</th>
        <th>Coluna 2</th>
        <th>Coluna 3</th>
    </tr>
    <tr>
        <td>Linha 1, Coluna 1</td>
        <td>Linha 1, Coluna 2</td>
        <td>Linha 1, Coluna 3</td>
    </tr>
    <!-- ... outras linhas ... -->
</table>
```

Neste exemplo, estamos criando uma tabela simples. A primeira linha (linha de cabeçalho) contém três células de cabeçalho (`<th>`) representando as colunas. As linhas seguintes (linhas de dados) contêm as células de dados (`<td>`) correspondentes às colunas. É uma estrutura básica de tabela.

## Tabela Completa com Formatação

```html
<table border="1" cellpadding="10" width="100%" align="center">
    <thead>
        <tr>
            <th>Qtd</th>
            <th>Descrição</th>
            <th>Valor</th>
        </tr>
    </thead>
    <tbody>
        <tr align="center">
            <td>1</td>
            <td>Lápis</td>
            <td>1,00</td>
        </tr>
        <!-- ... outras linhas ... -->
    </tbody>
    <tfoot>
        <tr>
            <td colspan="2"><b>Total</b></td>
            <td>19,00</td>
        </tr>
    </tfoot>
</table>
```

Aqui, criamos uma tabela mais elaborada. A seção `<thead>` contém os cabeçalhos das colunas, a seção `<tbody>` contém as linhas de dados e a seção `<tfoot>` contém informações adicionais no rodapé. Estamos usando `align`, `bgcolor` e `colspan` para alinhar o conteúdo, definir cores de fundo e mesclar células.

## Mesclando Linhas e Colunas

```html
<table border="1" cellspacing="0">
    <tr>
        <th>coluna 1</th>
        <th>coluna 2</th>
        <th>coluna 3</th>
    </tr>
    <tr>
        <td rowspan="2">linha 1, coluna 1</td>
        <td>linha 1, coluna 2</td>
        <td>linha 1, coluna 3</td>
    </tr>
    <tr>
        <td>linha 2, coluna 1</td>
        <td>linha 2, coluna 2</td>
    </tr>
    <!-- ... outras linhas ... -->
</table>
```

Neste exemplo, estamos explorando a mesclagem de células. Usamos `rowspan` para mesclar duas células verticalmente na primeira coluna. Também usamos `colspan` para mesclar duas células horizontalmente na última linha da tabela. Isso cria uma estrutura mais complexa e organizada.
