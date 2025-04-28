<!--
Meta Description: # WaveShaperNode: Manipulando Ondas de Áudio com JavaScript ## Sinopse O WaveShaperNode é uma interface do Web Audio API que permite aos desenvolvedor...
Meta Keywords: audiocontext, distorção, const, waveshaper, waveshapernode
-->

# WaveShaperNode: Manipulando Ondas de Áudio com JavaScript

## Sinopse
O WaveShaperNode é uma interface do Web Audio API que permite aos desenvolvedores modificar formas de onda de áudio, criando distorções e efeitos sonoros únicos. Essa ferramenta é essencial para a manipulação avançada de áudio em aplicações web.

## Documentação
O WaveShaperNode é usado para aplicar uma curva de distorção a um sinal de áudio. Ele recebe um sinal de entrada, aplica uma função de mapeamento e produz um sinal de saída modificado. Isso é especialmente útil para criar efeitos como overdrive, fuzz e outros tipos de distorção.

### Propriedades Principais
- **curve**: Um `Float32Array` que define a função de mapeamento da forma de onda. O valor de cada elemento na matriz deve estar entre -1 e 1.
- **oversample**: Define o método de oversampling usado para suavizar a distorção. Pode ser `none`, `2x` ou `4x`.

### Métodos
- **constructor()**: Cria uma nova instância de WaveShaperNode.
- **connect(destination)**: Conecta o WaveShaperNode a outro nó de áudio.
- **disconnect(destination)**: Desconecta o WaveShaperNode de um nó de áudio.

### Uso
Para usar o WaveShaperNode, você primeiro deve criar um contexto de áudio e, em seguida, instanciar o WaveShaperNode. Você pode definir a curva de distorção e conectar o nó ao seu fluxo de áudio.

```javascript
const audioContext = new (window.AudioContext || window.webkitAudioContext)();
const waveShaper = audioContext.createWaveShaper();
```

## Exemplos

### Exemplo 1: Distorção Simples
```javascript
const audioContext = new (window.AudioContext || window.webkitAudioContext)();
const waveShaper = audioContext.createWaveShaper();

// Definindo a curva de distorção
const curve = new Float32Array(44100);
for (let i = 0; i < 44100; ++i) {
    const x = i * 2 / 44100 - 1; // Normaliza entre -1 e 1
    curve[i] = (Math.abs(x) < 0.5) ? x * 2 : 1; // Distorção
}
waveShaper.curve = curve;
waveShaper.oversample = '4x';

// Conectando a um oscilador
const oscillator = audioContext.createOscillator();
oscillator.connect(waveShaper);
waveShaper.connect(audioContext.destination);

oscillator.start();
```

### Exemplo 2: Distorção com Oversampling
```javascript
const audioContext = new (window.AudioContext || window.webkitAudioContext)();
const waveShaper = audioContext.createWaveShaper();

// Curva de distorção personalizada
const curve = new Float32Array([-1, -0.5, 0, 0.5, 1]);
waveShaper.curve = curve;
waveShaper.oversample = '2x';

const oscillator = audioContext.createOscillator();
oscillator.connect(waveShaper);
waveShaper.connect(audioContext.destination);

oscillator.start();
```

## Explicação
Um erro comum ao trabalhar com o WaveShaperNode é não normalizar adequadamente os valores da curva. Os valores devem sempre estar entre -1 e 1. Outro ponto a ser observado é a escolha do oversampling, que pode impactar a qualidade do som. O uso de oversampling pode adicionar latência, mas melhora a suavidade da distorção.

Além disso, certifique-se de que o contexto de áudio esteja em execução antes de tentar reproduzir sons. Se o contexto estiver em estado suspenso, você deve chamar `audioContext.resume()`.

## Resumo em Uma Linha
O WaveShaperNode permite a manipulação precisa de formas de onda em aplicações de áudio web, possibilitando a criação de efeitos de distorção personalizados.