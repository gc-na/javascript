<!--
Meta Description: # AudioBufferSourceNode em JavaScript: Guia Completo para Manipulação de Áudio ## Sinopse O `AudioBufferSourceNode` é uma interface da Web Audio API q...
Meta Keywords: source, áudio, para, audiocontext, audiobuffersourcenode
-->

# AudioBufferSourceNode em JavaScript: Guia Completo para Manipulação de Áudio

## Sinopse
O `AudioBufferSourceNode` é uma interface da Web Audio API que permite reproduzir áudio armazenado em um `AudioBuffer`, oferecendo controle preciso sobre a reprodução e manipulação do som em aplicações web.

## Documentação
O `AudioBufferSourceNode` é utilizado para tocar sons que foram previamente carregados em um buffer de áudio. Ele é um dos nós fundamentais da Web Audio API, permitindo a reprodução de áudio com características específicas, como controle de volume, tempo de reprodução e manipulação de efeitos.

### Propósito
O `AudioBufferSourceNode` é projetado para permitir a reprodução de áudio de forma eficiente e flexível, possibilitando que desenvolvedores criem experiências sonoras ricas em aplicações web.

### Uso
Para usar o `AudioBufferSourceNode`, siga os passos abaixo:

1. **Criar um contexto de áudio**:
   ```javascript
   const audioContext = new (window.AudioContext || window.webkitAudioContext)();
   ```

2. **Carregar um áudio em um `AudioBuffer`**:
   ```javascript
   function carregarAudio(url) {
       return fetch(url)
           .then(response => response.arrayBuffer())
           .then(data => audioContext.decodeAudioData(data));
   }
   ```

3. **Criar e configurar um `AudioBufferSourceNode`**:
   ```javascript
   carregarAudio('caminho/para/seu/audio.mp3').then(audioBuffer => {
       const source = audioContext.createBufferSource();
       source.buffer = audioBuffer;

       // Conectar ao destino (alto-falante)
       source.connect(audioContext.destination);

       // Iniciar a reprodução
       source.start(0);
   });
   ```

### Detalhes
- O `AudioBufferSourceNode` pode ser reproduzido apenas uma vez. Para reproduzir o áudio novamente, é necessário criar um novo nó.
- Ele pode ser configurado com propriedades como `loop` para reprodução contínua.
- É possível conectar o nó a outros nós da Web Audio API para aplicar efeitos, como equalização ou reverberação.

## Exemplos
### Exemplo Básico de Reprodução
```javascript
const audioContext = new (window.AudioContext || window.webkitAudioContext)();
const source = audioContext.createBufferSource();

// Carregar e reproduzir um áudio
carregarAudio('caminho/para/seu/audio.mp3').then(audioBuffer => {
    source.buffer = audioBuffer;
    source.connect(audioContext.destination);
    source.start();
});
```

### Exemplo com Loop
```javascript
carregarAudio('caminho/para/seu/audio.mp3').then(audioBuffer => {
    const source = audioContext.createBufferSource();
    source.buffer = audioBuffer;
    source.loop = true; // Habilita o loop
    source.connect(audioContext.destination);
    source.start();
});
```

## Explicação
Um erro comum ao usar o `AudioBufferSourceNode` é tentar reproduzir o mesmo nó várias vezes, o que resulta em uma exceção. Sempre crie um novo nó para cada reprodução. Além disso, lembre-se de que o `AudioBufferSourceNode` deve ser iniciado antes que o contexto de áudio esteja em execução, ou você poderá não ouvir nada.

Outro ponto importante é o tratamento de promessas ao carregar arquivos de áudio. Certifique-se de que o arquivo foi carregado e decodificado corretamente antes de tentar reproduzi-lo.

## Resumo em Uma Linha
O `AudioBufferSourceNode` é uma interface da Web Audio API que permite reproduzir áudio armazenado em um `AudioBuffer`, facilitando o controle e manipulação do som em aplicações web.