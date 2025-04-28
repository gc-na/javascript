<!--
Meta Description: # parseInt: Comando Esencial em JavaScript para Conversão de Strings em Números Inteiros ## Sinopse O `parseInt` é uma função embutida em JavaScript q...
Meta Keywords: parseint, javascript, string, para, não
-->

# parseInt: Comando Esencial em JavaScript para Conversão de Strings em Números Inteiros

## Sinopse
O `parseInt` é uma função embutida em JavaScript que converte uma string em um número inteiro, permitindo especificar a base numérica (radix) da conversão. É amplamente utilizado para manipulação de dados e entradas de usuários.

## Documentação
### Propósito
A função `parseInt` tem como objetivo transformar uma string que representa um número em um inteiro. Esta função é especialmente útil quando se lida com dados recebidos de formulários ou outras fontes onde os números são apresentados como texto.

### Uso
A sintaxe da função é a seguinte:

```javascript
parseInt(string, radix);
```

- **string**: A string que será convertida para um número inteiro.
- **radix**: Um número inteiro que representa a base para a conversão. Pode variar de 2 (binário) até 36. Se o radix não for fornecido, o JavaScript tentará determinar a base automaticamente; no entanto, é recomendado sempre especificá-lo para evitar resultados inesperados.

### Detalhes
- Se a string não iniciar com um valor numérico, `parseInt` retorna `NaN` (Not-a-Number).
- O `parseInt` ignora espaços em branco no início da string.
- Caracteres não numéricos após um número válido resultarão na conversão até o ponto onde o número válido termina.
- Se o primeiro caractere da string não for um dígito ou um sinal (+/-), `parseInt` retornará `NaN`.

## Exemplos
### Exemplo 1: Conversão básica
```javascript
console.log(parseInt("123")); // Saída: 123
```

### Exemplo 2: Conversão com radix
```javascript
console.log(parseInt("1010", 2)); // Saída: 10 (binário para decimal)
```

### Exemplo 3: Ignorando espaços em branco
```javascript
console.log(parseInt("   42   ")); // Saída: 42
```

### Exemplo 4: Caracteres não numéricos
```javascript
console.log(parseInt("123abc")); // Saída: 123
```

### Exemplo 5: Retornando NaN
```javascript
console.log(parseInt("abc123")); // Saída: NaN
```

## Explicação
Uma armadilha comum ao usar `parseInt` é não especificar o radix. Isso pode levar a resultados inesperados, especialmente quando a string começa com '0', que pode ser interpretada como octal em algumas circunstâncias. Para evitar confusões, é sempre recomendável definir o radix explicitamente.

Além disso, ao trabalhar com entradas de usuários, é importante validar se o resultado não é `NaN` antes de realizar operações com o valor retornado. Isso garante que seu código não falhe devido a entradas inválidas.

## Resumo em Uma Linha
O `parseInt` é uma função do JavaScript que converte strings em números inteiros, permitindo especificar a base da conversão para maior precisão e controle.