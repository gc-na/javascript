<!--
Meta Description: # OscillatorNode em JavaScript: Criando Sons com a Web Audio API ## Sinopse O `OscillatorNode` é uma interface da Web Audio API que permite gerar onda...
Meta Keywords: audioctx, audiocontext, oscillatornode, áudio, ser
-->

# OscillatorNode em JavaScript: Criando Sons com a Web Audio API

## Sinopse
O `OscillatorNode` é uma interface da Web Audio API que permite gerar ondas sonoras de diferentes formas, como senóides, quadradas, triangulares e dente de serra, facilitando a criação de áudio dinâmico e interativo em aplicações web.

## Documentação
O `OscillatorNode` é utilizado para produzir sinais de áudio oscilatórios. Ele é frequentemente utilizado em jogos, música e aplicações de áudio interativas. O node pode ser configurado para gerar diferentes tipos de formas de onda e frequências, permitindo uma ampla gama de possibilidades sonoras.

### Propósito
O principal propósito do `OscillatorNode` é gerar sons contínuos que podem ser manipulados em tempo real. Ele pode ser conectado a outros nodes de áudio para criar composições complexas.

### Uso
Para utilizar um `OscillatorNode`, você precisa de um contexto de áudio (`AudioContext`). A seguir está um exemplo básico de como criar um `OscillatorNode`.

```javascript
// Criação do contexto de áudio
const audioContext = new (window.AudioContext || window.webkitAudioContext)();

// Criação do OscillatorNode
const oscillator = audioContext.createOscillator();

// Configuração da forma de onda
oscillator.type = 'sine'; // 'sine', 'square', 'sawtooth', 'triangle'

// Configuração da frequência
oscillator.frequency.setValueAtTime(440, audioContext.currentTime); // A4

// Conexão ao destino de áudio (saída)
oscillator.connect(audioContext.destination);

// Início do oscilador
oscillator.start();
```

## Exemplos
### Exemplo 1: Oscilador de Onda Senoidal
```javascript
const audioCtx = new (window.AudioContext || window.webkitAudioContext)();
const sineOscillator = audioCtx.createOscillator();
sineOscillator.type = 'sine';
sineOscillator.frequency.setValueAtTime(440, audioCtx.currentTime);
sineOscillator.connect(audioCtx.destination);
sineOscillator.start();
```

### Exemplo 2: Oscilador de Onda Quadrada
```javascript
const audioCtx = new (window.AudioContext || window.webkitAudioContext)();
const squareOscillator = audioCtx.createOscillator();
squareOscillator.type = 'square';
squareOscillator.frequency.setValueAtTime(220, audioCtx.currentTime);
squareOscillator.connect(audioCtx.destination);
squareOscillator.start();
```

### Exemplo 3: Alterando a Frequência
```javascript
const audioCtx = new (window.AudioContext || window.webkitAudioContext)();
const triangleOscillator = audioCtx.createOscillator();
triangleOscillator.type = 'triangle';
triangleOscillator.frequency.setValueAtTime(330, audioCtx.currentTime);
triangleOscillator.connect(audioCtx.destination);
triangleOscillator.start();
setTimeout(() => {
    triangleOscillator.frequency.setValueAtTime(660, audioCtx.currentTime); // Mudando a frequência
}, 1000);
```

## Explicação
### Armadilhas Comuns
- **Contexto de Áudio**: Sempre verifique se o `AudioContext` está em um estado de execução. Se o contexto estiver em pausa, o som não será reproduzido.
- **Forma de Onda**: Escolher a forma de onda correta é fundamental para obter o som desejado. Teste diferentes tipos para entender suas características.
- **Frequência**: Frequências muito altas ou muito baixas podem não ser audíveis dependendo do hardware de saída.

### Notas Adicionais
- O `OscillatorNode` pode ser parado usando o método `stop()`, que deve ser chamado antes de o `AudioContext` ser encerrado.
- O `OscillatorNode` pode ser recriado a qualquer momento, mas certifique-se de que ele não esteja conectado antes de parar.

## Resumo em Uma Linha
O `OscillatorNode` da Web Audio API permite a geração de ondas sonoras de diferentes formas, proporcionando uma poderosa ferramenta para criar experiências de áudio dinâmicas em aplicações web.