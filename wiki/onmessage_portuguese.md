<!--
Meta Description: # onmessage: Entendendo o Evento de Mensagem em JavaScript ## Sinopse O `onmessage` é um evento essencial em JavaScript usado para comunicação entre t...
Meta Keywords: que, worker, onmessage, mensagem, event
-->

# onmessage: Entendendo o Evento de Mensagem em JavaScript

## Sinopse
O `onmessage` é um evento essencial em JavaScript usado para comunicação entre threads, especialmente em Web Workers e objetos `MessagePort`. Este evento permite que scripts recebam mensagens de outras partes da aplicação, facilitando a troca de dados de forma assíncrona.

## Documentação

### Propósito
O evento `onmessage` é acionado quando uma mensagem é recebida por um objeto que escuta o retorno de dados, como um Web Worker ou um objeto `MessagePort`. Ele é crucial para implementar a comunicação entre diferentes contextos de execução, permitindo que informações sejam enviadas e recebidas de maneira eficiente e não bloqueante.

### Uso
Para utilizar o `onmessage`, você deve definir uma função que será chamada quando uma mensagem for recebida. Essa função recebe um objeto `MessageEvent`, que contém informações sobre a mensagem recebida.

### Sintaxe
```javascript
worker.onmessage = function(event) {
    // Lógica a ser executada ao receber a mensagem
    console.log(event.data); // Exibe os dados da mensagem
};
```

## Exemplos

### Exemplo Básico com Web Worker
```javascript
// worker.js
self.onmessage = function(event) {
    const result = event.data * 2; // Multiplica a mensagem recebida por 2
    self.postMessage(result); // Envia o resultado de volta
};

// script principal
const worker = new Worker('worker.js');
worker.onmessage = function(event) {
    console.log('Resultado do Worker:', event.data); // Exibe o resultado recebido
};

worker.postMessage(5); // Envia o valor 5 para o Worker
```

### Exemplo com MessagePort
```javascript
const { port1, port2 } = new MessageChannel();

port1.onmessage = function(event) {
    console.log('Mensagem recebida na porta 1:', event.data);
};

port2.postMessage('Olá Porta 1!'); // Envia mensagem para porta 1
```

## Explicação
Um dos principais desafios ao trabalhar com `onmessage` é garantir que a comunicação entre diferentes contextos (como um Worker e o script principal) seja realizada corretamente. Além disso, é importante lembrar que as mensagens enviadas e recebidas são clonadas, o que significa que objetos complexos podem não ser passados como referência. 

### Pontos a Considerar
- **Clonagem de Mensagens**: Objetos enviados por `postMessage` são copiados, não referenciados. Isso pode causar comportamento inesperado se você esperar que uma alteração em um objeto afete outra parte do código.
- **Erro de Contexto**: Certifique-se de que o código que manipula `onmessage` esteja sempre acessível e não seja afetado por erros de escopo ou contexto.

## Resumo em Uma Linha
O `onmessage` em JavaScript é um evento que permite a comunicação assíncrona entre diferentes contextos de execução, como Web Workers e MessagePorts.