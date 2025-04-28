<!--
Meta Description: # URIError em JavaScript: Entendendo e Manipulando Erros de URI ## Sinopse O `URIError` é um tipo de erro que ocorre em JavaScript quando há problemas...
Meta Keywords: urierror, error, que, uri, javascript
-->

# URIError em JavaScript: Entendendo e Manipulando Erros de URI

## Sinopse
O `URIError` é um tipo de erro que ocorre em JavaScript quando há problemas na manipulação de URIs (Uniform Resource Identifiers). Este erro é frequentemente encontrado ao usar funções que codificam ou decodificam URIs, como `decodeURI()` e `decodeURIComponent()`.

## Documentação
O `URIError` é uma classe de erro embutida em JavaScript que herda da classe `Error`. Ele é lançado quando uma função de URI recebe um valor que não é válido ou que não pode ser decodificado corretamente.

### Propósito
O principal propósito do `URIError` é facilitar a identificação e o tratamento de erros relacionados a URIs durante a execução de código JavaScript. Isso é especialmente útil ao trabalhar com URLs e quando se manipula dados que podem ter formatos inesperados.

### Uso
Para usar `URIError`, basta chamá-lo diretamente em seu código. Normalmente, você não cria instâncias de `URIError` manualmente, mas sim, trata-o através de blocos de captura `try...catch` ao trabalhar com funções que podem lançar esse erro.

### Detalhes
- **Classe**: `URIError`
- **Herança**: Extende a classe `Error`
- **Métodos Comuns**: `name`, `message`, `stack`

Quando um `URIError` é lançado, você pode capturá-lo e acessar suas propriedades para entender melhor o que ocorreu.

## Exemplos

### Exemplo 1: Tratamento de URIError com `decodeURI`
```javascript
try {
    const url = decodeURI('%E0%A4%A');
} catch (error) {
    if (error instanceof URIError) {
        console.error('Erro de URI: ', error.message);
    }
}
```

### Exemplo 2: Tratamento de URIError com `decodeURIComponent`
```javascript
try {
    const component = decodeURIComponent('%E0%A4%A');
} catch (error) {
    if (error instanceof URIError) {
        console.error('Erro de URI: ', error.message);
    }
}
```

### Exemplo 3: Função de manipulação de URI
```javascript
function safeDecode(uri) {
    try {
        return decodeURIComponent(uri);
    } catch (error) {
        if (error instanceof URIError) {
            console.error('URI malformada:', error.message);
            return null;
        }
    }
}

console.log(safeDecode('%E0%A4%A'));  // Saída: null (e mensagem de erro)
```

## Explicação
Um `URIError` pode ser frustrante, especialmente quando você não espera que uma string URI malformada cause uma exceção. É importante validar suas URIs antes de decodificá-las, utilizando métodos como `encodeURI()` e `encodeURIComponent()` para garantir que elas estejam no formato correto.

Um ponto comum de confusão é esquecer que as funções `decodeURI()` e `decodeURIComponent()` podem lançar erros se a string de entrada não for válida. Portanto, sempre utilize blocos `try...catch` ao chamar essas funções, para evitar que a execução do programa seja interrompida.

## Resumo em uma linha
O `URIError` em JavaScript é lançado quando ocorre um erro na manipulação de URIs, especialmente ao usar funções de decodificação.