<!--
Meta Description: # ontransitionend: O Evento de Transição em JavaScript ## Sinopse O evento `ontransitionend` é um manipulador de eventos em JavaScript que permite det...
Meta Keywords: transição, ontransitionend, box, button, evento
-->

# ontransitionend: O Evento de Transição em JavaScript

## Sinopse
O evento `ontransitionend` é um manipulador de eventos em JavaScript que permite detectar quando uma transição CSS termina. Ele é frequentemente utilizado para executar ações após a conclusão de animações em elementos HTML.

## Documentação

### Propósito
O `ontransitionend` é acionado quando uma transição CSS atinge seu estado final. Isso é útil para criar interações dinâmicas e responsivas em aplicações web.

### Uso
Para utilizar o evento `ontransitionend`, você pode atribuí-lo a um elemento HTML. O evento pode ser usado diretamente nas propriedades do elemento ou através do método `addEventListener`.

### Sintaxe
```javascript
element.ontransitionend = function(event) {
    // Código a ser executado quando a transição termina
};
```
ou
```javascript
element.addEventListener('transitionend', function(event) {
    // Código a ser executado quando a transição termina
});
```

### Propriedades do Evento
- `propertyName`: O nome da propriedade CSS que sofreu a transição.
- `elapsedTime`: O tempo total que a transição levou, em segundos.
- `pseudoElement`: O pseudo-elemento associado à transição (se houver).

## Exemplos

### Exemplo 1: Usando ontransitionend
```html
<div id="box" style="width: 100px; height: 100px; background-color: red; transition: background-color 2s;"></div>
<button id="changeColor">Mudar Cor</button>

<script>
    const box = document.getElementById('box');
    const button = document.getElementById('changeColor');

    button.onclick = function() {
        box.style.backgroundColor = 'blue';
    };

    box.ontransitionend = function(event) {
        alert('A transição da cor terminou!');
    };
</script>
```

### Exemplo 2: Usando addEventListener
```html
<div id="box" style="width: 100px; height: 100px; background-color: red; transition: width 2s;"></div>
<button id="increaseSize">Aumentar Tamanho</button>

<script>
    const box = document.getElementById('box');
    const button = document.getElementById('increaseSize');

    button.onclick = function() {
        box.style.width = '200px';
    };

    box.addEventListener('transitionend', function(event) {
        console.log('A transição do tamanho terminou!');
    });
</script>
```

## Explicação
Um dos principais desafios ao usar `ontransitionend` é garantir que o evento seja capturado apenas uma vez para cada transição. Caso contrário, você pode acabar com múltiplas chamadas da mesma função. Além disso, se você estiver lidando com múltiplas transições em um único elemento, pode ser necessário verificar o `propertyName` para determinar qual transição terminou.

Outro ponto a ser observado é a compatibilidade entre navegadores. Embora `ontransitionend` seja amplamente suportado, é sempre bom verificar se o navegador que você está utilizando tem suporte para transições CSS.

## Resumo em Uma Linha
O `ontransitionend` é um evento JavaScript que permite detectar o término de transições CSS, facilitando a implementação de animações dinâmicas em páginas web.