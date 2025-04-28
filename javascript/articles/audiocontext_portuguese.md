<!--
Meta Description: # AudioContext em JavaScript: Manipulação de Áudio na Web ## Sinopse O `AudioContext` é uma interface fundamental da API Web Audio, que permite a cria...
Meta Keywords: audiocontext, áudio, oscillator, que, para
-->

# AudioContext em JavaScript: Manipulação de Áudio na Web

## Sinopse
O `AudioContext` é uma interface fundamental da API Web Audio, que permite a criação e manipulação de áudio em aplicações web, oferecendo recursos avançados como processamento em tempo real, efeitos sonoros e análise de áudio.

## Documentação
### O que é o AudioContext?
O `AudioContext` é um objeto que representa um ambiente de som e é a base para trabalhar com áudio na web. Ele permite que os desenvolvedores criem, manipulem e reproduzam áudio de maneira programática, utilizando recursos como fontes de áudio, filtros e efeitos.

### Como usar o AudioContext?
Para criar um novo `AudioContext`, você simplesmente instância a classe:

```javascript
const audioContext = new AudioContext();
```

Uma vez criado, você pode utilizar métodos e propriedades do `AudioContext` para criar fontes de áudio, conectar nós de áudio e controlar a reprodução.

### Principais Propriedades e Métodos
- **createBufferSource()**: cria uma fonte de áudio a partir de um buffer.
- **createGain()**: cria um nó de ganho para controlar o volume.
- **createAnalyser()**: cria um nó de análise para visualizar dados de áudio.
- **destination**: propriedade que retorna o nó de destino para o contexto de áudio.

## Exemplos
### Exemplo Básico de Criação de uma Fonte de Áudio
```javascript
const audioContext = new AudioContext();
const oscillator = audioContext.createOscillator();
oscillator.type = 'sine'; // Tipo de onda: 'sine', 'square', 'sawtooth', 'triangle'
oscillator.frequency.setValueAtTime(440, audioContext.currentTime); // A4
oscillator.connect(audioContext.destination);
oscillator.start();
oscillator.stop(audioContext.currentTime + 1); // Toca por 1 segundo
```

### Exemplo de Controle de Volume com GainNode
```javascript
const audioContext = new AudioContext();
const gainNode = audioContext.createGain();
gainNode.gain.setValueAtTime(0.5, audioContext.currentTime); // Volume a 50%

const oscillator = audioContext.createOscillator();
oscillator.connect(gainNode);
gainNode.connect(audioContext.destination);
oscillator.start();
oscillator.stop(audioContext.currentTime + 1);
```

## Explicação
### Armadilhas Comuns e Dicas
- **Autorização de Reprodução de Áudio**: Navegadores modernos exigem interação do usuário (como um clique) para iniciar a reprodução de áudio. Certifique-se de que qualquer chamada a métodos que reproduzam som esteja dentro de um evento de interação.
- **Gerenciamento de Recursos**: O `AudioContext` pode ser usado para gerenciar múltiplas fontes de áudio, mas é importante garantir que você está liberando recursos corretamente para evitar vazamentos de memória.
- **Compatibilidade de Navegadores**: Embora o `AudioContext` seja amplamente suportado, sempre verifique a compatibilidade com navegadores específicos e considere o tratamento de erros quando a API não estiver disponível.

## Resumo em Uma Linha
O `AudioContext` é uma interface da API Web Audio em JavaScript que permite a criação e manipulação avançada de áudio em aplicações web.