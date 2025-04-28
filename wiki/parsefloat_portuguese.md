<!--
Meta Description: # parseFloat: Entendendo a Função para Conversão de Strings em Números em JavaScript ## Sinopse O `parseFloat` é uma função embutida em JavaScript que...
Meta Keywords: parsefloat, string, número, que, não
-->

# parseFloat: Entendendo a Função para Conversão de Strings em Números em JavaScript

## Sinopse
O `parseFloat` é uma função embutida em JavaScript que converte uma string em um número de ponto flutuante. É amplamente utilizada para garantir que os valores numéricos sejam interpretados corretamente em operações matemáticas.

## Documentação
### Propósito
A função `parseFloat` é utilizada para analisar uma string e retornar um número decimal. Isso é especialmente útil quando se lida com dados que vêm como texto, como entradas de usuários ou dados de APIs.

### Uso
A sintaxe básica do `parseFloat` é:

```javascript
parseFloat(string)
```

#### Parâmetros
- **string**: A string que será analisada. Se o valor não puder ser convertido em um número, o retorno será `NaN` (Not-a-Number).

#### Retorno
- Um número de ponto flutuante correspondente ao valor contido na string. Se a string não iniciar com um número válido, o retorno será `NaN`.

### Detalhes
- `parseFloat` ignora espaços em branco no início da string.
- A função para a conversão assim que encontra um caractere que não pode ser parte de um número (por exemplo, letras ou símbolos não numéricos).
- Caso a string seja vazia ou não contenha números válidos, `NaN` será retornado.

## Exemplos
Aqui estão alguns exemplos básicos de como usar `parseFloat`:

```javascript
console.log(parseFloat("3.14")); // Saída: 3.14
console.log(parseFloat("   42.5abc")); // Saída: 42.5
console.log(parseFloat("abc42.5")); // Saída: NaN
console.log(parseFloat("100")); // Saída: 100
console.log(parseFloat("0.1e2")); // Saída: 10
```

## Explicação
### Armadilhas Comuns
1. **Espaços em Branco**: `parseFloat` ignora espaços em branco antes do número, mas isso pode causar confusão se não for esperado.
2. **Retorno de NaN**: Se a string não contiver um número válido no início, o retorno será `NaN`, o que pode levar a erros se não for tratado corretamente. Para verificar se o resultado é `NaN`, use a função `isNaN()`.

### Notas Adicionais
- `parseFloat` só analisa o primeiro número que pode ser encontrado na string. Se houver caracteres após o número, estes serão ignorados.
- A função não considera a notação em octal ou hexadecimal, apenas números decimais.

## Resumo em Uma Linha
`parseFloat` é uma função JavaScript que converte uma string em um número de ponto flutuante, sendo essencial para manipulação correta de dados numéricos.