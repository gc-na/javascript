<!--
Meta Description: # WebSocket em JavaScript: Conexões em Tempo Real na Web ## Sinopse WebSocket é uma tecnologia que permite a comunicação bidirecional em tempo real en...
Meta Keywords: websocket, socket, uma, servidor, conexão
-->

# WebSocket em JavaScript: Conexões em Tempo Real na Web

## Sinopse
WebSocket é uma tecnologia que permite a comunicação bidirecional em tempo real entre um cliente e um servidor, oferecendo uma alternativa eficiente ao modelo tradicional de requisições HTTP.

## Documentação
O WebSocket é uma API que permite a criação de conexões persistentes entre o navegador e o servidor. Essa tecnologia é ideal para aplicações que requerem atualizações em tempo real, como chats, jogos online e serviços de notificações.

### Propósito
O principal objetivo do WebSocket é permitir uma comunicação contínua e de baixa latência, onde o servidor pode enviar dados para o cliente assim que eles estiverem disponíveis, sem a necessidade de o cliente solicitar por novos dados repetidamente.

### Uso
Para utilizar o WebSocket em JavaScript, siga os passos abaixo:

1. **Criar uma nova instância de WebSocket**:
   ```javascript
   const socket = new WebSocket('ws://exemplo.com/socket');
   ```

2. **Definir manipuladores de eventos**:
   - `onopen`: Executado quando a conexão é estabelecida.
   - `onmessage`: Executado quando uma mensagem é recebida do servidor.
   - `onerror`: Executado em caso de erro na conexão.
   - `onclose`: Executado quando a conexão é fechada.

3. **Enviar mensagens para o servidor**:
   ```javascript
   socket.send('Olá, servidor!');
   ```

### Detalhes
O WebSocket utiliza a porta 80 (ou 443 para conexões seguras) e estabelece uma conexão através do protocolo HTTP. Após a conexão ser estabelecida, ela é promovida para o protocolo WebSocket, permitindo comunicação contínua.

## Exemplos

### Exemplo Básico de Conexão WebSocket
```javascript
const socket = new WebSocket('ws://exemplo.com/socket');

socket.onopen = function(event) {
    console.log('Conexão estabelecida!');
    socket.send('Olá, servidor!');
};

socket.onmessage = function(event) {
    console.log('Mensagem recebida do servidor: ', event.data);
};

socket.onerror = function(error) {
    console.error('Erro na conexão WebSocket: ', error);
};

socket.onclose = function(event) {
    console.log('Conexão fechada: ', event);
};
```

### Enviando e Recebendo Mensagens
```javascript
const socket = new WebSocket('ws://exemplo.com/socket');

socket.onopen = function() {
    socket.send('Mensagem inicial');
};

socket.onmessage = function(event) {
    console.log('Nova mensagem: ', event.data);
    if (event.data === 'Fechar conexão') {
        socket.close();
    }
};
```

## Explicação
Embora o WebSocket seja uma ferramenta poderosa, existem algumas desvantagens e armadilhas a serem consideradas:

- **Compatibilidade**: Embora a maioria dos navegadores modernos suporte WebSockets, é importante verificar a compatibilidade se você estiver desenvolvendo para navegadores mais antigos.
- **Conexões perdidas**: Conexões WebSocket podem ser interrompidas por várias razões, como perda de internet ou problemas no servidor. É recomendável implementar uma lógica de reconexão automática.
- **Segurança**: Sempre use `wss://` em vez de `ws://` quando trabalhar com dados sensíveis, pois isso garante que a comunicação seja criptografada.

## Resumo em Uma Linha
WebSocket é uma API JavaScript que permite comunicação bidirecional em tempo real entre cliente e servidor, ideal para aplicações que exigem atualizações instantâneas.