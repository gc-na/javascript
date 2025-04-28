<!--
Meta Description: # WebSocket in JavaScript: Real-Time Communication Made Easy ## Synopsis WebSocket is a protocol that enables full-duplex communication channels over ...
Meta Keywords: websocket, socket, connection, data, server
-->

# WebSocket in JavaScript: Real-Time Communication Made Easy

## Synopsis
WebSocket is a protocol that enables full-duplex communication channels over a single TCP connection, allowing for real-time data exchange between clients and servers in JavaScript applications.

## Documentation

### Purpose
WebSocket provides a way to establish a persistent connection between a client (typically a web browser) and a server. This connection allows for asynchronous data transfer, making it ideal for applications requiring real-time updates, such as chat applications, online gaming, and live sports updates.

### Usage
To use WebSocket in JavaScript, you create a new instance of the `WebSocket` class, specifying the URL of the server you want to connect to. The protocol automatically handles opening and closing connections, as well as sending and receiving messages.

#### Basic Syntax
```javascript
const socket = new WebSocket('ws://example.com/socket');
```

### Events
WebSocket supports several events that you can listen to:
- `onopen`: Fired when the connection is successfully established.
- `onmessage`: Fired when a message is received from the server.
- `onerror`: Fired when there is an error with the connection.
- `onclose`: Fired when the connection is closed.

### Methods
- `send(data)`: Sends data to the server.
- `close()`: Closes the WebSocket connection.

## Examples

### Example 1: Basic WebSocket Connection
```javascript
const socket = new WebSocket('ws://example.com/socket');

socket.onopen = function() {
    console.log('WebSocket connection established');
    socket.send('Hello Server!');
};

socket.onmessage = function(event) {
    console.log('Message from server: ', event.data);
};

socket.onerror = function(error) {
    console.error('WebSocket Error: ', error);
};

socket.onclose = function() {
    console.log('WebSocket connection closed');
};
```

### Example 2: Sending JSON Data
```javascript
const socket = new WebSocket('ws://example.com/socket');

socket.onopen = function() {
    const data = { action: 'subscribe', channel: 'updates' };
    socket.send(JSON.stringify(data));
};
```

## Explanation
When using WebSocket, it's essential to be aware of certain common pitfalls:

- **Connection Limitations**: Ensure that your server can handle multiple WebSocket connections simultaneously. If too many connections are opened, it may lead to performance issues.
  
- **Cross-Origin Restrictions**: WebSocket connections may be subject to same-origin policy restrictions. Ensure that the server's CORS settings allow connections from your domain.
  
- **Error Handling**: Always implement error handling using the `onerror` event. This ensures that you can gracefully handle issues like network interruptions.

- **Closing Connections**: It is good practice to close the WebSocket connection when it's no longer needed to free up resources.

## One Line Summary
WebSocket in JavaScript enables real-time, full-duplex communication between clients and servers, making it essential for modern web applications requiring instant data updates.