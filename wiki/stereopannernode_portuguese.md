<!--
Meta Description: # StereoPannerNode: Controle de Panorâmica em JavaScript ## Sinopse O StereoPannerNode é uma interface da Web Audio API que permite manipular a posiçã...
Meta Keywords: áudio, stereopannernode, que, para, posição
-->

# StereoPannerNode: Controle de Panorâmica em JavaScript

## Sinopse
O StereoPannerNode é uma interface da Web Audio API que permite manipular a posição de um som no espaço estéreo, proporcionando um controle de panorâmica preciso para aplicações de áudio em JavaScript.

## Documentação

### Propósito
O StereoPannerNode é utilizado para posicionar sons em um campo estéreo, permitindo que os desenvolvedores ajustem a percepção de direção dos sons em aplicações web. Ele é fundamental para criar experiências de áudio mais imersivas e realistas.

### Uso
O StereoPannerNode pode ser criado a partir de um contexto de áudio e é frequentemente utilizado em conjunto com outros nós da Web Audio API. O nó aceita um parâmetro que especifica a posição do som, onde -1 representa o canal esquerdo, 1 representa o canal direito e 0 representa o centro.

### Detalhes
- **Propriedades**:
  - `pan`: Um valor que varia de -1 a 1, representando a posição do som no campo estéreo.
  
- **Métodos**:
  - `connect(destinationNode)`: Conecta o StereoPannerNode a outro nó de áudio.
  - `disconnect(destinationNode)`: Desconecta o StereoPannerNode de um nó de áudio.

### Exemplo de Criação e Uso
```javascript
// Criando o contexto de áudio
const audioContext = new (window.AudioContext || window.webkitAudioContext)();

// Criando um StereoPannerNode
const panner = audioContext.createStereoPanner();

// Ajustando a posição do som
panner.pan.value = -1; // Som totalmente para a esquerda

// Criando uma fonte de áudio
const source = audioContext.createBufferSource();
// Aqui você deve carregar um buffer de áudio previamente

// Conectando os nós
source.connect(panner);
panner.connect(audioContext.destination);

// Iniciando a reprodução
source.start();
```

## Explicação
Ao utilizar o StereoPannerNode, é essencial lembrar que o valor da propriedade `pan` deve estar sempre dentro do intervalo de -1 a 1, caso contrário, isso poderá causar um erro. Além disso, a manipulação da panorâmica deve ser feita após a conexão do nó de áudio para garantir que as alterações sejam aplicadas corretamente.

### Armadilhas Comuns
- **Reproduzindo Sem Conectar**: Muitos desenvolvedores esquecem de conectar o StereoPannerNode ao destino final. Sem essa conexão, o áudio não será reproduzido.
- **Valores de Pan Fora do Intervalo**: Definir valores para `pan` fora do intervalo permitido resultará em erros silenciosos que podem ser difíceis de depurar.

## Resumo em Uma Frase
O StereoPannerNode permite o controle da posição de sons em um espaço estéreo, essencial para criar experiências de áudio dinâmicas em JavaScript.