<!--
Meta Description: # onmessage en JavaScript: Comunicación en Web Workers y Eventos ## Sinopsis El evento `onmessage` en JavaScript es fundamental para la comunicación e...
Meta Keywords: worker, onmessage, event, web, hilo
-->

# onmessage en JavaScript: Comunicación en Web Workers y Eventos

## Sinopsis
El evento `onmessage` en JavaScript es fundamental para la comunicación entre el hilo principal y los Web Workers, permitiendo el intercambio de datos de manera eficiente y asíncrona en aplicaciones web.

## Documentación
El evento `onmessage` se utiliza para recibir mensajes enviados desde un Web Worker o desde otros contextos de ejecución. Este evento es crucial para la interacción entre el hilo principal y los Web Workers, ya que permite manejar la lógica de procesamiento en segundo plano sin bloquear la interfaz de usuario.

### Propósito
El objetivo de `onmessage` es facilitar la comunicación entre diferentes hilos de ejecución, mejorando la eficiencia y la capacidad de respuesta de las aplicaciones web.

### Uso
Para utilizar `onmessage`, se debe asignar una función a esta propiedad que maneje los mensajes recibidos. La función recibe un objeto `MessageEvent`, que contiene el dato enviado.

```javascript
// Ejemplo básico de uso de onmessage en un Web Worker

// worker.js
self.onmessage = function(event) {
    console.log('Mensaje recibido del hilo principal:', event.data);
    self.postMessage('Respuesta del Worker');
};

// hilo principal
const worker = new Worker('worker.js');
worker.onmessage = function(event) {
    console.log('Mensaje recibido del Worker:', event.data);
};
worker.postMessage('Hola Worker');
```

## Ejemplos
### Ejemplo 1: Comunicación Básica entre Hilos
```javascript
// worker.js
self.onmessage = function(event) {
    const result = event.data * 2;
    self.postMessage(result);
};

// hilo principal
const worker = new Worker('worker.js');
worker.onmessage = function(event) {
    console.log('El doble es:', event.data);
};
worker.postMessage(5); // Enviamos 5 al Worker
```

### Ejemplo 2: Manejo de Errores
```javascript
// worker.js
self.onmessage = function(event) {
    try {
        // Simulamos una operación
        if (event.data === 'error') throw new Error('Error simulado');
        self.postMessage(`Mensaje recibido: ${event.data}`);
    } catch (error) {
        self.postMessage(`Error: ${error.message}`);
    }
};

// hilo principal
const worker = new Worker('worker.js');
worker.onmessage = function(event) {
    console.log(event.data);
};
worker.postMessage('error'); // Producimos un error
```

## Explicación
Al utilizar `onmessage`, es importante tener en cuenta que:
- Los Web Workers operan en un contexto separado, lo que significa que no pueden acceder al DOM directamente.
- Los mensajes deben ser serializables. Algunos tipos de datos, como funciones o instancias de clases complejas, no se pueden enviar directamente.
- Es recomendable manejar errores adecuadamente en el Worker, utilizando bloques `try-catch` para evitar que fallos en el Worker afecten al hilo principal.

## Resumen en Una Línea
El evento `onmessage` en JavaScript permite la comunicación eficiente entre el hilo principal y los Web Workers, facilitando el intercambio de datos en aplicaciones web.