<!--
Meta Description: # Números em JavaScript: Entendendo o Tipo Numérico ## Sinopse Neste artigo, exploramos o tipo Numérico em JavaScript, uma das principais categorias d...
Meta Keywords: números, javascript, number, que, para
-->

# Números em JavaScript: Entendendo o Tipo Numérico

## Sinopse
Neste artigo, exploramos o tipo Numérico em JavaScript, uma das principais categorias de dados na linguagem. Aprenda sobre suas características, como utilizá-lo corretamente e evite armadilhas comuns.

## Documentação
### O que é o tipo Numérico?
Em JavaScript, o tipo Numérico é utilizado para representar valores numéricos, tanto inteiros quanto de ponto flutuante. JavaScript utiliza o padrão IEEE 754 para a representação de números, o que significa que todos os números são armazenados como números de ponto flutuante de 64 bits.

### Propósito
O tipo Numérico é fundamental para qualquer operação matemática em JavaScript, permitindo realizar cálculos, manipulações e comparações entre valores numéricos.

### Uso
Os números em JavaScript podem ser usados em expressões matemáticas, como adição, subtração, multiplicação e divisão. Além disso, JavaScript fornece uma série de métodos associados ao objeto `Number` para manipulação e formatação de números.

### Detalhes
- **Representação**: Todos os números em JavaScript são do tipo `number`, não importa se são inteiros ou decimais.
- **Limites**: O maior número que pode ser representado em JavaScript é `Number.MAX_SAFE_INTEGER` (2^53 - 1), e o menor é `Number.MIN_SAFE_INTEGER` (-2^53 + 1).
- **NaN**: O valor "Not a Number" (NaN) é retornado quando uma operação matemática falha.
- **Infinity**: O valor infinito é representado por `Infinity`, que ocorre em operações como divisão por zero.

## Exemplos

### Exemplo 1: Operações Básicas
```javascript
let a = 10;
let b = 5;

let soma = a + b; // 15
let subtracao = a - b; // 5
let multiplicacao = a * b; // 50
let divisao = a / b; // 2
```

### Exemplo 2: Usando o objeto Number
```javascript
let numero = 123.456;
console.log(Number.isInteger(numero)); // false
console.log(Number.parseFloat("123.45")); // 123.45
console.log(Number.MAX_VALUE); // 1.7976931348623157e+308
```

## Explicação
### Armadilhas Comuns
1. **Comparação de Números**: Ao comparar números, é importante lembrar que a precisão de números de ponto flutuante pode levar a resultados inesperados. Por exemplo, `0.1 + 0.2 !== 0.3`.
   
2. **NaN**: Qualquer operação que envolva `NaN` resultará em `NaN`. Para verificar se um valor é `NaN`, utilize `Number.isNaN()`, pois `NaN` não é igual a ele mesmo.

3. **Conversão de Tipos**: Ao realizar operações com strings que contêm números, JavaScript tenta converter essas strings em números. Isso pode resultar em `NaN` se a conversão não for possível.

4. **Arredondamento**: Os números de ponto flutuante podem causar problemas de arredondamento. Para evitar isso, considere usar métodos como `Number.toFixed()` para controlar a precisão decimal.

## Resumo em Uma Linha
O tipo Numérico em JavaScript é fundamental para operações matemáticas, representando tanto inteiros quanto números de ponto flutuante, com características específicas que devem ser compreendidas para evitar erros comuns.