<!--
Meta Description: # Understanding the `onclose` Event in JavaScript: A Comprehensive Guide ## Synopsis The `onclose` event in JavaScript is an essential feature for man...
Meta Keywords: event, connection, onclose, socket, websocket
-->

# Understanding the `onclose` Event in JavaScript: A Comprehensive Guide

## Synopsis
The `onclose` event in JavaScript is an essential feature for managing WebSocket connections. It is triggered when a WebSocket connection is closed, allowing developers to execute specific actions in response to the closure.

## Documentation
### Purpose
The `onclose` event handler is designed to monitor the lifecycle of a WebSocket connection. It provides a way to handle cleanup tasks, user notifications, or any necessary state updates when a connection is no longer active.

### Usage
To use the `onclose` event, you need to create a WebSocket instance and define the `onclose` property as a function that will be called automatically when the connection closes. 

### Syntax
```javascript
const socket = new WebSocket('ws://example.com');

socket.onclose = function(event) {
    // Your code to handle the close event
};
```

### Event Object
The `event` object passed to the `onclose` handler contains useful properties:
- **`code`**: A numeric value indicating the status code explaining why the connection was closed.
- **`reason`**: A string explaining the reason for closure (if provided).
- **`wasClean`**: A boolean indicating whether the connection was closed cleanly.

## Examples
### Basic Example of `onclose`
```javascript
const socket = new WebSocket('ws://example.com');

socket.onopen = function() {
    console.log('Connection opened');
};

socket.onclose = function(event) {
    console.log('Connection closed:', event.code, event.reason);
};

// Simulate closing the socket
socket.close(1000, 'Done');
```

### Handling Connection Closure with a Retry Mechanism
```javascript
let retryInterval;

const connect = () => {
    const socket = new WebSocket('ws://example.com');

    socket.onopen = function() {
        console.log('Connection established');
        clearInterval(retryInterval); // Stop retrying if connection is successful
    };

    socket.onclose = function(event) {
        console.log('Connection closed:', event.code, event.reason);
        retryInterval = setInterval(connect, 5000); // Retry every 5 seconds
    };
};

connect(); // Initial connection attempt
```

## Explanation
### Common Pitfalls
- **Not Handling Closure Properly**: Failing to define an `onclose` handler can lead to unhandled scenarios when the connection drops unexpectedly.
- **Assuming Immediate Reconnection**: It’s essential to implement backoff strategies when attempting to reconnect, as immediate retries can overwhelm the server.
- **Ignoring Event Properties**: Not utilizing the `event` object’s properties can lead to a lack of understanding of why the connection was closed.

### Additional Notes
- The `onclose` event is particularly useful in applications that require real-time data updates, such as chat applications or live notifications.
- Always check the `wasClean` property before attempting to reconnect to differentiate between intentional closures and errors.

## One Line Summary
The `onclose` event in JavaScript allows developers to handle the closure of WebSocket connections efficiently, enabling responsive and robust applications.