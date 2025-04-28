<!--
Meta Description: # NaN em JavaScript: O Que É e Como Utilizá-lo ## Sinopse NaN (Not-a-Number) é um valor especial em JavaScript que indica que um valor não é um número...
Meta Keywords: nan, valor, que, não, isnan
-->

# NaN em JavaScript: O Que É e Como Utilizá-lo

## Sinopse
NaN (Not-a-Number) é um valor especial em JavaScript que indica que um valor não é um número válido. Ele é frequentemente encontrado em operações matemáticas que resultam em valores indefinidos ou impossíveis.

## Documentação
NaN é uma propriedade global que representa um valor numérico que não é um número. No JavaScript, NaN é do tipo `number` e é tipicamente gerado em operações aritméticas que não têm um resultado numérico válido. Abaixo estão algumas características e comportamentos associados ao NaN:

- **Tipo**: `typeof NaN` retorna `"number"`.
- **Comparação**: NaN é único, o que significa que não é igual a si mesmo. A expressão `NaN === NaN` retorna `false`.
- **Identificação**: Para verificar se um valor é NaN, deve-se usar a função `isNaN()` ou `Number.isNaN()`. A função `isNaN()` tenta converter o valor para um número antes de verificar, enquanto `Number.isNaN()` não faz essa conversão.

### Uso
NaN é usado principalmente em situações onde uma operação não produz um resultado numérico. Exemplos incluem a divisão de zero por zero, a conversão de uma string não numérica para número, entre outros.

## Exemplos
Aqui estão alguns exemplos de como o NaN pode ser gerado em JavaScript:

```javascript
// Exemplo 1: Divisão por zero
let resultado = 0 / 0; // resultado é NaN
console.log(resultado); // NaN

// Exemplo 2: Conversão de string não numérica
let valor = Number("texto"); // valor é NaN
console.log(valor); // NaN

// Exemplo 3: Operação inválida
let soma = 5 * "abc"; // soma é NaN
console.log(soma); // NaN

// Usando isNaN
console.log(isNaN(resultado)); // true
console.log(Number.isNaN(valor)); // true
```

## Explicação
Embora NaN seja uma parte fundamental de JavaScript, existem algumas armadilhas que os desenvolvedores devem estar cientes:

- **Comparações**: Devido ao comportamento exclusivo de NaN, é importante usar `isNaN()` ou `Number.isNaN()` para verificar se um valor é NaN. Comparações diretas não funcionarão.
  
- **Type Coercion**: A função `isNaN()` pode causar confusão, pois ela tenta converter o valor para um número antes de verificar. Por exemplo, `isNaN("texto")` retornará `true` porque `"texto"` não pode ser convertido em um número.

- **NaN e Arrays**: Se você tentar adicionar NaN a um array, ele será tratado como um valor, mas isso pode levar a resultados inesperados em operações subsequentes.

## Resumo em Uma Linha
NaN é um valor especial em JavaScript que indica que um resultado não é um número válido e deve ser tratado com cuidado em comparações e operações.