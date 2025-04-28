<!--
Meta Description: # EventSource en JavaScript: Conexiones en Tiempo Real a través de SSE ## Sinopsis `EventSource` es una interfaz de JavaScript que permite la recepció...
Meta Keywords: eventsource, servidor, para, conexión, una
-->

# EventSource en JavaScript: Conexiones en Tiempo Real a través de SSE

## Sinopsis
`EventSource` es una interfaz de JavaScript que permite la recepción de eventos enviados por un servidor utilizando la tecnología Server-Sent Events (SSE). Es ideal para aplicaciones que requieren actualizaciones en tiempo real, como notificaciones o actualizaciones de contenido.

## Documentación
### Propósito
`EventSource` se utiliza para abrir una conexión persistente con un servidor, permitiendo recibir datos de forma unidireccional desde el servidor hacia el cliente. A diferencia de WebSockets, `EventSource` es más sencillo y está diseñado específicamente para recibir mensajes desde el servidor.

### Uso
Para utilizar `EventSource`, se crea una nueva instancia pasando la URL del endpoint que proporcionará los eventos. Una vez creada la conexión, se pueden manejar distintos tipos de eventos.

#### Sintaxis
```javascript
const eventSource = new EventSource(url);
```

#### Propiedades y Métodos
- **onmessage**: Función que se ejecuta cuando se recibe un mensaje del servidor.
- **onerror**: Función que se ejecuta si ocurre un error en la conexión.
- **addEventListener(event, listener)**: Permite agregar un manejador para eventos específicos.
- **close()**: Cierra la conexión con el servidor.

### Ejemplo
A continuación se presenta un ejemplo básico de cómo utilizar `EventSource` para recibir mensajes de un servidor.

```javascript
const eventSource = new EventSource('https://mi-servidor.com/eventos');

eventSource.onmessage = function(event) {
    console.log('Mensaje recibido:', event.data);
};

eventSource.onerror = function(event) {
    console.error('Error en la conexión:', event);
};

// Para cerrar la conexión
// eventSource.close();
```

### Explicación
- **Limitaciones**: `EventSource` solo permite la comunicación unidireccional desde el servidor hacia el cliente. No se pueden enviar mensajes de vuelta al servidor a través de esta conexión.
- **Compatibilidad**: `EventSource` es compatible con la mayoría de los navegadores modernos, aunque no es soportado por Internet Explorer.
- **Manejo de reconexiones**: Si la conexión se interrumpe, `EventSource` intentará reconectarse automáticamente después de un tiempo. Es importante manejar correctamente los errores para asegurar una experiencia de usuario fluida.

## Resumen en una línea
`EventSource` permite recibir actualizaciones en tiempo real desde un servidor a un cliente en JavaScript utilizando Server-Sent Events.