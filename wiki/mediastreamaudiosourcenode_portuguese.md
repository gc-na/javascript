<!--
Meta Description: # MediaStreamAudioSourceNode em JavaScript: Capturando Áudio em Tempo Real ## Sinopse O `MediaStreamAudioSourceNode` é uma interface da Web Audio API ...
Meta Keywords: áudio, audiocontext, mediastreamaudiosourcenode, const, error
-->

# MediaStreamAudioSourceNode em JavaScript: Capturando Áudio em Tempo Real

## Sinopse
O `MediaStreamAudioSourceNode` é uma interface da Web Audio API que permite capturar áudio de um stream de mídia, como uma chamada de vídeo ou uma gravação, para processá-lo usando a API de áudio do navegador.

## Documentação
O `MediaStreamAudioSourceNode` serve como uma fonte de áudio que alimenta um gráfico de áudio a partir de um `MediaStream`. Essa funcionalidade é especialmente útil para aplicações que requerem manipulação de áudio em tempo real, como chamadas de vídeo, gravações de áudio ou transmissões ao vivo.

### Propósito
- Capturar áudio de um `MediaStream`.
- Integrar com outras partes da Web Audio API para manipular e processar áudio em tempo real.

### Uso
Para utilizar o `MediaStreamAudioSourceNode`, você deve seguir estas etapas:

1. Criar um contexto de áudio usando `AudioContext`.
2. Criar um `MediaStream` (por exemplo, usando `getUserMedia`).
3. Criar um `MediaStreamAudioSourceNode` passando o `MediaStream` para o contexto de áudio.

### Detalhes
```javascript
const audioContext = new (window.AudioContext || window.webkitAudioContext)();
navigator.mediaDevices.getUserMedia({ audio: true })
  .then((stream) => {
    const source = audioContext.createMediaStreamSource(stream);
    // Operações adicionais podem ser realizadas com 'source'
  })
  .catch((error) => {
    console.error('Erro ao acessar o microfone:', error);
  });
```

## Exemplos
### Exemplo Básico
```javascript
// Criando um contexto de áudio
const audioContext = new (window.AudioContext || window.webkitAudioContext)();

// Capturando áudio do microfone
navigator.mediaDevices.getUserMedia({ audio: true })
  .then((stream) => {
    // Criando o MediaStreamAudioSourceNode
    const source = audioContext.createMediaStreamSource(stream);
    source.connect(audioContext.destination); // Enviar áudio para os alto-falantes
  })
  .catch((error) => {
    console.error('Erro ao acessar o microfone:', error);
  });
```

### Exemplo com Análise de Áudio
```javascript
const audioContext = new (window.AudioContext || window.webkitAudioContext)();
navigator.mediaDevices.getUserMedia({ audio: true })
  .then((stream) => {
    const source = audioContext.createMediaStreamSource(stream);
    const analyser = audioContext.createAnalyser();
    
    // Conectando o MediaStreamAudioSourceNode ao analisador
    source.connect(analyser);
    analyser.connect(audioContext.destination);
    
    // Configurações do analisador
    analyser.fftSize = 2048;
    const bufferLength = analyser.frequencyBinCount;
    const dataArray = new Uint8Array(bufferLength);
    
    function draw() {
      requestAnimationFrame(draw);
      analyser.getByteFrequencyData(dataArray);
      // Processamento dos dados de áudio...
    }
    draw();
  })
  .catch((error) => {
    console.error('Erro ao acessar o microfone:', error);
  });
```

## Explicação
Um erro comum ao trabalhar com `MediaStreamAudioSourceNode` é tentar utilizá-lo antes que o contexto de áudio esteja em um estado "suspenso". É necessário garantir que o contexto esteja em execução chamando `audioContext.resume()` se estiver suspenso. Além disso, o `MediaStream` deve ser obtido com sucesso, o que requer permissões adequadas do usuário.

## Resumo em Uma Linha
O `MediaStreamAudioSourceNode` é uma interface da Web Audio API que permite capturar e processar áudio em tempo real de um `MediaStream` no JavaScript.