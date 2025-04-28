<!--
Meta Description: # BigInt64Array: Entendendo o Array de Inteiros de 64 Bits em JavaScript ## Sinopse O `BigInt64Array` é uma estrutura de dados em JavaScript que permi...
Meta Keywords: bigint64array, bigintarray, que, javascript, inteiros
-->

# BigInt64Array: Entendendo o Array de Inteiros de 64 Bits em JavaScript

## Sinopse
O `BigInt64Array` é uma estrutura de dados em JavaScript que permite armazenar e manipular arrays de números inteiros de 64 bits com sinal, oferecendo maior precisão para operações matemáticas que exigem grandes inteiros.

## Documentação
O `BigInt64Array` faz parte da especificação Typed Arrays do ECMAScript, permitindo que desenvolvedores trabalhem com arrays de inteiros de 64 bits. Essa estrutura é útil em aplicações que requerem o processamento de grandes números inteiros que não podem ser representados com precisão usando o tipo `Number` padrão do JavaScript.

### Propósito
O principal propósito do `BigInt64Array` é fornecer uma maneira eficiente de lidar com grandes inteiros, especialmente em aplicações que envolvem manipulação de dados binários, como gráficos, jogos, ou cálculos financeiros.

### Uso
Para criar um `BigInt64Array`, você pode passar um array de números, um array-like object, ou um buffer. Aqui estão algumas formas de instanciar um `BigInt64Array`:

```javascript
// Criando um BigInt64Array a partir de um array de números
const bigIntArray1 = new BigInt64Array([1n, 2n, 3n]);

// Criando um BigInt64Array a partir de um buffer
const buffer = new ArrayBuffer(8 * 3); // 3 elementos de 64 bits
const bigIntArray2 = new BigInt64Array(buffer);

// Criando um BigInt64Array a partir de um ArrayBuffer existente
const bigIntArray3 = new BigInt64Array(buffer, 0, 3);
```

## Exemplos
### Exemplo 1: Criando e acessando elementos
```javascript
const bigIntArray = new BigInt64Array(3);
bigIntArray[0] = 9007199254740991n; // Número máximo seguro em JavaScript
bigIntArray[1] = 1234567890123456789n;
bigIntArray[2] = -9876543210987654321n;

console.log(bigIntArray[0]); // 9007199254740991n
console.log(bigIntArray[1]); // 1234567890123456789n
console.log(bigIntArray[2]); // -9876543210987654321n
```

### Exemplo 2: Iterando sobre um BigInt64Array
```javascript
const bigIntArray = new BigInt64Array([1n, 2n, 3n]);

for (let i = 0; i < bigIntArray.length; i++) {
    console.log(bigIntArray[i]); // 1n, 2n, 3n
}
```

### Exemplo 3: Usando métodos de Typed Array
```javascript
const bigIntArray = new BigInt64Array([10n, 20n, 30n]);
const newArray = bigIntArray.map(x => x * 2n);

console.log(newArray); // BigInt64Array(3) [20n, 40n, 60n]
```

## Explicação
### Armadilhas Comuns e Dicas
1. **Uso de Tipos**: Lembre-se de que os elementos do `BigInt64Array` devem ser do tipo `BigInt`. Usar números normais resultará em um erro.
2. **Limitação de Tamanho**: O `BigInt64Array` pode conter até 2^31-1 elementos, o que pode não ser suficiente para algumas aplicações que requerem arrays muito grandes.
3. **Compatibilidade**: Verifique a compatibilidade do ambiente com `BigInt64Array`, pois não está disponível em versões mais antigas de navegadores.

## Resumo em Uma Linha
O `BigInt64Array` em JavaScript é uma estrutura que permite a manipulação eficiente de arrays de inteiros de 64 bits, oferecendo precisão para grandes números inteiros.