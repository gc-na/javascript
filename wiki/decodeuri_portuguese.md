<!--
Meta Description: # decodeURI: Decodificando URLs em JavaScript ## Sinopse O `decodeURI` é uma função embutida em JavaScript que decodifica uma URI (Uniform Resource Id...
Meta Keywords: decodeuri, uma, uri, que, função
-->

# decodeURI: Decodificando URLs em JavaScript

## Sinopse
O `decodeURI` é uma função embutida em JavaScript que decodifica uma URI (Uniform Resource Identifier) previamente codificada. Essa função é essencial para manipular e interpretar adequadamente URLs, especialmente quando elas contêm caracteres especiais.

## Documentação
### Propósito
A função `decodeURI` é utilizada para converter uma string que representa uma URI codificada de volta ao seu formato original. É particularmente útil quando se trabalha com parâmetros de consulta em URLs, onde caracteres especiais são frequentemente codificados para garantir que a URI seja válida.

### Uso
A sintaxe para utilizar a função `decodeURI` é a seguinte:

```javascript
decodeURI(uri);
```

#### Parâmetros
- `uri`: Uma string que representa a URI codificada que se deseja decodificar.

#### Retorno
A função retorna uma nova string que representa a URI decodificada. Se a string de entrada não estiver codificada corretamente, o comportamento pode variar, mas ela será retornada sem alterações.

### Detalhes
- A função `decodeURI` não decodifica caracteres reservados, como `#`, `?`, e `&`, pois esses caracteres têm significados especiais em uma URI.
- Para decodificar caracteres reservados, utilize a função `decodeURIComponent`.

## Exemplos
### Exemplo 1: Decodificando uma URI simples
```javascript
const uriCodificada = "https%3A%2F%2Fwww.exemplo.com%2Fcaminho%3Fparametro%3Dvalor";
const uriDecodificada = decodeURI(uriCodificada);
console.log(uriDecodificada); // Saída: https://www.exemplo.com/caminho?parametro=valor
```

### Exemplo 2: Decodificando URI com espaços
```javascript
const uriComEspacos = "https%3A%2F%2Fwww.exemplo.com%2Fminha%20pagina";
const uriDecodificada = decodeURI(uriComEspacos);
console.log(uriDecodificada); // Saída: https://www.exemplo.com/minha pagina
```

## Explicação
### Armadilhas Comuns
- **Uso de `decodeURI` em vez de `decodeURIComponent`**: Uma armadilha comum é usar `decodeURI` para decodificar componentes de uma URL que contêm caracteres reservados. Isso pode levar a resultados inesperados, pois `decodeURI` não altera esses caracteres.
  
- **Codificação Inadequada**: Se a URI não estiver codificada corretamente, `decodeURI` pode não funcionar como esperado, resultando em uma string que pode não ser útil.

### Notas Adicionais
- É importante sempre garantir que as URIs estejam devidamente codificadas antes de serem passadas para `decodeURI`.
- A função é útil em ambientes que exigem manipulação de URLs, como em aplicações web que lidam com navegação e redirecionamento.

## Resumo em Uma Linha
A função `decodeURI` em JavaScript decodifica uma URI previamente codificada, convertendo caracteres especiais de volta ao seu formato original.