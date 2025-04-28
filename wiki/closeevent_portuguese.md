<!--
Meta Description: # CloseEvent em JavaScript: Entenda Como Funciona ## Sinopse O `CloseEvent` é um objeto em JavaScript que representa um evento de fechamento, frequent...
Meta Keywords: fechamento, conexão, que, com, event
-->

# CloseEvent em JavaScript: Entenda Como Funciona

## Sinopse
O `CloseEvent` é um objeto em JavaScript que representa um evento de fechamento, frequentemente utilizado em aplicações web que interagem com WebSockets ou outras conexões que podem ser fechadas.

## Documentação
O `CloseEvent` é um dos eventos que podem ser disparados em um contexto de WebSockets. Ele fornece informações sobre o fechamento de uma conexão, como o código de status e uma razão para o fechamento. O evento é essencial para tratar situações em que a comunicação com o servidor é interrompida.

### Propriedades do CloseEvent
- **code**: Um número que representa o código de status do fechamento da conexão. Por exemplo, 1000 indica que a conexão foi fechada normalmente.
- **reason**: Uma string que fornece a razão para o fechamento, se disponível.
- **wasClean**: Um booleano que indica se a conexão foi fechada de maneira limpa (true) ou não (false).

### Uso
O `CloseEvent` é utilizado em conjunto com o objeto `WebSocket`. Quando uma conexão WebSocket é fechada, um evento `close` é disparado, e o `CloseEvent` é passado como argumento para o manipulador desse evento.

```javascript
const socket = new WebSocket('ws://example.com');

socket.addEventListener('close', function(event) {
    console.log('Conexão fechada:');
    console.log('Código:', event.code);
    console.log('Razão:', event.reason);
    console.log('Fechamento limpo:', event.wasClean);
});
```

## Exemplos
### Exemplo Básico de Uso do CloseEvent
```javascript
const socket = new WebSocket('ws://example.com');

socket.addEventListener('close', function(event) {
    console.log(`A conexão foi fechada com código: ${event.code}`);
    if (!event.wasClean) {
        console.log('O fechamento não foi limpo.');
    }
});
```

### Exemplo com Razão do Fechamento
```javascript
const socket = new WebSocket('ws://example.com');

socket.addEventListener('close', function(event) {
    console.log(`Conexão fechada: ${event.reason}`);
    if (event.wasClean) {
        console.log('Conexão fechada de forma limpa.');
    } else {
        console.log('Conexão fechada de forma não limpa.');
    }
});
```

## Explicação
Ao trabalhar com `WebSocket`, é importante entender o comportamento do `CloseEvent`. Um erro comum é não verificar o estado da conexão antes de realizar operações adicionais após o fechamento. Além disso, é crucial lidar adequadamente com o fechamento não limpo, que pode indicar problemas na rede ou no servidor.

Outro ponto a se atentar é que algumas razões de fechamento podem não ser informadas se o fechamento ocorrer por motivos inesperados. Portanto, é sempre uma boa prática registrar o código e a razão para ajudar na depuração de problemas.

## Resumo em Uma Linha
O `CloseEvent` em JavaScript representa o evento de fechamento de uma conexão WebSocket, fornecendo informações sobre o código de status, razão e se o fechamento foi limpo.