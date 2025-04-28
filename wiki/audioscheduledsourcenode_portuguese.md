<!--
Meta Description: # AudioScheduledSourceNode: Manipulação Avançada de Áudio em JavaScript ## Sinopse O AudioScheduledSourceNode permite a reprodução de áudio de forma p...
Meta Keywords: áudio, reprodução, que, audioscheduledsourcenode, audiobuffersourcenode
-->

# AudioScheduledSourceNode: Manipulação Avançada de Áudio em JavaScript

## Sinopse
O AudioScheduledSourceNode permite a reprodução de áudio de forma programada e precisa na Web, sendo um componente essencial da API Web Audio. Com ele, desenvolvedores podem criar experiências sonoras dinâmicas e interativas.

## Documentação
O `AudioScheduledSourceNode` é uma interface da API Web Audio que representa uma fonte de áudio que pode ser programada para iniciar e parar a reprodução em momentos específicos. Essa interface serve como uma base para outros tipos de nós de áudio, como `AudioBufferSourceNode`, que é utilizado para reproduzir dados de áudio armazenados em buffers.

### Propósito
O principal propósito do `AudioScheduledSourceNode` é permitir que os desenvolvedores tenham controle total sobre a reprodução de áudio, programando eventos de início e término com precisão.

### Uso
Para utilizar o `AudioScheduledSourceNode`, você deve primeiro criar um contexto de áudio (`AudioContext`). Em seguida, você pode criar uma instância de um nó de áudio, como `AudioBufferSourceNode`, que herda de `AudioScheduledSourceNode`. 

### Detalhes Importantes
- **Métodos**: O `AudioScheduledSourceNode` possui métodos como `start()` e `stop()`, que permitem iniciar e parar a reprodução do áudio.
- **Parâmetros**: Os métodos mencionados aceitam parâmetros que permitem especificar o tempo de início e o tempo de parada da reprodução.
- **Eventos**: Os nós de áudio podem emitir eventos, como `ended`, quando a reprodução é concluída.

## Exemplos

### Exemplo Básico de Reproduzir um Áudio
```javascript
const audioContext = new AudioContext();
const audioBufferSourceNode = audioContext.createBufferSource();

// Carregar um buffer de áudio
fetch('audio-file.mp3')
  .then(response => response.arrayBuffer())
  .then(data => audioContext.decodeAudioData(data))
  .then(buffer => {
    audioBufferSourceNode.buffer = buffer;
    audioBufferSourceNode.connect(audioContext.destination);
    
    // Iniciar a reprodução após 2 segundos
    audioBufferSourceNode.start(audioContext.currentTime + 2);
  })
  .catch(error => console.error('Error loading audio file:', error));
```

### Exemplo de Parar a Reprodução
```javascript
// Parar a reprodução após 5 segundos
audioBufferSourceNode.stop(audioContext.currentTime + 5);
```

## Explicação
Um dos principais desafios ao trabalhar com `AudioScheduledSourceNode` é garantir que o áudio seja carregado antes de tentar reproduzi-lo. Além disso, é importante lembrar que um `AudioBufferSourceNode` só pode ser reproduzido uma vez. Se você precisar reproduzir o mesmo áudio novamente, deve criar uma nova instância do `AudioBufferSourceNode`.

Outro ponto a considerar é que a reprodução de áudio não começará até que a interação do usuário com a página ocorra, devido a restrições de reprodução automática em muitos navegadores. Por isso, é recomendado iniciar a reprodução em resposta a eventos, como cliques ou toques.

## Resumo em Uma Linha
O `AudioScheduledSourceNode` é uma interface da API Web Audio que permite a reprodução precisa e programada de áudio em aplicações JavaScript.