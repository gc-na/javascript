<!--
Meta Description: # Função em JavaScript: Guia Completo ## Sinopse A função em JavaScript é um bloco de código reutilizável que pode ser executado quando chamado. Elas ...
Meta Keywords: funções, função, javascript, código, são
-->

# Função em JavaScript: Guia Completo

## Sinopse
A função em JavaScript é um bloco de código reutilizável que pode ser executado quando chamado. Elas são fundamentais para a programação, permitindo a organização e modularização do código.

## Documentação
Uma função em JavaScript é definida utilizando a palavra-chave `function`, seguida por um nome, parênteses para parâmetros e um bloco de código que será executado. As funções podem ser declaradas de diversas maneiras, incluindo funções nomeadas, funções anônimas e expressões de função.

### Estrutura Básica
```javascript
function nomeDaFuncao(param1, param2) {
    // Código a ser executado
}
```

### Propósito
As funções são usadas para encapsular lógica, facilitar a reutilização de código e melhorar a legibilidade. Elas podem receber parâmetros e retornar valores, tornando-as uma parte essencial da programação em JavaScript.

### Uso
As funções podem ser chamadas em qualquer lugar do código após sua definição. Elas podem ser utilizadas para realizar operações, processar dados ou manipular o DOM (Document Object Model).

### Tipos de Funções
1. **Funções Nomeadas**: Definidas com um nome explícito.
2. **Funções Anônimas**: Não têm um nome e geralmente são usadas como argumentos para outras funções.
3. **Funções de Flecha**: Uma forma mais concisa de escrever funções, introduzida no ES6.

## Exemplos
### Função Nomeada
```javascript
function soma(a, b) {
    return a + b;
}
console.log(soma(2, 3)); // Saída: 5
```

### Função Anônima
```javascript
const multiplicar = function(a, b) {
    return a * b;
};
console.log(multiplicar(4, 5)); // Saída: 20
```

### Função de Flecha
```javascript
const dividir = (a, b) => a / b;
console.log(dividir(10, 2)); // Saída: 5
```

## Explicação
Um dos erros comuns ao trabalhar com funções é não levar em conta o escopo de variáveis. As variáveis declaradas dentro de uma função não são acessíveis fora dela. Além disso, é importante lembrar que funções podem ser chamadas antes de sua declaração, devido ao *hoisting*, mas isso não se aplica a expressões de função.

Outro ponto importante é a diferença entre parâmetros e argumentos. Parâmetros são as variáveis listadas na definição da função, enquanto argumentos são os valores que você passa para a função quando a chama.

## Resumo em Uma Linha
As funções em JavaScript são blocos de código reutilizáveis que permitem organizar e modularizar a lógica do programa.