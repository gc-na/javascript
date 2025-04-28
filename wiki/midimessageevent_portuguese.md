<!--
Meta Description: # MIDIMessageEvent em JavaScript: Entendendo e Utilizando Eventos MIDI ## Sinopse O `MIDIMessageEvent` é um evento utilizado em JavaScript para manipu...
Meta Keywords: midi, que, midimessageevent, mensagem, mensagens
-->

# MIDIMessageEvent em JavaScript: Entendendo e Utilizando Eventos MIDI

## Sinopse
O `MIDIMessageEvent` é um evento utilizado em JavaScript para manipular mensagens MIDI (Musical Instrument Digital Interface) em aplicações web, permitindo que desenvolvedores interajam com dispositivos MIDI de forma eficiente.

## Documentação
O `MIDIMessageEvent` é um objeto que representa uma mensagem MIDI recebida de um dispositivo MIDI. Esse evento é parte da Web MIDI API, que facilita a comunicação entre navegadores e dispositivos MIDI.

### Propósito
O principal objetivo do `MIDIMessageEvent` é fornecer uma maneira de capturar e processar mensagens MIDI, que podem incluir informações sobre notas, controle de parâmetros e outros dados musicais.

### Uso
Para utilizar o `MIDIMessageEvent`, é necessário que a Web MIDI API esteja disponível no navegador. As mensagens MIDI podem ser recebidas através de um `MIDIInput` e, ao receber uma mensagem, um evento do tipo `MIDIMessageEvent` é disparado.

### Detalhes
- **Propriedades**:
  - `data`: Um objeto `Uint8Array` que contém os bytes da mensagem MIDI.
  - `timeStamp`: Um timestamp em milissegundos que indica o momento em que a mensagem foi recebida.

- **Método de Criação**: O evento é gerado automaticamente pelo sistema quando uma mensagem MIDI é recebida.

## Exemplo
Aqui está um exemplo básico de como utilizar o `MIDIMessageEvent` em uma aplicação JavaScript:

```javascript
// Verifica se a Web MIDI API está suportada
if (navigator.requestMIDIAccess) {
    navigator.requestMIDIAccess().then(onMIDISuccess, onMIDIFailure);
}

// Função chamada quando o acesso MIDI é bem-sucedido
function onMIDISuccess(midiAccess) {
    const inputs = midiAccess.inputs;
    inputs.forEach(input => {
        input.onmidimessage = handleMIDIMessage;
    });
}

// Função que lida com a mensagem MIDI recebida
function handleMIDIMessage(event) {
    const message = event.data; // Obtemos os dados da mensagem
    const time = event.timeStamp; // Obtemos o timestamp

    console.log(`Mensagem MIDI recebida: ${message}, Timestamp: ${time}`);
}

// Função chamada quando o acesso MIDI falha
function onMIDIFailure() {
    console.error("Erro ao acessar dispositivos MIDI.");
}
```

## Explicação
- **Cuidados Comuns**: Um dos principais cuidados ao trabalhar com `MIDIMessageEvent` é garantir que a Web MIDI API esteja suportada no navegador em uso, uma vez que nem todos os navegadores oferecem suporte a essa API.

- **Mensagens MIDI**: As mensagens podem incluir diferentes tipos de informações, como notas de teclado ou mensagens de controle. É importante entender a estrutura das mensagens MIDI para manipulá-las adequadamente.

- **Objetos Uint8Array**: O `data` do `MIDIMessageEvent` é armazenado em um `Uint8Array`, que pode ser manipulado como um array de bytes. Este aspecto é crucial para a interpretação correta da mensagem.

## Resumo em Uma Linha
O `MIDIMessageEvent` é uma interface da Web MIDI API que permite capturar e processar mensagens MIDI recebidas em aplicações JavaScript.