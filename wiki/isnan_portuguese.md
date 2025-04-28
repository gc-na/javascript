<!--
Meta Description: # Entendendo o isNaN no JavaScript: Verificação de Números ## Sinopse O `isNaN` é uma função em JavaScript que verifica se um valor é `NaN` (Not-a-Num...
Meta Keywords: isnan, valor, que, não, número
-->

# Entendendo o isNaN no JavaScript: Verificação de Números

## Sinopse
O `isNaN` é uma função em JavaScript que verifica se um valor é `NaN` (Not-a-Number), permitindo identificar se um dado não é um número válido. Esta função é essencial para a validação de dados em aplicações web.

## Documentação
A função `isNaN()` é uma função global em JavaScript que retorna um valor booleano indicando se o valor fornecido é `NaN` ou não. O `NaN` é um valor especial que representa um número que não é um número real, geralmente resultante de operações matemáticas inválidas.

### Propósito
O propósito principal do `isNaN` é ajudar os desenvolvedores a validar os dados de entrada e a evitar erros que podem ocorrer ao tentar realizar operações aritméticas em valores que não são números.

### Uso
A função `isNaN()` pode ser utilizada da seguinte forma:

```javascript
isNaN(value);
```

- **value**: O valor que você deseja verificar.

### Detalhes
- `isNaN()` tenta converter o valor passado para um número antes de verificar se é `NaN`. Portanto, valores que não podem ser convertidos em números (como strings que não representam números) resultam em `true`.
- A função `Number.isNaN()` é uma alternativa mais estrita que verifica se o valor é exatamente `NaN`, sem realizar conversões.

## Exemplos
### Exemplo Básico
```javascript
console.log(isNaN(NaN)); // true
console.log(isNaN(123)); // false
console.log(isNaN('abc')); // true
console.log(isNaN('123')); // false
console.log(isNaN(undefined)); // true
```

### Exemplo de Validação de Entrada
```javascript
function validarEntrada(valor) {
    if (isNaN(valor)) {
        console.log("O valor fornecido não é um número.");
    } else {
        console.log("O valor fornecido é um número.");
    }
}

validarEntrada('teste'); // O valor fornecido não é um número.
validarEntrada(42); // O valor fornecido é um número.
```

## Explicação
Um dos erros mais comuns ao usar `isNaN` é não perceber que ele converte o valor passado para um número antes de verificar. Por exemplo:

```javascript
console.log(isNaN('123')); // false, pois '123' é convertido para 123
console.log(isNaN('abc')); // true, pois 'abc' não pode ser convertido em número
```

Outro ponto importante é a distinção entre `isNaN` e `Number.isNaN`. Enquanto `isNaN` pode retornar `true` para valores que não são números, `Number.isNaN` é mais rigoroso e retorna `true` apenas para o valor `NaN`.

### Conclusão
Ao trabalhar com dados de entrada em JavaScript, é crucial entender como o `isNaN` e `Number.isNaN` funcionam para garantir que sua aplicação trate corretamente erros de tipo e conversão.

## Resumo em Uma Linha
A função `isNaN` em JavaScript verifica se um valor não é um número, retornando `true` se o valor for `NaN` ou não puder ser convertido em número.