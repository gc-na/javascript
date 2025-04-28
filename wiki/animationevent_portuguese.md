<!--
Meta Description: # Evento de Animação em JavaScript: Compreendendo o AnimationEvent ## Sinopse O `AnimationEvent` em JavaScript é um objeto que fornece informações sob...
Meta Keywords: animação, que, css, animationevent, animações
-->

# Evento de Animação em JavaScript: Compreendendo o AnimationEvent

## Sinopse
O `AnimationEvent` em JavaScript é um objeto que fornece informações sobre a execução de animações CSS, permitindo que os desenvolvedores capturem eventos como início, término e interrupção de animações.

## Documentação
O `AnimationEvent` é um tipo de evento que é disparado em resposta a animações CSS aplicadas a um elemento. Ele é parte da API de eventos do DOM e é utilizado para rastrear o progresso e o estado de animações definidas por meio de CSS. 

### Propósito
O objetivo principal do `AnimationEvent` é permitir que os desenvolvedores monitorem quando uma animação começa, termina ou é interrompida, facilitando a criação de interações dinâmicas em aplicações web.

### Uso
Para usar o `AnimationEvent`, você deve adicionar um ouvinte de eventos a um elemento DOM. Os eventos disponíveis incluem:

- `animationstart`: Disparado quando uma animação começa.
- `animationend`: Disparado quando uma animação termina.
- `animationiteration`: Disparado quando uma animação é reiniciada.

### Detalhes
Os objetos `AnimationEvent` contêm propriedades importantes, como:

- `animationName`: O nome da animação CSS que está sendo executada.
- `elapsedTime`: O tempo decorrido desde o início da animação até o momento em que o evento foi disparado.
- `pseudoElement`: O pseudo-elemento ao qual a animação está aplicada (se aplicável).

## Exemplos

### Exemplo Básico de Uso

```javascript
// Selecionando um elemento
const box = document.querySelector('.caixa');

// Adicionando ouvintes de eventos
box.addEventListener('animationstart', (event) => {
    console.log(`A animação "${event.animationName}" começou.`);
});

box.addEventListener('animationend', (event) => {
    console.log(`A animação "${event.animationName}" terminou.`);
});

// Adicionando uma classe que inicia a animação
box.classList.add('animar');
```

### CSS Exemplo

```css
.caixa {
    width: 100px;
    height: 100px;
    background-color: blue;
}

.animar {
    animation: exemploAnimacao 2s forwards;
}

@keyframes exemploAnimacao {
    from {
        transform: translateX(0);
    }
    to {
        transform: translateX(100px);
    }
}
```

## Explicação
É importante notar que o `AnimationEvent` pode não funcionar conforme esperado se as animações não forem definidas corretamente no CSS. Além disso, múltiplas animações aplicadas a um único elemento podem gerar confusão, pois cada animação disparará seus próprios eventos. Atente-se ao uso do `animationName` para identificar corretamente qual animação está disparando o evento.

Outro ponto a considerar é que o suporte a animações CSS pode variar entre navegadores, portanto, sempre teste em diferentes ambientes para garantir a compatibilidade.

## Resumo em Uma Linha
O `AnimationEvent` em JavaScript permite rastrear e responder a eventos relacionados a animações CSS, como início, término e iterações.