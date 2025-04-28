<!--
Meta Description: # XRLightEstimate: Estimativa de Luz em Realidade Aumentada com JavaScript ## Sinopse O XRLightEstimate é uma interface da WebXR que fornece informaçõ...
Meta Keywords: luz, xrlightestimate, que, ambiente, com
-->

# XRLightEstimate: Estimativa de Luz em Realidade Aumentada com JavaScript

## Sinopse
O XRLightEstimate é uma interface da WebXR que fornece informações sobre a iluminação ambiente em um espaço físico, permitindo que desenvolvedores de aplicações de realidade aumentada (AR) ajustem suas experiências visuais de acordo com as condições de luz do ambiente.

## Documentação
### Propósito
A interface XRLightEstimate é utilizada para obter dados sobre a luz ambiente em um contexto de realidade aumentada. Isso é crucial para criar experiências AR realistas, onde a iluminação do conteúdo digital se alinha com a iluminação do mundo real.

### Uso
O XRLightEstimate é acessado através da interface XRFrame, que é parte da API WebXR. O desenvolvedor deve primeiro garantir que está dentro de um ambiente de realidade aumentada e, em seguida, pode acessar a estimativa de luz a cada quadro renderizado.

### Detalhes
A interface XRLightEstimate fornece as seguintes propriedades:

- **ambientIntensity**: Um valor que representa a intensidade da luz ambiente, variando entre 0 (sem luz) e 1 (luz máxima).
- **colorTemperature**: Uma estimativa da temperatura da cor da luz em Kelvin, que ajuda a adaptar a cor do conteúdo digital à luz do ambiente.

Para usar o XRLightEstimate, você precisa de uma sessão XR iniciada com suporte a AR. Após iniciar a sessão, você pode acessar os dados de luz usando o método `getLightEstimate()` no objeto XRFrame.

## Exemplos
### Exemplo Básico de Uso do XRLightEstimate

```javascript
let xrSession;

navigator.xr.requestSession('immersive-ar').then((session) => {
    xrSession = session;
    const refSpace = xrSession.requestReferenceSpace('local');
    xrSession.requestAnimationFrame(onXRFrame);
});

function onXRFrame(time, frame) {
    const lightEstimate = frame.getLightEstimate();
    
    if (lightEstimate) {
        const ambientIntensity = lightEstimate.ambientIntensity;
        const colorTemperature = lightEstimate.colorTemperature;

        // Use ambientIntensity e colorTemperature para ajustar a cena
        console.log(`Intensidade Ambiente: ${ambientIntensity}`);
        console.log(`Temperatura da Cor: ${colorTemperature}K`);
    }

    xrSession.requestAnimationFrame(onXRFrame);
}
```

## Explicação
### Problemas Comuns e Observações
- **Compatibilidade**: O XRLightEstimate só está disponível em navegadores que suportam a API WebXR. Certifique-se de testar em ambientes compatíveis.
- **Precisão**: As estimativas de luz podem variar dependendo da qualidade do sensor do dispositivo. A calibração da câmera e as condições de iluminação podem influenciar os resultados.
- **Desempenho**: Consultar a estimativa de luz em cada quadro pode impactar o desempenho da aplicação, especialmente em dispositivos com hardware limitado. Considere otimizar o uso das informações.

## Resumo em Uma Linha
O XRLightEstimate permite que desenvolvedores de JavaScript obtenham informações sobre a iluminação ambiente em aplicações de realidade aumentada, melhorando a integração do conteúdo digital com o mundo real.