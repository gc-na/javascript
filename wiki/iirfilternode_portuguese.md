<!--
Meta Description: # IIRFilterNode: O Filtro IIR em JavaScript para Processamento de Áudio ## Sinopse O `IIRFilterNode` é uma interface da Web Audio API que permite a im...
Meta Keywords: iirfilternode, const, audiocontext, áudio, feedforward
-->

# IIRFilterNode: O Filtro IIR em JavaScript para Processamento de Áudio

## Sinopse
O `IIRFilterNode` é uma interface da Web Audio API que permite a implementação de filtros digitais Infinite Impulse Response (IIR) para manipulação de áudio em aplicações JavaScript, possibilitando uma filtragem precisa e eficiente de sinais sonoros.

## Documentação

### O que é o IIRFilterNode?
O `IIRFilterNode` é utilizado para aplicar filtros IIR a um sinal de áudio. Ao contrário dos filtros FIR (Finite Impulse Response), os filtros IIR podem ter um número infinito de coeficientes de impulso, o que permite um design mais eficiente em termos de recursos computacionais. Com o `IIRFilterNode`, desenvolvedores podem criar efeitos de áudio complexos, como equalização e modulação.

### Como Usar o IIRFilterNode
Para usar o `IIRFilterNode`, você deve primeiro criar um contexto de áudio e, em seguida, instanciar o filtro com os coeficientes desejados:

```javascript
// Criação de um contexto de áudio
const audioContext = new AudioContext();

// Coeficientes do filtro (feedforward e feedback)
const feedforward = [1, -1];
const feedback = [1, -0.5];

// Criação do IIRFilterNode
const iirFilterNode = audioContext.createIIRFilter(feedforward, feedback);

// Conectando o nó a um fonte de áudio
const source = audioContext.createBufferSource();
// (O buffer de áudio deve ser carregado antes)
source.connect(iirFilterNode);
iirFilterNode.connect(audioContext.destination);

// Início da reprodução
source.start();
```

### Detalhes do IIRFilterNode
- **Propriedades**: O `IIRFilterNode` não possui propriedades acessíveis diretamente, mas suas entradas e saídas podem ser manipuladas via conexões no contexto de áudio.
- **Métodos**: O principal método é `createIIRFilter(feedforward, feedback)`, onde `feedforward` e `feedback` são arrays que definem os coeficientes do filtro.

## Exemplos

### Exemplo 1: Filtro passa-baixa
```javascript
const audioContext = new AudioContext();
const feedforward = [0.5]; // Coeficientes feedforward
const feedback = [1, -0.5]; // Coeficientes feedback

const lowPassFilter = audioContext.createIIRFilter(feedforward, feedback);
```

### Exemplo 2: Usando um IIRFilterNode em um fluxo de áudio
```javascript
const audioContext = new AudioContext();
const source = audioContext.createBufferSource();
// (Carregar o buffer aqui)

const feedforward = [0.1, 0.2, 0.3]; 
const feedback = [1, -0.7]; 

const filterNode = audioContext.createIIRFilter(feedforward, feedback);
source.connect(filterNode);
filterNode.connect(audioContext.destination);
source.start();
```

## Explicação
Uma armadilha comum ao trabalhar com `IIRFilterNode` é a escolha inadequada dos coeficientes, que pode resultar em um som indesejado ou em instabilidades no sinal. É crucial entender como os coeficientes de feedforward e feedback interagem para evitar distorções.

Além disso, é importante lembrar que o `IIRFilterNode` é uma interface de baixo nível. Portanto, para usuários que não estão familiarizados com teoria de filtros, pode ser desafiador alcançar resultados desejáveis sem um entendimento sólido sobre a manipulação de sinais de áudio.

## Resumo em Uma Linha
O `IIRFilterNode` é uma interface poderosa na Web Audio API para aplicar filtros IIR em áudio usando JavaScript, permitindo a criação de efeitos sonoros sofisticados.