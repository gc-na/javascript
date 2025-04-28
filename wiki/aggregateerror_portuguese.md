<!--
Meta Description: # AggregateError em JavaScript: O que é e Como Usar ## Sinopse O `AggregateError` é uma classe de erro introduzida no ECMAScript 2021 (ES12) que permi...
Meta Keywords: erro, aggregateerror, erros, error, que
-->

# AggregateError em JavaScript: O que é e Como Usar

## Sinopse
O `AggregateError` é uma classe de erro introduzida no ECMAScript 2021 (ES12) que permite agrupar múltiplos erros em uma única instância, facilitando o tratamento de erros em operações assíncronas que podem falhar simultaneamente.

## Documentação

### Propósito
O `AggregateError` é utilizado para representar um conjunto de erros que ocorreram durante a execução de operações assíncronas, como promessas. Essa classe é especialmente útil em situações onde várias promessas podem falhar e você deseja capturar todos os erros em um único objeto.

### Uso
O `AggregateError` pode ser instanciado diretamente, passando uma lista de erros como argumento. Ele também é usado internamente em métodos que gerenciam múltiplas promessas, como o `Promise.any()`.

#### Sintaxe
```javascript
const erroAgregado = new AggregateError(errors, message);
```

- **errors**: Um array contendo os erros a serem agregados.
- **message**: (opcional) Uma mensagem descritiva sobre o erro.

### Propriedades
- **message**: Retorna a mensagem de erro.
- **errors**: Retorna um array contendo todos os erros agregados.

## Exemplos

### Exemplo 1: Usando AggregateError
```javascript
const promessas = [
    Promise.reject(new Error("Erro 1")),
    Promise.reject(new Error("Erro 2")),
    Promise.resolve("Sucesso")
];

Promise.any(promessas)
    .then(result => console.log(result))
    .catch(erro => {
        console.log(erro instanceof AggregateError); // true
        console.log(erro.errors); // [Error: "Erro 1", Error: "Erro 2"]
        console.log(erro.message); // "All promises were rejected"
    });
```

### Exemplo 2: Instanciando AggregateError Manualmente
```javascript
const erros = [
    new Error("Falha na conexão"),
    new Error("Timeout excedido")
];

const erroAgregado = new AggregateError(erros, "Vários erros ocorreram");
console.log(erroAgregado.message); // "Vários erros ocorreram"
console.log(erroAgregado.errors); // [Error: "Falha na conexão", Error: "Timeout excedido"]
```

## Explicação
Um erro comum ao usar `AggregateError` é não compreender que ele é mais útil em cenários com múltiplas promessas. Usá-lo em contextos onde apenas um erro é esperado pode ser desnecessário. Além disso, é importante notar que o `AggregateError` foi introduzido em ES2021, portanto, não está disponível em ambientes mais antigos. Para garantir a compatibilidade, sempre verifique o suporte do ambiente onde o código será executado.

## Resumo em Uma Linha
O `AggregateError` em JavaScript permite agrupar múltiplos erros em uma única instância, facilitando o tratamento de falhas em operações assíncronas.