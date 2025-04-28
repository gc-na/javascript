<!--
Meta Description: # encodeURI: Função para Codificação de URIs em JavaScript ## Sinopse A função `encodeURI` em JavaScript é utilizada para codificar uma URI (Identific...
Meta Keywords: uri, uma, caracteres, encodeuri, função
-->

# encodeURI: Função para Codificação de URIs em JavaScript

## Sinopse
A função `encodeURI` em JavaScript é utilizada para codificar uma URI (Identificador Uniforme de Recursos), substituindo caracteres especiais por suas representações percentuais, garantindo que a URI seja transmitida corretamente na web.

## Documentação
A função `encodeURI` é uma função global do JavaScript que converte uma URI em uma versão codificada. O propósito principal dessa função é preparar uma URI para ser utilizada em solicitações HTTP, evitando problemas de interpretação de caracteres especiais.

### Sintaxe
```javascript
encodeURI(uri)
```

### Parâmetros
- **uri**: Uma string que representa a URI a ser codificada.

### Retorno
Retorna uma nova string, que é a versão codificada da URI fornecida.

### Observações
- A função não codifica caracteres que têm um significado especial em URIs, como `:`, `/`, `?`, `&`, e `#`.
- Para codificar todos os caracteres especiais, deve-se usar a função `encodeURIComponent`.

## Exemplos
### Exemplo Básico
```javascript
const uri = "https://www.exemplo.com/uma página com espaços";
const uriCodificada = encodeURI(uri);
console.log(uriCodificada); // https://www.exemplo.com/uma%20p%C3%A1gina%20com%20espa%C3%A7os
```

### Exemplo com Caracteres Especiais
```javascript
const uri = "https://www.exemplo.com/procurar?busca=maçã & laranja";
const uriCodificada = encodeURI(uri);
console.log(uriCodificada); // https://www.exemplo.com/procurar?busca=maçã%20&%20laranja
```

## Explicação
Embora `encodeURI` seja útil, é importante entender algumas armadilhas comuns:
- **Não codifica todos os caracteres**: Como mencionado anteriormente, `encodeURI` não codifica caracteres que têm funções específicas nas URIs. Isso pode levar a erros se você tentar passar dados que contenham esses caracteres.
- **Uso apropriado**: Se você precisa codificar uma parte de uma URI, como um parâmetro de consulta, considere usar `encodeURIComponent`, que codifica todos os caracteres especiais.

## Resumo em Uma Linha
A função `encodeURI` em JavaScript codifica URIs, substituindo caracteres especiais por suas representações percentuais, facilitando a transmissão na web.