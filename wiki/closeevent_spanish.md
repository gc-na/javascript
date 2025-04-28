<!--
Meta Description: # CloseEvent en JavaScript: Manejo de Eventos de Cierre en Aplicaciones Web ## Sinopsis CloseEvent es un objeto en JavaScript que se utiliza para repr...
Meta Keywords: websocket, cierre, conexión, event, closeevent
-->

# CloseEvent en JavaScript: Manejo de Eventos de Cierre en Aplicaciones Web

## Sinopsis
CloseEvent es un objeto en JavaScript que se utiliza para representar el evento de cierre de una ventana o un canal de comunicación, como WebSocket, en aplicaciones web. Este evento es crucial para gestionar la finalización de conexiones y para realizar tareas de limpieza o de notificación al usuario.

## Documentación
El objeto CloseEvent se activa cuando una conexión, como un WebSocket, se cierra o se finaliza. Proporciona información importante sobre el motivo del cierre y el estado de la conexión.

### Propósito
CloseEvent se utiliza principalmente en aplicaciones que requieren comunicaciones en tiempo real, como chats o aplicaciones de colaboración. Permite a los desarrolladores manejar situaciones en las que la conexión se cierra de forma intencionada o inesperada.

### Uso
Para trabajar con CloseEvent, se debe añadir un listener al WebSocket utilizando el evento `close`. El objeto CloseEvent proporciona los siguientes atributos:

- `code`: Un número que indica el código de cierre de la conexión.
- `reason`: Una cadena que proporciona una descripción opcional del motivo por el que se cerró la conexión.
- `wasClean`: Un booleano que indica si el cierre fue limpio (`true`) o no (`false`).

### Sintaxis
```javascript
websocket.addEventListener('close', function(event) {
    console.log('Conexión cerrada:', event.code, event.reason, event.wasClean);
});
```

## Ejemplos

### Ejemplo Básico de Uso
```javascript
const websocket = new WebSocket('wss://example.com/socket');

websocket.addEventListener('open', function() {
    console.log('Conexión abierta');
});

websocket.addEventListener('close', function(event) {
    console.log('Conexión cerrada con código:', event.code);
    console.log('Razón del cierre:', event.reason);
    console.log('¿Cierre limpio?', event.wasClean);
});
```

### Ejemplo con Manejo de Reconexión
```javascript
function connectWebSocket() {
    const websocket = new WebSocket('wss://example.com/socket');

    websocket.addEventListener('close', function(event) {
        console.log('Conexión cerrada. Intentando reconectar...');
        setTimeout(connectWebSocket, 3000); // Reintentar la conexión después de 3 segundos
    });
}

connectWebSocket();
```

## Explicación
Al trabajar con CloseEvent, es importante tener en cuenta algunos aspectos:

- **Códigos de Cierre**: Los códigos de cierre son estandarizados y pueden variar. Es recomendable revisar la documentación de WebSocket para entender qué significan cada uno.
- **Limpieza**: Realizar tareas de limpieza al cerrar conexiones es crucial para evitar fugas de memoria o comportamientos inesperados.
- **Conexiones Inesperadas**: Un cierre inesperado puede ocurrir por problemas de red o en el servidor. Implementar un sistema de reconexión puede mejorar la experiencia del usuario.

## Resumen en Una Línea
CloseEvent en JavaScript facilita el manejo de eventos de cierre en conexiones, permitiendo la gestión adecuada de la finalización de comunicaciones en aplicaciones web.