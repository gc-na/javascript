<!--
Meta Description: # BigInt em JavaScript: Números Inteiros de Precisão Arbitrária ## Sinopse BigInt é um tipo de dado em JavaScript que permite trabalhar com números in...
Meta Keywords: bigint, const, que, javascript, tipo
-->

# BigInt em JavaScript: Números Inteiros de Precisão Arbitrária

## Sinopse
BigInt é um tipo de dado em JavaScript que permite trabalhar com números inteiros de precisão arbitrária, superando os limites do tipo Number tradicional, que é baseado em ponto flutuante.

## Documentação
O BigInt é uma adição ao JavaScript que permite representar números inteiros que são maiores que o limite do tipo Number, que é 2^53 - 1 (ou seja, 9007199254740991). O BigInt é especialmente útil em aplicações que requerem cálculos de alta precisão, como criptografia, manipulação de grandes quantidades de dados, ou quando se trabalha com números que excedem os limites de precisão do JavaScript padrão.

### Criação de BigInt
Você pode criar um BigInt de duas maneiras:

1. **Usando a função `BigInt()`**:
   ```javascript
   const bigInt1 = BigInt(123456789012345678901234567890);
   ```

2. **Usando a notação de sufisso `n`**:
   ```javascript
   const bigInt2 = 123456789012345678901234567890n;
   ```

### Operações com BigInt
BigInt suporta operações aritméticas básicas como adição (+), subtração (-), multiplicação (*), e divisão (/). No entanto, a divisão de BigInt resulta em um resultado arredondado para baixo.

```javascript
const a = 12345678901234567890n;
const b = 98765432109876543210n;
const sum = a + b; // 111111111111111111100n
const quotient = b / 10n; // 9876543210987654321n
```

### Comparações
BigInt pode ser comparado a outros BigInts ou a valores do tipo Number, mas é importante lembrar que a comparação entre esses dois tipos pode não se comportar como esperado.

## Exemplos
```javascript
// Criando BigInts
const bigIntA = BigInt(10);
const bigIntB = 20n;

// Operações
const sum = bigIntA + bigIntB; // 30n
const product = bigIntA * bigIntB; // 200n

console.log(sum);      // Saída: 30n
console.log(product);  // Saída: 200n

// Comparação
console.log(bigIntA === 10); // Saída: false (diferentes tipos)
console.log(bigIntA == 10);  // Saída: true  (comparação coerente)
```

## Explicação
Um dos principais desafios ao utilizar BigInt é que ele não pode ser misturado diretamente com o tipo Number em operações matemáticas. Tentativas de realizar operações entre BigInt e Number resultarão em um erro. Por exemplo:

```javascript
const bigIntValue = 10n;
const numberValue = 10;

console.log(bigIntValue + numberValue); // Lança um TypeError
```

Além disso, a divisão de BigInt sempre resulta em um valor inteiro, descartando a parte decimal. Por exemplo:

```javascript
const bigIntDiv = 15n / 4n; // Resultado: 3n
```

## Resumo em Uma Linha
BigInt é um tipo de dado em JavaScript que permite o trabalho com números inteiros de precisão arbitrária, ideal para cálculos que excedem o limite do tipo Number.