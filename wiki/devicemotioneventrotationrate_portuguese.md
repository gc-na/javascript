<!--
Meta Description: # DeviceMotionEventRotationRate em JavaScript: Controle de Movimento em Dispositivos ## Sinopse O `DeviceMotionEventRotationRate` é uma propriedade do...
Meta Keywords: rotação, rotationrate, alpha, beta, gamma
-->

# DeviceMotionEventRotationRate em JavaScript: Controle de Movimento em Dispositivos

## Sinopse
O `DeviceMotionEventRotationRate` é uma propriedade do evento `DeviceMotion` em JavaScript que fornece a taxa de rotação de um dispositivo em três eixos, permitindo que desenvolvedores criem experiências interativas baseadas em movimento.

## Documentação
### Propósito
A propriedade `rotationRate` do evento `DeviceMotionEvent` é utilizada para obter a velocidade de rotação do dispositivo ao longo dos eixos X, Y e Z. Essa informação é essencial para aplicações que exigem controle baseado em movimento, como jogos, aplicativos de realidade aumentada e outras experiências interativas.

### Uso
Para acessar os dados de rotação, primeiro, é necessário ouvir o evento `devicemotion`. A propriedade `rotationRate` retorna um objeto contendo três propriedades:
- `alpha`: taxa de rotação em torno do eixo Z (em graus por segundo).
- `beta`: taxa de rotação em torno do eixo X (em graus por segundo).
- `gamma`: taxa de rotação em torno do eixo Y (em graus por segundo).

#### Exemplo de Uso
```javascript
if (window.DeviceMotionEvent) {
    window.addEventListener('devicemotion', function(event) {
        const rotationRate = event.rotationRate;
        console.log('Rotação - Alpha: ' + rotationRate.alpha);
        console.log('Rotação - Beta: ' + rotationRate.beta);
        console.log('Rotação - Gamma: ' + rotationRate.gamma);
    });
} else {
    console.log('Dispositivo não suporta DeviceMotionEvent.');
}
```

## Exemplos
### Exemplo Simples de Monitoramento de Rotação
```javascript
window.addEventListener('devicemotion', function(event) {
    const { alpha, beta, gamma } = event.rotationRate;
    document.getElementById('rotationData').innerHTML = `
        <p>Alpha: ${alpha}°/s</p>
        <p>Beta: ${beta}°/s</p>
        <p>Gamma: ${gamma}°/s</p>
    `;
});
```

### Exemplo de Aplicação em Jogo
```javascript
let rotationFeedback = document.getElementById('feedback');

window.addEventListener('devicemotion', function(event) {
    const { alpha, beta, gamma } = event.rotationRate;
    rotationFeedback.innerHTML = `Movimento detectado! Alpha: ${alpha}, Beta: ${beta}, Gamma: ${gamma}`;
    // Aqui você pode adicionar lógica para controlar um personagem ou objeto no jogo.
});
```

## Explicação
### Armadilhas Comuns
- **Permissões**: Em dispositivos móveis, o acesso a eventos de movimento pode exigir permissões. Certifique-se de que a permissão de acesso a sensores está habilitada.
- **Precisão**: A precisão das leituras pode variar dependendo do dispositivo. Teste em diferentes dispositivos para garantir uma experiência consistente.
- **Desempenho**: O uso excessivo do evento `devicemotion` pode causar problemas de desempenho. Considere limitar a frequência de chamadas usando técnicas como debouncing ou throttling.

## Resumo em Uma Linha
O `DeviceMotionEventRotationRate` permite que desenvolvedores acessem a taxa de rotação de dispositivos em JavaScript, essencial para aplicações interativas baseadas em movimento.