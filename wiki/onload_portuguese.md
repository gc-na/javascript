<!--
Meta Description: # onload em JavaScript: Entendendo o Comando e Suas Aplicações ## Sinopse O evento `onload` em JavaScript é um recurso fundamental que permite a execu...
Meta Keywords: onload, que, página, javascript, html
-->

# onload em JavaScript: Entendendo o Comando e Suas Aplicações

## Sinopse
O evento `onload` em JavaScript é um recurso fundamental que permite a execução de código assim que um documento HTML ou um recurso, como uma imagem, é totalmente carregado. Este evento é amplamente utilizado para garantir que scripts sejam executados apenas após a completa carga da página.

## Documentação
O `onload` é um evento que pode ser atribuído a objetos como `window`, `document` e elementos HTML. Ele é acionado quando o conteúdo da página, incluindo todos os elementos, imagens e outros recursos, foi completamente carregado.

### Propósito
O principal objetivo do `onload` é garantir que o JavaScript manipule elementos da página apenas após sua total disponibilização. Isso evita erros que podem surgir de tentativas de acessar elementos que ainda não estão prontos.

### Uso
Você pode usar o `onload` de várias maneiras, como mostrado abaixo:

- Em um elemento HTML:
  ```html
  <body onload="minhaFuncao()">
  ```

- Em um objeto JavaScript:
  ```javascript
  window.onload = function() {
      // Código a ser executado quando a página estiver totalmente carregada
  };
  ```

- Usando addEventListener:
  ```javascript
  window.addEventListener('load', function() {
      // Código a ser executado quando a página estiver totalmente carregada
  });
  ```

## Exemplos
### Exemplo 1: Usando onload no elemento body
```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <title>Exemplo onload</title>
    <script>
        function minhaFuncao() {
            alert("Página carregada!");
        }
    </script>
</head>
<body onload="minhaFuncao()">
    <h1>Bem-vindo!</h1>
</body>
</html>
```

### Exemplo 2: Usando window.onload
```javascript
window.onload = function() {
    console.log("A página foi carregada com sucesso!");
};
```

### Exemplo 3: Usando addEventListener
```javascript
window.addEventListener('load', function() {
    console.log("Todos os recursos da página foram carregados!");
});
```

## Explicação
Embora o evento `onload` seja útil, existem algumas armadilhas comuns a serem observadas:

- **Carregamento de múltiplos eventos:** Se você atribuir várias funções ao `onload` usando a forma tradicional (através da atribuição direta), apenas a última função será executada. Para evitar isso, sempre prefira `addEventListener`.

- **Desempenho:** O uso excessivo de `onload` pode afetar o desempenho, especialmente se muitas operações pesadas forem realizadas dentro dele. Sempre busque otimizar o que é executado neste evento.

- **Alternativas:** Para scripts que não dependem de carregamento total da página, considere usar `DOMContentLoaded`, que é disparado assim que o HTML é carregado e analisado, sem esperar por estilos, imagens, etc.

## Resumo em Uma Frase
O evento `onload` em JavaScript permite a execução de código após o carregamento completo de uma página ou recurso, garantindo a manipulação segura de elementos DOM.