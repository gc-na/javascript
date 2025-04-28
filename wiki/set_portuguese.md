<!--
Meta Description: # Set em JavaScript: Um Guia Completo ## Sinopse O objeto `Set` em JavaScript é uma coleção de valores únicos, permitindo que você armazene dados sem ...
Meta Keywords: set, que, javascript, elementos, dados
-->

# Set em JavaScript: Um Guia Completo

## Sinopse
O objeto `Set` em JavaScript é uma coleção de valores únicos, permitindo que você armazene dados sem duplicatas. É ideal para manipulação de conjuntos de dados e operações em que a unicidade dos elementos é necessária.

## Documentação
O `Set` é uma estrutura de dados introduzida no ECMAScript 2015 (ES6) que permite armazenar valores únicos de qualquer tipo, seja primitivo ou objeto. Um `Set` mantém a ordem de inserção dos elementos, o que significa que você pode iterar sobre seus elementos na ordem em que foram adicionados.

### Propósito
O principal objetivo do `Set` é garantir a unicidade dos valores, o que é particularmente útil em situações como filtragem de dados, verificação de duplicatas e operações de conjunto.

### Uso
Para criar um `Set`, você pode usar a seguinte sintaxe:

```javascript
const meuSet = new Set(iterable);
```

- `iterable`: (opcional) Um objeto iterável, como um array, que pode ser usado para inicializar o `Set`.

### Métodos Principais
- `add(value)`: Adiciona um novo elemento ao `Set`.
- `delete(value)`: Remove um elemento específico do `Set`.
- `has(value)`: Verifica se um valor está presente no `Set`.
- `clear()`: Remove todos os elementos do `Set`.
- `size`: Propriedade que retorna o número de elementos no `Set`.

## Exemplos

### Criando um Set
```javascript
const numeros = new Set([1, 2, 3, 4, 4, 5]); // O valor 4 é duplicado
console.log(numeros); // Set { 1, 2, 3, 4, 5 }
```

### Adicionando e Removendo Elementos
```javascript
const frutas = new Set();
frutas.add('maçã');
frutas.add('banana');
frutas.add('laranja');
console.log(frutas.size); // 3

frutas.delete('banana');
console.log(frutas.has('banana')); // false
```

### Iterando Sobre um Set
```javascript
const letras = new Set(['a', 'b', 'c']);
letras.forEach(letra => {
    console.log(letra);
});
// Saída: a, b, c
```

## Explicação
Embora o `Set` seja uma ferramenta poderosa, existem algumas armadilhas comuns a serem observadas:

1. **Tipos de Dados**: O `Set` considera valores primitivos e objetos diferentes. Por exemplo, dois objetos diferentes, mesmo com o mesmo conteúdo, são tratados como elementos distintos.

   ```javascript
   const obj1 = { nome: 'João' };
   const obj2 = { nome: 'João' };
   const conjunto = new Set();
   conjunto.add(obj1);
   conjunto.add(obj2);
   console.log(conjunto.size); // 2
   ```

2. **Comparação de Objetos**: A comparação de igualdade para objetos é feita por referência, não por valor. Portanto, dois objetos com o mesmo conteúdo não são considerados iguais.

3. **Imutabilidade**: Após a criação, os elementos de um `Set` não podem ser alterados diretamente. Você precisa removê-los e adicioná-los novamente se precisar alterar um valor.

## Resumo em Uma Linha
`Set` é uma estrutura de dados em JavaScript que permite armazenar valores únicos, facilitando a manipulação de conjuntos de dados sem duplicatas.