<!--
Meta Description: # DelayNode em JavaScript: Controle de Tempo na Manipulação de Áudio ## Sinopse O DelayNode é uma interface da Web Audio API que permite adicionar um ...
Meta Keywords: delaynode, áudio, que, atraso, audiocontext
-->

# DelayNode em JavaScript: Controle de Tempo na Manipulação de Áudio

## Sinopse
O DelayNode é uma interface da Web Audio API que permite adicionar um efeito de delay (atraso) a um sinal de áudio. Ele é amplamente utilizado para criar efeitos sonoros interessantes e para controlar a reprodução de áudio em aplicações web.

## Documentação
O DelayNode é parte do contexto de áudio da Web Audio API e serve para atrasar a reprodução de um sinal de áudio por um período específico. Ele pode ser utilizado para criar efeitos de eco, repetir sons ou simplesmente para sincronizar diferentes fontes de áudio.

### Propósito
O principal objetivo do DelayNode é manipular o tempo de reprodução de um sinal de áudio, permitindo que os desenvolvedores criem experiências sonoras mais dinâmicas e interativas.

### Uso
Para utilizar um DelayNode, é necessário seguir os seguintes passos básicos:

1. Criar um contexto de áudio.
2. Criar uma instância de DelayNode.
3. Conectar o DelayNode à fonte de áudio e ao destino (geralmente os alto-falantes).
4. Definir o tempo de atraso em segundos.

### Detalhes
- **Propriedades**:
  - `delayTime`: Um `AudioParam` que define o tempo de atraso em segundos.
- **Métodos**:
  - `connect(destinationNode)`: Conecta o DelayNode a outro nó de áudio.
  - `disconnect()`: Desconecta o DelayNode de um nó de áudio.

## Exemplos

### Exemplo Básico de Uso
```javascript
// Criando um contexto de áudio
const audioContext = new (window.AudioContext || window.webkitAudioContext)();

// Criando um DelayNode
const delayNode = audioContext.createDelay(5.0); // Delay máximo de 5 segundos

// Definindo o tempo de atraso
delayNode.delayTime.value = 1.0; // 1 segundo de atraso

// Criando uma fonte de áudio (exemplo com um oscilador)
const oscillator = audioContext.createOscillator();
oscillator.frequency.setValueAtTime(440, audioContext.currentTime); // Frequência de 440Hz

// Conectando os nós
oscillator.connect(delayNode);
delayNode.connect(audioContext.destination);

// Iniciando a reprodução
oscillator.start();
```

### Exemplo com Efeito de Eco
```javascript
// Continuando do exemplo anterior

// Definindo um segundo DelayNode para criar um efeito de eco
const echoNode = audioContext.createDelay(2.0);
echoNode.delayTime.value = 0.5; // 0.5 segundos de atraso

// Conectando o primeiro DelayNode ao segundo
delayNode.connect(echoNode);
echoNode.connect(audioContext.destination);

// Iniciando a reprodução
oscillator.start();
```

## Explicação
Um dos erros mais comuns ao trabalhar com o DelayNode é não entender como o tempo de atraso afeta a sincronização dos sons. É essencial ajustar o `delayTime` de acordo com o que se deseja alcançar. Além disso, lembre-se de que o valor do `delayTime` deve ser maior que zero, caso contrário, o áudio não será reproduzido com o atraso esperado.

Outro ponto importante é a gestão de recursos. Ao criar muitos DelayNodes, pode ocorrer um aumento significativo no uso de CPU, o que pode afetar o desempenho da aplicação. Portanto, use-os com moderação.

## Resumo em Uma Frase
O DelayNode é uma ferramenta poderosa da Web Audio API que permite aos desenvolvedores manipular o tempo de reprodução de áudio, criando efeitos sonoros complexos e dinâmicos.