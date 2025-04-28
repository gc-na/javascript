<!--
Meta Description: # OfflineAudioContext: Criando Áudio em JavaScript Sem Conexão ## Sinopse O `OfflineAudioContext` é uma interface da Web Audio API que permite process...
Meta Keywords: áudio, que, offlineaudiocontext, offlinecontext, oscillator
-->

# OfflineAudioContext: Criando Áudio em JavaScript Sem Conexão

## Sinopse
O `OfflineAudioContext` é uma interface da Web Audio API que permite processar e gerar áudio em segundo plano, sem a necessidade de uma conexão de áudio em tempo real. É ideal para situações em que você deseja renderizar áudio de forma não interativa, como em aplicativos web que precisam gerar sons complexos.

## Documentação
### Propósito
O `OfflineAudioContext` é utilizado para criar e manipular áudio que não é reproduzido imediatamente. Ele permite que desenvolvedores renderizem áudio e o exportem como um arquivo, sem a latência e as limitações de um contexto de áudio em tempo real.

### Uso
Para criar um `OfflineAudioContext`, você deve especificar três parâmetros:

1. **Número de canais**: O número de canais de áudio (por exemplo, estéreo tem 2 canais).
2. **Taxa de amostragem**: A taxa de amostragem em Hertz (Hz), que define quantas amostras de áudio são capturadas por segundo.
3. **Duração**: A duração total em segundos do áudio que será processado.

A estrutura básica para criar um `OfflineAudioContext` é:

```javascript
const offlineContext = new OfflineAudioContext(numberOfChannels, length, sampleRate);
```

### Detalhes
Após criar um `OfflineAudioContext`, você pode usar suas propriedades e métodos, como:

- **`startRendering()`**: Inicia a renderização do áudio. Retorna uma Promise que é resolvida com o resultado da renderização.
- **`createGain()`**: Cria um nó de ganho, permitindo ajustar o volume do áudio.
- **`createOscillator()`**: Cria um oscilador que gera ondas sonoras.

## Exemplos

### Exemplo 1: Criando um Oscilador Simples

```javascript
const offlineContext = new OfflineAudioContext(2, 44100 * 2, 44100);

const oscillator = offlineContext.createOscillator();
oscillator.frequency.setValueAtTime(440, 0); // 440 Hz (Nota A)
oscillator.start();

oscillator.connect(offlineContext.destination);
offlineContext.startRendering().then((buffer) => {
  console.log('Audio renderizado com sucesso!', buffer);
});
```

### Exemplo 2: Ajustando o Volume com Gain Node

```javascript
const offlineContext = new OfflineAudioContext(1, 44100 * 2, 44100);
const gainNode = offlineContext.createGain();
gainNode.gain.setValueAtTime(0.5, 0); // Volume reduzido a 50%

const oscillator = offlineContext.createOscillator();
oscillator.frequency.setValueAtTime(440, 0);
oscillator.connect(gainNode);
gainNode.connect(offlineContext.destination);
oscillator.start();

offlineContext.startRendering().then((buffer) => {
  console.log('Audio com volume ajustado renderizado!', buffer);
});
```

## Explicação
Um erro comum ao usar o `OfflineAudioContext` é tentar reproduzir o áudio antes de chamar `startRendering()`. O áudio não será audível até que a renderização esteja concluída e os dados sejam manipulados. Além disso, é importante lembrar que nem todos os efeitos de áudio ou interações em tempo real são suportados neste contexto, o que pode levar a resultados inesperados se você tentar usar técnicas que dependem de um fluxo de áudio contínuo.

## Resumo em Uma Frase
O `OfflineAudioContext` é uma ferramenta essencial da Web Audio API que permite a criação e renderização de áudio em JavaScript sem a necessidade de reprodução em tempo real.