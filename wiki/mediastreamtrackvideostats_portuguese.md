<!--
Meta Description: # MediaStreamTrackVideoStats: Estatísticas de Vídeo em Streams de Mídia no JavaScript ## Sinopse O `MediaStreamTrackVideoStats` é uma interface do Jav...
Meta Keywords: vídeo, estatísticas, stat, mediastreamtrackvideostats, console
-->

# MediaStreamTrackVideoStats: Estatísticas de Vídeo em Streams de Mídia no JavaScript

## Sinopse
O `MediaStreamTrackVideoStats` é uma interface do JavaScript que fornece estatísticas detalhadas sobre a qualidade e o desempenho de uma pista de vídeo em um stream de mídia. Ele é utilizado principalmente em aplicações de comunicação em tempo real, como videochamadas e transmissões ao vivo.

## Documentação
### Propósito
O `MediaStreamTrackVideoStats` permite que desenvolvedores monitorem o desempenho de um stream de vídeo em tempo real, ajudando a otimizar a qualidade do vídeo e a experiência do usuário.

### Uso
Para acessar as estatísticas de vídeo, você deve primeiro obter uma instância de `MediaStreamTrack` de um stream de mídia ativo. A partir daí, você pode usar a API de estatísticas para coletar informações relevantes.

### Detalhes
As propriedades mais comuns disponíveis em `MediaStreamTrackVideoStats` incluem:
- `frameWidth`: A largura do vídeo em pixels.
- `frameHeight`: A altura do vídeo em pixels.
- `framesPerSecond`: O número de quadros por segundo (FPS) capturados.
- `framesEncoded`: O número total de quadros codificados.
- `framesDropped`: O número de quadros que foram descartados durante a codificação.

Essas estatísticas são essenciais para a análise de qualidade em tempo real e podem ser utilizadas para ajustar parâmetros de transmissão.

## Exemplos
### Exemplo Básico de Uso
```javascript
navigator.mediaDevices.getUserMedia({ video: true })
  .then(stream => {
    const videoTrack = stream.getVideoTracks()[0];
    const stats = videoTrack.getStats();

    stats.then(report => {
      report.forEach(stat => {
        if (stat.type === 'video') {
          console.log('Largura do Frame:', stat.frameWidth);
          console.log('Altura do Frame:', stat.frameHeight);
          console.log('Frames por Segundo:', stat.framesPerSecond);
          console.log('Frames Codificados:', stat.framesEncoded);
          console.log('Frames Descartados:', stat.framesDropped);
        }
      });
    });
  })
  .catch(error => {
    console.error('Erro ao acessar a câmera:', error);
  });
```

## Explicação
Ao trabalhar com `MediaStreamTrackVideoStats`, é importante ter em mente que:
- A coleta de estatísticas pode não ser instantânea; aguarde a resolução da Promise retornada por `getStats()`.
- Algumas propriedades podem variar dependendo do ambiente do dispositivo e da qualidade da conexão de rede.
- Este objeto pode não estar disponível em todos os navegadores, por isso, sempre verifique a compatibilidade.

## Resumo em Uma Linha
O `MediaStreamTrackVideoStats` fornece estatísticas em tempo real sobre o desempenho de pistas de vídeo em streams de mídia no JavaScript.