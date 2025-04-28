<!--
Meta Description: # onmouseenter: Entenda o Evento de Entrada do Mouse em JavaScript ## Sinopse O evento `onmouseenter` em JavaScript é utilizado para detectar quando o...
Meta Keywords: onmouseenter, mouse, html, div, evento
-->

# onmouseenter: Entenda o Evento de Entrada do Mouse em JavaScript

## Sinopse
O evento `onmouseenter` em JavaScript é utilizado para detectar quando o cursor do mouse entra em um elemento HTML específico, permitindo a execução de funções e a manipulação do DOM de forma interativa.

## Documentação
O `onmouseenter` é um evento que faz parte do modelo de eventos do DOM (Document Object Model). Este evento é acionado quando o ponteiro do mouse entra na área de um elemento. Diferente do evento `onmouseover`, o `onmouseenter` não é disparado quando o mouse entra em um elemento filho, tornando-o ideal para situações onde você deseja detectar a entrada do mouse apenas em um único elemento.

### Propósito
O propósito principal do `onmouseenter` é criar interações dinâmicas em páginas web, como destacar elementos ou exibir informações adicionais ao usuário quando ele passa o mouse sobre um item.

### Uso
O `onmouseenter` pode ser adicionado diretamente no elemento HTML como um atributo ou através de JavaScript. A seguir, um exemplo de como utilizá-lo:

#### Atributo HTML
```html
<div onmouseenter="alert('Mouse entrou!')">Passe o mouse aqui!</div>
```

#### Uso com JavaScript
```javascript
const div = document.querySelector('div');
div.onmouseenter = function() {
    alert('Mouse entrou!');
};
```

## Exemplos
### Exemplo 1: Cor de Fundo ao Passar o Mouse
```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Exemplo onmouseenter</title>
    <style>
        .caixa {
            width: 200px;
            height: 200px;
            background-color: lightblue;
            border: 1px solid blue;
            text-align: center;
            line-height: 200px;
            margin: 20px;
        }
    </style>
</head>
<body>
    <div class="caixa" onmouseenter="this.style.backgroundColor='lightgreen'">Passe o mouse aqui!</div>
</body>
</html>
```

### Exemplo 2: Exibir uma Mensagem
```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Exemplo onmouseenter</title>
</head>
<body>
    <div id="mensagem" style="display:none;">Bem-vindo ao nosso site!</div>
    <button id="botao">Passe o mouse aqui!</button>

    <script>
        const botao = document.getElementById('botao');
        const mensagem = document.getElementById('mensagem');

        botao.onmouseenter = function() {
            mensagem.style.display = 'block';
        };

        botao.onmouseleave = function() {
            mensagem.style.display = 'none';
        };
    </script>
</body>
</html>
```

## Explicação
Um dos principais desafios ao usar o `onmouseenter` é a confusão com o evento `onmouseover`. É importante lembrar que `onmouseenter` não é ativado quando o mouse entra em um elemento filho, o que pode ser vantajoso em muitas situações. Além disso, o uso excessivo de eventos pode levar a um desempenho inferior da página, especialmente em elementos com muitos filhos. Portanto, sempre teste a performance e evite event handlers desnecessários.

## Resumo em Uma Linha
O evento `onmouseenter` permite a detecção da entrada do mouse em um elemento HTML, proporcionando interatividade e dinamismo nas páginas web.