<!--
Meta Description: # RangeError em JavaScript: Entenda e Resolva Erros de Intervalo ## Sinopse O `RangeError` é um tipo de erro no JavaScript que ocorre quando um valor ...
Meta Keywords: rangeerror, que, javascript, não, erro
-->

# RangeError em JavaScript: Entenda e Resolva Erros de Intervalo

## Sinopse
O `RangeError` é um tipo de erro no JavaScript que ocorre quando um valor não está dentro do intervalo esperado. Este erro é comum em situações que envolvem operações matemáticas, conversões de tipo e manipulação de strings.

## Documentação
### O que é o RangeError?
O `RangeError` é uma classe de erro que é lançada em JavaScript quando uma operação é realizada com um valor fora dos limites permitidos. Isso pode acontecer em várias situações, como ao passar um número inválido para funções que esperam um valor em um intervalo específico, ou quando um array é manipulado de maneira inadequada.

### Uso do RangeError
O `RangeError` pode ser gerado automaticamente pelo JavaScript ou pode ser lançado manualmente por um desenvolvedor. Para criar um `RangeError` manualmente, você pode usar o construtor `RangeError` e passar uma mensagem opcional que descreve o erro.

#### Sintaxe:
```javascript
throw new RangeError("Mensagem de erro personalizada");
```

### Detalhes
O `RangeError` é um subtipo de `Error`, portanto, herda todas as propriedades e métodos de `Error`. Ele é frequentemente utilizado nas seguintes circunstâncias:

- Quando um número é passado para uma função fora do intervalo esperado.
- Quando um array é acessado com um índice que não existe.
- Em operações que dependem de limites, como `setTimeout` ou `setInterval`.

## Exemplos
### Exemplo 1: Acesso a Índice Inválido
```javascript
const array = [1, 2, 3];
console.log(array[5]); // undefined, mas não lança RangeError
```

### Exemplo 2: Lançamento de RangeError
```javascript
function calcularRaizQuadrada(valor) {
    if (valor < 0) {
        throw new RangeError("Não é possível calcular a raiz quadrada de um número negativo.");
    }
    return Math.sqrt(valor);
}

try {
    console.log(calcularRaizQuadrada(-1));
} catch (e) {
    console.error(e); // RangeError: Não é possível calcular a raiz quadrada de um número negativo.
}
```

### Exemplo 3: Números Fora do Intervalo
```javascript
function definirIdade(idade) {
    if (idade < 0 || idade > 150) {
        throw new RangeError("Idade deve estar entre 0 e 150.");
    }
    console.log("Idade definida:", idade);
}

try {
    definirIdade(200); // Lança RangeError
} catch (e) {
    console.error(e); // RangeError: Idade deve estar entre 0 e 150.
}
```

## Explicação
O `RangeError` pode ser confuso para desenvolvedores iniciantes, especialmente quando não está claro qual operação gerou o erro. Um erro comum é não validar entradas antes de realizar operações que dependem de valores numéricos. Sempre é recomendado implementar validações para garantir que os dados estejam dentro dos limites esperados antes de prosseguir com operações críticas.

Além disso, ao trabalhar com arrays, é importante lembrar que acessar índices fora do comprimento do array não gera um `RangeError`, mas sim retorna `undefined`. Por isso, a validação de índices é uma boa prática para evitar comportamentos inesperados.

## Resumo em Uma Linha
O `RangeError` em JavaScript é um erro que indica que um valor não está dentro do intervalo esperado, sendo comum em operações matemáticas e manipulações de dados.