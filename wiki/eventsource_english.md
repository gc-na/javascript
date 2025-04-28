<!--
Meta Description: # EventSource in JavaScript: Real-Time Server-Sent Events (SSE) Made Easy ## Synopsis EventSource is a JavaScript API that enables web applications to...
Meta Keywords: eventsource, server, event, events, data
-->

# EventSource in JavaScript: Real-Time Server-Sent Events (SSE) Made Easy

## Synopsis
EventSource is a JavaScript API that enables web applications to receive real-time updates from a server through Server-Sent Events (SSE). This allows for efficient one-way communication from the server to the client, making it ideal for applications that require live data streaming.

## Documentation

### Purpose
The EventSource interface is designed to facilitate the reception of server-sent events in a web application. Unlike WebSockets, which allow for full-duplex communication, EventSource is optimized for unidirectional data flow from the server to the client, making it a simpler choice for scenarios where clients only need to receive updates.

### Usage
To use EventSource, you create a new instance by passing the URL of the server endpoint that will send the events. The server must set the appropriate headers to indicate that the data being sent is of the type "text/event-stream".

```javascript
const eventSource = new EventSource('https://example.com/events');

eventSource.onmessage = function(event) {
    console.log('New message: ', event.data);
};

eventSource.onerror = function(event) {
    console.error('EventSource failed: ', event);
};
```

### Details
- **Constructor**: `EventSource(url, [eventSourceInit])`
  - `url`: The URL of the server endpoint that sends events.
  - `[eventSourceInit]`: An optional object that can contain additional settings such as `withCredentials`.

- **Properties**:
  - `readyState`: Reflects the current state of the connection. Possible values include:
    - `0`: CONNECTING
    - `1`: OPEN
    - `2`: CLOSED

- **Methods**:
  - `close()`: Closes the connection to the server.

- **Events**:
  - `onmessage`: Fired when a new message is received.
  - `onerror`: Fired when an error occurs.

## Examples

### Basic Example
```javascript
const eventSource = new EventSource('https://example.com/events');

eventSource.onmessage = function(event) {
    document.body.innerHTML += `<p>${event.data}</p>`;
};

eventSource.onerror = function() {
    console.error('Connection error');
};
```

### Handling Different Event Types
You can also handle custom event types sent by the server using the `addEventListener` method.

```javascript
const eventSource = new EventSource('https://example.com/events');

eventSource.addEventListener('customEvent', function(event) {
    console.log('Custom event data:', event.data);
});
```

## Explanation
While using EventSource, there are a few common pitfalls to keep in mind:

- **CORS Issues**: If you're making requests to a different origin, ensure that the server sends the correct CORS headers (`Access-Control-Allow-Origin`).
- **Connection Limitations**: Browsers may limit the number of concurrent connections to a single server, which can affect applications that open multiple EventSource instances.
- **Reconnection Logic**: EventSource automatically attempts to reconnect if the connection closes unexpectedly. However, it does not provide a way to control this behavior directly.

## One Line Summary
EventSource in JavaScript is a simple API for receiving real-time updates from a server using Server-Sent Events, making live data streaming straightforward and efficient.