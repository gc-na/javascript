<!--
Meta Description: # Infinity em JavaScript: Entendendo o Valor Especial ## Sinopse O `Infinity` em JavaScript é um valor numérico que representa a infinidade ou um núme...
Meta Keywords: infinity, que, número, console, log
-->

# Infinity em JavaScript: Entendendo o Valor Especial

## Sinopse
O `Infinity` em JavaScript é um valor numérico que representa a infinidade ou um número maior do que qualquer outro número finito.

## Documentação
O `Infinity` é uma propriedade global em JavaScript que é usada para indicar um número que é maior do que a maior representação numérica possível. Ele é frequentemente utilizado em operações matemáticas e comparações.

### Propósito
O valor `Infinity` é útil para lidar com cálculos que podem resultar em valores que excedem os limites numéricos normais, como em divisões por zero.

### Uso
Para acessar o valor de `Infinity`, você pode usar diretamente a palavra-chave `Infinity` no código. O JavaScript também permite que você crie `Infinity` através de expressões matemáticas, como `1 / 0`.

### Detalhes
- `Infinity` é um número do tipo `number`.
- `-Infinity` representa a menor infinidade, ou seja, valores que são infinitamente negativos.
- Comparações com `Infinity` seguem a lógica matemática, onde qualquer número finito é menor que `Infinity`.
- É importante notar que `Infinity` não é um número finito, e não deve ser tratado como tal.

## Exemplos
```javascript
console.log(Infinity); // Saída: Infinity
console.log(-Infinity); // Saída: -Infinity

// Exemplo de divisão por zero
console.log(1 / 0); // Saída: Infinity
console.log(-1 / 0); // Saída: -Infinity

// Comparações
console.log(1000 < Infinity); // Saída: true
console.log(Infinity === Infinity); // Saída: true
console.log(Infinity > 1000000); // Saída: true
```

## Explicação
Um dos erros comuns ao trabalhar com `Infinity` é assumir que ele é um número finito. Por exemplo, qualquer operação que envolva `Infinity` e um número finito ainda resultará em `Infinity`. Além disso, `Infinity` não deve ser confundido com `NaN` (Not a Number), que representa um valor indefinido ou não representável.

Outro ponto a ser considerado é que, ao realizar operações matemáticas envolvendo `Infinity`, o resultado pode não ser intuitivo. Por exemplo, a expressão `Infinity - Infinity` resulta em `NaN`, pois não se pode determinar o que acontece quando se subtrai uma infinidade de outra.

## Resumo em Uma Linha
`Infinity` é um valor especial em JavaScript que representa a infinidade e é utilizado frequentemente em operações matemáticas e comparações.