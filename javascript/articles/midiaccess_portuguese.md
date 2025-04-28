<!--
Meta Description: # Acesso MIDI em JavaScript: Como Usar a API Web MIDI ## Sinopse O `MIDIAccess` é uma interface da API Web MIDI que permite o acesso a dispositivos MI...
Meta Keywords: midi, dispositivos, midiaccess, que, uma
-->

# Acesso MIDI em JavaScript: Como Usar a API Web MIDI

## Sinopse
O `MIDIAccess` é uma interface da API Web MIDI que permite o acesso a dispositivos MIDI conectados ao computador através do navegador, possibilitando a comunicação e controle de instrumentos musicais digitais.

## Documentação
O `MIDIAccess` é uma interface que fornece uma forma de interagir com todos os dispositivos MIDI disponíveis no sistema. Essa API é útil para desenvolvedores que desejam criar aplicações web que envolvam a manipulação de dispositivos MIDI, como teclados, controladores e sintetizadores.

### Propósito
O principal objetivo do `MIDIAccess` é facilitar a integração de dispositivos MIDI em aplicações web, permitindo que desenvolvedores possam enviar e receber mensagens MIDI de forma simples e eficaz.

### Uso
Para acessar os dispositivos MIDI, você deve utilizar o método `navigator.requestMIDIAccess()`, que retorna uma promessa que resolve para um objeto `MIDIAccess`.

```javascript
navigator.requestMIDIAccess()
  .then(onMIDISuccess, onMIDIFailure);

function onMIDISuccess(midiAccess) {
  console.log('MIDI Access Success:', midiAccess);
}

function onMIDIFailure() {
  console.error('Failed to access MIDI devices.');
}
```

### Detalhes
- O objeto `MIDIAccess` contém métodos e propriedades para listar e gerenciar dispositivos MIDI.
- `inputs` e `outputs` são coleções de dispositivos MIDI conectados.
- Você pode escutar eventos de conexão e desconexão de dispositivos utilizando event listeners.

## Exemplos

### Exemplo Básico de Acesso a Dispositivos MIDI
```javascript
navigator.requestMIDIAccess()
  .then(midiAccess => {
    const inputs = midiAccess.inputs;
    inputs.forEach(input => {
      console.log(`Dispositivo MIDI Conectado: ${input.name}`);
    });
  })
  .catch(err => {
    console.error('Erro ao acessar dispositivos MIDI:', err);
  });
```

### Enviando Mensagens MIDI
```javascript
navigator.requestMIDIAccess().then(midiAccess => {
  const outputs = midiAccess.outputs;
  outputs.forEach(output => {
    // Envia uma nota MIDI (Nota 60, Velocidade 127)
    output.send([0x90, 60, 127]); // Nota On
    output.send([0x80, 60, 0]);   // Nota Off
  });
});
```

## Explicação
Alguns dos desafios comuns ao trabalhar com `MIDIAccess` incluem:
- **Compatibilidade do Navegador:** A API Web MIDI não é suportada por todos os navegadores. Verifique a compatibilidade antes de implementar.
- **Permissões do Usuário:** O acesso às interfaces MIDI requer permissões do usuário. Assegure-se de tratar o caso em que o usuário nega a permissão.
- **Dispositivos Desconectados:** Ao tentar acessar dispositivos, esteja preparado para lidar com a ausência de dispositivos MIDI conectados.

## Resumo em Uma Linha
O `MIDIAccess` em JavaScript permite o acesso e controle de dispositivos MIDI conectados ao navegador, facilitando a criação de aplicações musicais interativas.