<!--
Meta Description: # SharedWorker en JavaScript: Ventajas y Usos ## Sinopsis SharedWorker es una característica de JavaScript que permite a múltiples conexiones de difer...
Meta Keywords: sharedworker, worker, port, event, que
-->

# SharedWorker en JavaScript: Ventajas y Usos

## Sinopsis
SharedWorker es una característica de JavaScript que permite a múltiples conexiones de diferentes ventanas, pestañas o iframes compartir un único hilo de trabajo, facilitando la comunicación y el manejo de tareas en segundo plano.

## Documentación
### Propósito
SharedWorker proporciona una forma de ejecutar código en un contexto separado del hilo principal de la aplicación, permitiendo que múltiples clientes se comuniquen con el mismo worker. Esto es especialmente útil para aplicaciones web que requieren mantener el estado o compartir datos entre diferentes partes de la aplicación.

### Uso
Para utilizar un SharedWorker, se debe crear un archivo JavaScript que contenga el código del worker. Luego, se puede instanciar desde el contexto de la aplicación principal utilizando el constructor `SharedWorker`. A continuación se muestra la estructura básica:

1. **Creación del archivo del worker** (`worker.js`):
   ```javascript
   // worker.js
   onconnect = function(event) {
       const port = event.ports[0];
       port.onmessage = function(event) {
           port.postMessage(`Echo: ${event.data}`);
       };
   };
   ```

2. **Instanciación desde el contexto principal**:
   ```javascript
   // script.js
   const worker = new SharedWorker('worker.js');

   worker.port.onmessage = function(event) {
       console.log(event.data); // Muestra el mensaje recibido del worker
   };

   worker.port.start(); // Inicia la comunicación con el worker
   worker.port.postMessage('Hello, Worker!'); // Envía un mensaje al worker
   ```

### Detalles
- **Conexiones**: Cada vez que se crea un `SharedWorker`, se pueden establecer múltiples conexiones desde diferentes contextos. Cada conexión se administra a través de un puerto (`port`).
- **Comunicación**: La comunicación se realiza mediante el envío de mensajes a través de `postMessage` y la recepción de mensajes mediante el evento `onmessage`.
- **Persistencia**: A diferencia de los Web Workers, que están limitados a la pestaña o ventana que los creó, los SharedWorkers persisten mientras haya al menos una conexión activa.

## Ejemplos
### Ejemplo Básico de SharedWorker
```javascript
// worker.js
onconnect = function(event) {
    const port = event.ports[0];
    port.onmessage = function(event) {
        port.postMessage(`Hola desde el SharedWorker: ${event.data}`);
    };
};

// script.js
const sharedWorker = new SharedWorker('worker.js');

sharedWorker.port.onmessage = function(event) {
    console.log(event.data);
};

sharedWorker.port.start();
sharedWorker.port.postMessage('¡Saludos!');
```

### Ejemplo con Múltiples Conexiones
```javascript
// script1.js
const worker1 = new SharedWorker('worker.js');
worker1.port.onmessage = function(event) {
    console.log('Desde script1:', event.data);
};
worker1.port.start();
worker1.port.postMessage('Mensaje desde script1');

// script2.js
const worker2 = new SharedWorker('worker.js');
worker2.port.onmessage = function(event) {
    console.log('Desde script2:', event.data);
};
worker2.port.start();
worker2.port.postMessage('Mensaje desde script2');
```

## Explicación
### Problemas Comunes
- **Compatibilidad**: No todos los navegadores soportan SharedWorker. Es importante verificar la compatibilidad antes de utilizar esta característica.
- **Cierre del Worker**: Si no hay conexiones activas, el SharedWorker puede cerrarse. Asegúrate de manejar adecuadamente el ciclo de vida de las conexiones.
- **Errores de Mensaje**: Asegúrate de que los mensajes enviados y recibidos sean del tipo correcto para evitar errores en el procesamiento.

## Resumen en Una Línea
SharedWorker permite la comunicación y ejecución de tareas en segundo plano entre múltiples conexiones en diferentes contextos de una aplicación web, optimizando el rendimiento y la gestión de datos compartidos.