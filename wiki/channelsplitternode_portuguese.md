<!--
Meta Description: # ChannelSplitterNode em JavaScript: Manipulação Avançada de Áudio ## Sinopse O `ChannelSplitterNode` é uma interface da Web Audio API em JavaScript q...
Meta Keywords: audiocontext, áudio, const, splitter, channelsplitternode
-->

# ChannelSplitterNode em JavaScript: Manipulação Avançada de Áudio

## Sinopse
O `ChannelSplitterNode` é uma interface da Web Audio API em JavaScript que permite dividir um fluxo de áudio em múltiplos canais, facilitando a manipulação e o processamento individual dos canais de áudio.

## Documentação
O `ChannelSplitterNode` é utilizado para separar um único sinal de áudio em várias saídas, correspondendo ao número de canais do áudio de entrada. Isso é especialmente útil em aplicações de áudio onde diferentes canais de um sinal precisam ser processados separadamente, como em mixers de áudio ou efeitos de som em tempo real.

### Criação
Para criar um `ChannelSplitterNode`, você deve utilizar o método `createChannelSplitter()` do contexto de áudio (`AudioContext`). A sintaxe básica é a seguinte:

```javascript
const audioContext = new AudioContext();
const splitter = audioContext.createChannelSplitter(numberOfOutputs);
```

- `numberOfOutputs`: Um número inteiro que representa o número de canais que você deseja dividir. Esse valor deve ser maior que zero.

### Propriedades
- `numberOfOutputs`: Retorna o número de saídas do `ChannelSplitterNode`.

### Uso
Após a criação do `ChannelSplitterNode`, você pode conectar o nó a um nó de entrada e, em seguida, conectar suas saídas a diferentes destinos, como `GainNode`, `ChannelMergerNode`, ou mesmo a outros nós de processamento de áudio.

```javascript
const source = audioContext.createBufferSource();
source.connect(splitter);
```

## Exemplos
### Exemplo Básico de Uso

```javascript
const audioContext = new AudioContext();
const splitter = audioContext.createChannelSplitter(2); // Divide em 2 canais

// Conectando um buffer de áudio à entrada do splitter
const source = audioContext.createBufferSource();
// ... (carregar buffer de áudio aqui)
source.connect(splitter);

// Conectando as saídas do splitter a diferentes destinos
const leftChannel = splitter.connect(audioContext.destination, 0); // Canal esquerdo
const rightChannel = splitter.connect(audioContext.destination, 1); // Canal direito

source.start();
```

### Exemplo com Efeitos de Áudio

```javascript
const audioContext = new AudioContext();
const splitter = audioContext.createChannelSplitter(2);
const gainNodeLeft = audioContext.createGain();
const gainNodeRight = audioContext.createGain();

gainNodeLeft.gain.value = 0.5; // Reduz volume do canal esquerdo
gainNodeRight.gain.value = 1.5; // Aumenta volume do canal direito

const source = audioContext.createBufferSource();
// ... (carregar buffer de áudio aqui)
source.connect(splitter);

splitter.connect(gainNodeLeft, 0); // Canal esquerdo
splitter.connect(gainNodeRight, 1); // Canal direito

gainNodeLeft.connect(audioContext.destination);
gainNodeRight.connect(audioContext.destination);

source.start();
```

## Explicação
Alguns pontos a serem considerados ao usar o `ChannelSplitterNode`:

1. **Número de Saídas**: O número de saídas deve corresponder ao número de canais do áudio de entrada. Se o áudio de entrada for estéreo, você deve usar `createChannelSplitter(2)`.
   
2. **Conexões**: Certifique-se de que as saídas do `ChannelSplitterNode` estejam conectadas a nós válidos. Conexões incorretas podem resultar em silêncio ou em erros no processamento de áudio.

3. **Performance**: O uso excessivo de nós e conexões pode impactar a performance, especialmente em dispositivos com recursos limitados. Use apenas o necessário.

4. **Compatibilidade**: Verifique a compatibilidade do `ChannelSplitterNode` com diferentes navegadores, já que a implementação da Web Audio API pode variar.

## Resumo em Uma Linha
O `ChannelSplitterNode` é uma ferramenta poderosa na Web Audio API que permite dividir um sinal de áudio em múltiplos canais para processamento individual.