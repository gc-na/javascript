<!--
Meta Description: # ScriptProcessorNode em JavaScript: Manipulação de Áudio em Tempo Real ## Sinopse O `ScriptProcessorNode` é uma interface da Web Audio API que permit...
Meta Keywords: áudio, const, scriptprocessornode, audiocontext, event
-->

# ScriptProcessorNode em JavaScript: Manipulação de Áudio em Tempo Real

## Sinopse
O `ScriptProcessorNode` é uma interface da Web Audio API que permite a manipulação de áudio em tempo real, possibilitando a criação de efeitos e processamento de áudio personalizado diretamente no navegador.

## Documentação
O `ScriptProcessorNode` é utilizado para processar o fluxo de áudio em tempo real, permitindo que os desenvolvedores possam alterar, analisar ou gerar áudio. Ele é parte do contexto de áudio (AudioContext) e pode ser usado para aplicar efeitos, como modulação ou filtragem, e para realizar tarefas como a análise do espectro de um sinal de áudio.

### Propósito
O propósito do `ScriptProcessorNode` é fornecer uma maneira de processar áudio de forma flexível e em tempo real, permitindo que os desenvolvedores criem experiências sonoras interativas e dinâmicas.

### Uso
Para utilizar o `ScriptProcessorNode`, siga os passos abaixo:

1. Crie um contexto de áudio:
   ```javascript
   const audioContext = new (window.AudioContext || window.webkitAudioContext)();
   ```

2. Crie um `ScriptProcessorNode`:
   ```javascript
   const bufferSize = 4096; // Tamanho do buffer
   const scriptProcessor = audioContext.createScriptProcessor(bufferSize, 1, 1);
   ```

3. Conecte o `ScriptProcessorNode` a um nó de áudio (por exemplo, uma fonte de áudio):
   ```javascript
   const source = audioContext.createBufferSource();
   source.connect(scriptProcessor);
   scriptProcessor.connect(audioContext.destination);
   ```

4. Defina a função de processamento de áudio:
   ```javascript
   scriptProcessor.onaudioprocess = function(event) {
       const inputBuffer = event.inputBuffer;
       const outputBuffer = event.outputBuffer;

       for (let channel = 0; channel < outputBuffer.numberOfChannels; channel++) {
           const inputData = inputBuffer.getChannelData(channel);
           const outputData = outputBuffer.getChannelData(channel);

           for (let sample = 0; sample < inputBuffer.length; sample++) {
               // Processamento de áudio
               outputData[sample] = inputData[sample]; // Exemplo: Passagem direta
           }
       }
   };
   ```

## Exemplos
### Exemplo 1: Passagem Direta de Áudio
O exemplo abaixo demonstra como passar o áudio de uma fonte sem alterações:
```javascript
const audioContext = new (window.AudioContext || window.webkitAudioContext)();
const scriptProcessor = audioContext.createScriptProcessor(4096, 1, 1);
scriptProcessor.onaudioprocess = function(event) {
    const inputData = event.inputBuffer.getChannelData(0);
    const outputData = event.outputBuffer.getChannelData(0);
    for (let i = 0; i < inputData.length; i++) {
        outputData[i] = inputData[i]; // Passagem direta
    }
};
```

### Exemplo 2: Invertendo o Áudio
Este exemplo inverte o áudio processado:
```javascript
scriptProcessor.onaudioprocess = function(event) {
    const inputData = event.inputBuffer.getChannelData(0);
    const outputData = event.outputBuffer.getChannelData(0);
    for (let i = 0; i < inputData.length; i++) {
        outputData[i] = inputData[inputData.length - 1 - i]; // Inversão
    }
};
```

## Explicação
### Armadilhas Comuns
- **Desempenho**: O `ScriptProcessorNode` pode introduzir latência se não for utilizado corretamente. O tamanho do buffer deve ser ajustado para atender às necessidades de desempenho da aplicação.
- **Obsolescência**: O `ScriptProcessorNode` está obsoleto e seu uso é desencorajado em favor da `AudioWorklet`, que oferece um modelo mais eficiente e poderoso para o processamento de áudio.
- **Limitações de Canal**: O `ScriptProcessorNode` suporta apenas um número fixo de canais. Se você precisar de um processador de áudio multicanal, considere usar o `AudioWorklet`.

## Resumo em Uma Linha
O `ScriptProcessorNode` permite a manipulação de áudio em tempo real na Web Audio API, embora seu uso esteja sendo gradualmente substituído pelo `AudioWorklet`.