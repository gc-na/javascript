<!--
Meta Description: # Int8Array: Entendendo o Tipo de Dado em JavaScript ## Sinopse O `Int8Array` é uma estrutura de dados em JavaScript que representa um array de inteir...
Meta Keywords: int8array, javascript, const, array, new
-->

# Int8Array: Entendendo o Tipo de Dado em JavaScript

## Sinopse
O `Int8Array` é uma estrutura de dados em JavaScript que representa um array de inteiros de 8 bits com sinal, permitindo manipulação eficiente de dados binários.

## Documentação
O `Int8Array` faz parte do conjunto de Typed Arrays do JavaScript, que oferece uma forma de trabalhar com dados binários de maneira mais eficiente do que os arrays normais. O `Int8Array` especificamente armazena inteiros de 8 bits, variando de -128 a 127. Isso é útil em diversas aplicações, como manipulação de imagens, áudio, e comunicação de rede.

### Propósito
O `Int8Array` é utilizado quando é necessário lidar com dados binários de forma mais controlada e eficiente, especialmente em contextos onde a performance é crucial.

### Uso
Para criar um `Int8Array`, você pode utilizar diversas formas:

1. **Criando um array vazio**:
   ```javascript
   const arr = new Int8Array(10); // Cria um Int8Array com 10 elementos inicializados como 0
   ```

2. **Criando a partir de um array existente**:
   ```javascript
   const arr = new Int8Array([1, 2, -3, 4]); // Cria um Int8Array a partir de um array de números
   ```

3. **Criando a partir de um ArrayBuffer**:
   ```javascript
   const buffer = new ArrayBuffer(16); // Cria um buffer de 16 bytes
   const arr = new Int8Array(buffer); // Cria um Int8Array que usa o ArrayBuffer
   ```

### Métodos e Propriedades
`Int8Array` herda métodos de `TypedArray`, incluindo:
- `.set()`: Para definir valores a partir de outro array.
- `.subarray()`: Para criar uma visão de uma parte do array.
- `.slice()`: Para extrair uma seção do array.

## Exemplos
### Criando e Acessando Elementos
```javascript
const intArray = new Int8Array(5);
intArray[0] = -128;
intArray[1] = 0;
intArray[2] = 127;
console.log(intArray); // Int8Array(5) [-128, 0, 127, 0, 0]
```

### Usando o método `set()`
```javascript
const arr1 = new Int8Array([1, 2, 3]);
const arr2 = new Int8Array(3);
arr2.set(arr1);
console.log(arr2); // Int8Array(3) [1, 2, 3]
```

### Usando o método `subarray()`
```javascript
const arr = new Int8Array([10, 20, 30, 40]);
const subArr = arr.subarray(1, 3);
console.log(subArr); // Int8Array(2) [20, 30]
```

## Explicação
Um erro comum ao usar `Int8Array` é tentar armazenar valores fora do intervalo permitido (-128 a 127). Tentar fazer isso resultará em truncamento, onde valores fora desse intervalo serão convertidos. Por exemplo, armazenar 128 se tornará -128.

Além disso, como os `Typed Arrays` não são arrays normais, eles não têm todos os métodos de um array padrão, como `push()` ou `pop()`. Portanto, é importante compreender as limitações e as operações disponíveis.

## Resumo em Uma Linha
O `Int8Array` é uma estrutura de dados em JavaScript que permite a manipulação eficiente de arrays de inteiros de 8 bits com sinal, ideal para aplicações que requerem controle sobre dados binários.