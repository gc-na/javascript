<!--
Meta Description: # BigUint64Array: Manipulando Números Inteiros de 64 Bits em JavaScript ## Sinopse O `BigUint64Array` é um tipo de array em JavaScript que permite arm...
Meta Keywords: biguint64array, javascript, números, inteiros, array
-->

# BigUint64Array: Manipulando Números Inteiros de 64 Bits em JavaScript

## Sinopse
O `BigUint64Array` é um tipo de array em JavaScript que permite armazenar e manipular números inteiros não negativos de 64 bits. Ele é especialmente útil para aplicações que requerem alta precisão em cálculos numéricos.

## Documentação
O `BigUint64Array` é uma estrutura de dados que faz parte da especificação Typed Arrays do JavaScript. Este tipo de array é projetado para armazenar inteiros de 64 bits, sendo ideal para operações que exigem manipulação de grandes números, como em aplicações financeiras, jogos e criptografia.

### Propósito
O principal propósito do `BigUint64Array` é fornecer uma maneira eficiente de trabalhar com números inteiros grandes, garantindo que você não perca precisão durante operações matemáticas.

### Uso
Para usar o `BigUint64Array`, você pode criar uma instância passando o tamanho desejado ou um array existente. Aqui estão algumas maneiras de criar um `BigUint64Array`:

```javascript
// Criando um BigUint64Array com um tamanho específico
const array1 = new BigUint64Array(5);

// Criando um BigUint64Array a partir de um array existente
const array2 = new BigUint64Array([1n, 2n, 3n, 4n, 5n]);
```

### Métodos
O `BigUint64Array` oferece vários métodos úteis, como:

- `.set()`: Define valores em posições específicas do array.
- `.subarray()`: Cria uma nova visão do array em um intervalo específico.

## Exemplos
Aqui estão alguns exemplos ilustrativos de como usar o `BigUint64Array`:

### Exemplo 1: Criando e Populando um BigUint64Array
```javascript
const bigArray = new BigUint64Array(3);
bigArray[0] = 12345678901234567890n;
bigArray[1] = 98765432109876543210n;
bigArray[2] = 11223344556677889900n;

console.log(bigArray); // Output: BigUint64Array(3) [ 12345678901234567890n, 98765432109876543210n, 11223344556677889900n ]
```

### Exemplo 2: Usando o Método set
```javascript
const sourceArray = new BigUint64Array([10n, 20n, 30n]);
const targetArray = new BigUint64Array(3);
targetArray.set(sourceArray);

console.log(targetArray); // Output: BigUint64Array(3) [ 10n, 20n, 30n ]
```

### Exemplo 3: Criando um Subarray
```javascript
const bigArray = new BigUint64Array([100n, 200n, 300n, 400n]);
const subArray = bigArray.subarray(1, 3);

console.log(subArray); // Output: BigUint64Array(2) [ 200n, 300n ]
```

## Explicação
Embora o `BigUint64Array` seja uma ferramenta poderosa, existem algumas considerações a serem feitas:

- **Limitações de Precisão**: Lembre-se de que esse tipo de array é usado apenas para inteiros não negativos. Tentar armazenar números negativos ou valores não inteiros resultará em erros.
- **Performance**: Operações com `BigUint64Array` são geralmente mais rápidas do que trabalhar com arrays normais contendo números, especialmente quando se trata de manipulação de grandes conjuntos de dados.

## Resumo em uma Linha
O `BigUint64Array` em JavaScript permite armazenar e manipular números inteiros não negativos de 64 bits de forma eficiente e precisa.