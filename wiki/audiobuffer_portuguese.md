<!--
Meta Description: # AudioBuffer: Manipulação de Áudio em JavaScript ## Sinopse O `AudioBuffer` é uma interface da Web Audio API que permite armazenar dados de áudio em ...
Meta Keywords: audiocontext, áudio, para, buffer, audiobuffer
-->

# AudioBuffer: Manipulação de Áudio em JavaScript

## Sinopse
O `AudioBuffer` é uma interface da Web Audio API que permite armazenar dados de áudio em memória para processamento e reprodução. Essa funcionalidade é essencial para desenvolvedores que desejam criar aplicativos web interativos com áudio de alta qualidade.

## Documentação
O `AudioBuffer` é utilizado para representar um buffer de áudio que pode ser manipulado e reproduzido usando a Web Audio API. Ele é criado a partir de um contexto de áudio (`AudioContext`) e permite armazenar dados de áudio em um formato digital.

### Propósito
O `AudioBuffer` é fundamental para o processamento de áudio em tempo real, permitindo que desenvolvedores manipulem amostras de áudio, aplique efeitos e crie experiências sonoras dinâmicas.

### Uso
Para criar um `AudioBuffer`, você deve primeiro instanciar um `AudioContext`. O método `createBuffer()` do `AudioContext` é usado para criar um novo `AudioBuffer`. 

```javascript
const audioContext = new (window.AudioContext || window.webkitAudioContext)();
const buffer = audioContext.createBuffer(numberOfChannels, length, sampleRate);
```

- **numberOfChannels**: Número de canais de áudio (por exemplo, 1 para mono, 2 para estéreo).
- **length**: O número de amostras (sample frames) que o buffer deve conter.
- **sampleRate**: A taxa de amostragem (em Hertz) do áudio, que geralmente é 44100 Hz para áudio de CD.

## Exemplos
### Exemplo Básico de Criação de um AudioBuffer
```javascript
const audioContext = new (window.AudioContext || window.webkitAudioContext)();
const buffer = audioContext.createBuffer(2, audioContext.sampleRate * 2, audioContext.sampleRate);

// Preenchendo o buffer com um tom simples
const channelData = buffer.getChannelData(0);
for (let i = 0; i < buffer.length; i++) {
    channelData[i] = Math.sin(2 * Math.PI * 440 * (i / audioContext.sampleRate)); // 440 Hz
}
```

### Exemplo de Reprodução de um AudioBuffer
```javascript
const source = audioContext.createBufferSource();
source.buffer = buffer;
source.connect(audioContext.destination);
source.start(0);
```

## Explicação
### Armadilhas Comuns e Dicas
- **Taxa de Amostragem**: Certifique-se de que a taxa de amostragem do `AudioBuffer` corresponda àquela usada na gravação de áudio original para evitar distorções.
- **Número de Canais**: Um buffer estéreo deve ter exatamente dois canais. Tentar criar um buffer com um número diferente de canais resultará em erro.
- **Gerenciamento de Memória**: Buffers podem consumir uma quantidade significativa de memória, especialmente se forem grandes. Sempre libere os buffers que não são mais necessários chamando a função `close()` no `AudioContext`.

## Resumo em Uma Linha
O `AudioBuffer` permite armazenar e manipular dados de áudio digital em JavaScript, essencial para aplicações de áudio interativas.