<!--
Meta Description: # Evento de Transição em JavaScript: Compreendendo o TransitionEvent ## Sinopse O `TransitionEvent` é um evento do DOM que é disparado quando uma tran...
Meta Keywords: que, transitionevent, transição, uma, css
-->

# Evento de Transição em JavaScript: Compreendendo o TransitionEvent

## Sinopse
O `TransitionEvent` é um evento do DOM que é disparado quando uma transição CSS começa ou termina, permitindo que os desenvolvedores JavaScript respondam a mudanças de estado das propriedades CSS de um elemento.

## Documentação
O `TransitionEvent` é parte da interface `Event` e é utilizado para capturar eventos relacionados a transições CSS. Este evento é especialmente útil em animações, onde você deseja executar um código específico em resposta ao início ou ao término de uma transição.

### Propósito
O principal propósito do `TransitionEvent` é fornecer uma maneira de detectar quando uma animação CSS começa e termina, permitindo que desenvolvedores criem interações mais ricas e dinâmicas em suas aplicações web.

### Uso
Para utilizar o `TransitionEvent`, você deve adicionar um listener de evento ao elemento HTML que possui transições CSS. Você pode escutar eventos como `transitionend`, que é disparado quando uma transição CSS é concluída.

### Detalhes
- **Propriedades do Evento**: O `TransitionEvent` possui algumas propriedades importantes:
  - `propertyName`: O nome da propriedade CSS que foi alterada.
  - `elapsedTime`: O tempo decorrido desde o início da transição até o ponto em que o evento foi disparado.
  - `pseudoElement`: O pseudoelemento associado à transição, se aplicável.

### Sintaxe
```javascript
element.addEventListener('transitionend', function(event) {
    // Seu código aqui
});
```

## Exemplos

### Exemplo Básico
```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <style>
        .caixa {
            width: 100px;
            height: 100px;
            background-color: blue;
            transition: background-color 1s ease;
        }
        .caixa.mudar {
            background-color: red;
        }
    </style>
    <title>Exemplo de TransitionEvent</title>
</head>
<body>
    <div class="caixa"></div>
    <button id="trocar">Trocar Cor</button>

    <script>
        const caixa = document.querySelector('.caixa');
        const botao = document.getElementById('trocar');

        botao.addEventListener('click', () => {
            caixa.classList.toggle('mudar');
        });

        caixa.addEventListener('transitionend', (event) => {
            console.log(`A cor mudou para ${event.propertyName}`);
        });
    </script>
</body>
</html>
```

## Explicação
Um erro comum ao trabalhar com `TransitionEvent` é não levar em conta que o evento só é disparado após a conclusão da transição. Assim, se você tentar aplicar uma lógica de forma imediata após adicionar ou remover uma classe que inicia a transição, pode não obter o resultado esperado. Além disso, é importante notar que o `TransitionEvent` é disparado para cada propriedade que possui uma transição, o que pode levar a múltiplos eventos se várias propriedades forem alteradas simultaneamente.

## Resumo em Uma Linha
O `TransitionEvent` em JavaScript permite capturar e responder a eventos de início e término de transições CSS, melhorando a interatividade em aplicações web.