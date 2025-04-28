<!--
Meta Description: # HTMLTableRowElement em JavaScript: Entenda e Utilize ## Sinopse O `HTMLTableRowElement` é uma interface do DOM que representa uma linha em uma tabel...
Meta Keywords: linha, tabela, uma, nova, javascript
-->

# HTMLTableRowElement em JavaScript: Entenda e Utilize

## Sinopse
O `HTMLTableRowElement` é uma interface do DOM que representa uma linha em uma tabela HTML, permitindo a manipulação de elementos `<tr>` com JavaScript.

## Documentação
O `HTMLTableRowElement` é parte da API do Document Object Model (DOM) e fornece propriedades e métodos para interagir com as linhas de uma tabela. Ele é frequentemente utilizado em conjunto com outros elementos de tabela, como `HTMLTableCellElement` (para células) e `HTMLTableElement` (para a tabela em si).

### Propósito
O `HTMLTableRowElement` permite aos desenvolvedores acessar, modificar e gerenciar linhas de tabelas de forma programática, facilitando a criação de interfaces dinâmicas e interativas.

### Uso
Para acessar ou criar uma nova linha de tabela, você pode usar métodos como `insertRow()` para adicionar uma nova linha e `deleteRow()` para remover uma linha existente. As propriedades mais comuns incluem `cells`, que retorna uma coleção de células (`<td>` ou `<th>`) na linha.

### Detalhes
- **Propriedades principais:**
  - `cells`: Retorna uma coleção de todas as células da linha.
  - `rowIndex`: O índice da linha dentro da tabela.
  
- **Métodos principais:**
  - `insertCell(index)`: Adiciona uma nova célula à linha no índice especificado.
  - `deleteCell(index)`: Remove a célula no índice especificado.

## Exemplos

### Exemplo 1: Acessando uma linha da tabela
```javascript
const tabela = document.getElementById("minhaTabela");
const linha = tabela.rows[0]; // Acessa a primeira linha da tabela
console.log(linha.cells); // Exibe as células da linha
```

### Exemplo 2: Adicionando uma nova linha
```javascript
const tabela = document.getElementById("minhaTabela");
const novaLinha = tabela.insertRow(); // Insere uma nova linha no final da tabela
const novaCelula = novaLinha.insertCell(0); // Adiciona uma célula na nova linha
novaCelula.innerText = "Nova Célula"; // Define o texto da nova célula
```

### Exemplo 3: Removendo uma linha
```javascript
const tabela = document.getElementById("minhaTabela");
tabela.deleteRow(0); // Remove a primeira linha da tabela
```

## Explicação
Um erro comum ao trabalhar com `HTMLTableRowElement` é tentar acessar propriedades ou métodos antes que a tabela esteja completamente carregada no DOM. Sempre certifique-se de que o script JavaScript é executado após os elementos da tabela estarem disponíveis. Além disso, ao usar `insertRow()` ou `insertCell()`, você deve estar ciente do índice que está passando, para evitar erros de índice fora do intervalo.

## Resumo em Uma Frase
O `HTMLTableRowElement` é uma interface do DOM que facilita a manipulação programática de linhas de tabelas HTML em JavaScript.