<!--
Meta Description: # onwebkitanimationiteration: Entendendo o Evento de Iteração de Animação em JavaScript ## Sinopse O evento `onwebkitanimationiteration` é um manipula...
Meta Keywords: que, onwebkitanimationiteration, evento, animação, iteração
-->

# onwebkitanimationiteration: Entendendo o Evento de Iteração de Animação em JavaScript

## Sinopse
O evento `onwebkitanimationiteration` é um manipulador de eventos em JavaScript que é acionado sempre que uma animação CSS com prefixo `-webkit-` completa uma iteração. Este evento é útil para executar ações específicas durante a execução de animações em elementos web.

## Documentação
O evento `onwebkitanimationiteration` é parte das interfaces de eventos de animação CSS e está associado a animações que utilizam o prefixo `-webkit-`, que foi amplamente utilizado para garantir compatibilidade com navegadores baseados em WebKit, como versões mais antigas do Safari e do Chrome.

### Propósito
O propósito principal deste evento é permitir que os desenvolvedores respondam a cada iteração de uma animação, possibilitando modificações dinâmicas no estado da aplicação ou na interface do usuário.

### Uso
Para utilizar o `onwebkitanimationiteration`, você deve adicioná-lo como um manipulador de eventos a um elemento HTML que possui uma animação CSS aplicada. O evento é acionado automaticamente cada vez que a animação completa uma iteração.

### Sintaxe
```javascript
element.onwebkitanimationiteration = function(event) {
    // Código a ser executado quando a animação completar uma iteração
};
```

## Exemplos
### Exemplo Básico
Neste exemplo, um evento `onwebkitanimationiteration` é adicionado a um elemento `<div>`, que muda de cor a cada iteração da animação.

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Exemplo de onwebkitanimationiteration</title>
    <style>
        .animacao {
            width: 100px;
            height: 100px;
            background-color: red;
            animation: mudarCor 2s infinite;
        }

        @keyframes mudarCor {
            0% { background-color: red; }
            100% { background-color: blue; }
        }
    </style>
</head>
<body>
    <div class="animacao" id="caixa"></div>
    <script>
        const caixa = document.getElementById('caixa');

        caixa.onwebkitanimationiteration = function() {
            console.log('A animação completou uma iteração!');
        };
    </script>
</body>
</html>
```

## Explicação
### Armadilhas Comuns
- **Compatibilidade de Navegadores**: O uso de `onwebkitanimationiteration` é específico para navegadores que suportam o prefixo `-webkit-`. Para garantir que seu código funcione em todos os navegadores, considere usar o evento padrão `animationiteration`, que é amplamente suportado.
  
- **Remoção do Manipulador**: Se você precisar remover o manipulador de eventos, utilize `removeEventListener()` e assegure-se de que o método esteja vinculado corretamente.

- **Cuidado com a Performance**: Acionar muitas funções durante a animação pode impactar a performance. É importante otimizar as funções que estão sendo chamadas no evento.

## Resumo em Uma Linha
O evento `onwebkitanimationiteration` em JavaScript permite que desenvolvedores respondam a cada iteração de animações CSS com prefixo `-webkit-`, facilitando interações dinâmicas na interface do usuário.