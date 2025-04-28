<!--
Meta Description: # decodeURIComponent: Decodificando Componentes de URI em JavaScript ## Sinopse O `decodeURIComponent` é uma função embutida em JavaScript que decodif...
Meta Keywords: decodeuricomponent, que, uri, javascript, uma
-->

# decodeURIComponent: Decodificando Componentes de URI em JavaScript

## Sinopse
O `decodeURIComponent` é uma função embutida em JavaScript que decodifica uma string que foi codificada como um componente de URI, convertendo sequências de escape Unicode e percentuais de volta aos seus caracteres originais.

## Documentação
### Propósito
A função `decodeURIComponent` é utilizada para decodificar componentes de um URI que foram previamente codificados usando `encodeURIComponent`. Isso é essencial quando se trabalha com URLs, pois os navegadores codificam certos caracteres para garantir que os URIs sejam válidos e seguros.

### Uso
A sintaxe da função é a seguinte:

```javascript
decodeURIComponent(encodedURIComponent);
```

#### Parâmetros
- `encodedURIComponent`: Uma string que representa um componente de URI codificado. Esta string pode conter caracteres que foram codificados em formato percentual.

#### Retorno
A função retorna uma nova string que representa o valor decodificado do componente do URI.

### Detalhes
O `decodeURIComponent` é especialmente útil para manipular dados obtidos de URLs, como parâmetros de consulta, onde caracteres especiais podem ser codificados. Por exemplo, espaços são representados como `%20`, e caracteres como `!`, `@`, `#`, entre outros, podem ser codificados.

## Exemplos
### Exemplo 1: Decodificando um espaço
```javascript
const encoded = "Hello%20World%21";
const decoded = decodeURIComponent(encoded);
console.log(decoded); // Saída: Hello World!
```

### Exemplo 2: Decodificando caracteres especiais
```javascript
const encoded = "JavaScript%20%C2%A9%202023";
const decoded = decodeURIComponent(encoded);
console.log(decoded); // Saída: JavaScript © 2023
```

### Exemplo 3: Decodificando um parâmetro de URL
```javascript
const encodedUrl = "https%3A%2F%2Fexemplo.com%2Fproduto%3Fnome%3Dma%C3%A7%C3%A3%26pre%C3%A7o%3D10.00";
const decodedUrl = decodeURIComponent(encodedUrl);
console.log(decodedUrl); // Saída: https://exemplo.com/produto?nome=maçã&preço=10.00
```

## Explicação
### Armadilhas Comuns
1. **Uso de `decodeURI` vs `decodeURIComponent`**: É importante notar que `decodeURI` decodifica um URI completo, enquanto `decodeURIComponent` é destinado a decodificar apenas os componentes de um URI. Isso significa que se você usar `decodeURI` em uma string que contém caracteres especiais, pode não decodificá-los corretamente.

2. **Erros de Sintaxe**: Se a string de entrada contiver uma sequência de escape inválida, `decodeURIComponent` lançará uma exceção. Por exemplo, `decodeURIComponent('%')` resultará em um erro.

3. **Codificação Prévia**: Certifique-se de que a string fornecida já tenha sido codificada com `encodeURIComponent`. Caso contrário, a função pode não produzir o resultado esperado.

## Resumo em Uma Linha
A função `decodeURIComponent` decodifica componentes de URI codificados, convertendo sequências de escape em seus caracteres originais.