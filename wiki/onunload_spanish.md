<!--
Meta Description: # Evento onunload en JavaScript: Uso y Ejemplos Esenciales ## Sinopsis El evento `onunload` en JavaScript se activa cuando un documento se está a punt...
Meta Keywords: evento, onunload, javascript, que, unload
-->

# Evento onunload en JavaScript: Uso y Ejemplos Esenciales

## Sinopsis
El evento `onunload` en JavaScript se activa cuando un documento se está a punto de ser descargado o cerrado, permitiendo a los desarrolladores ejecutar código antes de que la página se cierre.

## Documentación
El evento `onunload` se utiliza para capturar la acción de salida de un usuario de una página web. Este evento se puede asociar con el objeto `window`, lo que permite ejecutar una función específica justo antes de que el usuario abandone la página.

### Propósito
El propósito principal del evento `onunload` es permitir a los desarrolladores realizar tareas como:
- Guardar datos en el almacenamiento local.
- Enviar información a un servidor antes de que el usuario se aleje de la página.
- Limpiar recursos, como cerrar conexiones de WebSocket.

### Uso
El evento `onunload` se puede asignar usando JavaScript de la siguiente manera:

```javascript
window.onunload = function() {
    // Código a ejecutar en el evento unload
    console.log("La página se está cerrando o recargando.");
};
```

Además de esto, se puede agregar el evento utilizando `addEventListener`:

```javascript
window.addEventListener('unload', function() {
    // Código a ejecutar en el evento unload
    console.log("La página se está cerrando o recargando.");
});
```

## Ejemplos

### Ejemplo 1: Mensaje simple en la consola
```javascript
window.onunload = function() {
    console.log("Adiós, gracias por visitar!");
};
```

### Ejemplo 2: Guardar datos en el almacenamiento local
```javascript
window.onunload = function() {
    localStorage.setItem('data', JSON.stringify({ key: 'value' }));
};
```

### Ejemplo 3: Enviar datos a un servidor
```javascript
window.addEventListener('unload', function() {
    navigator.sendBeacon('/log', JSON.stringify({ event: 'page unload' }));
});
```

## Explicación
Al utilizar el evento `onunload`, es importante tener en cuenta algunos puntos:

1. **Limitaciones del Navegador**: Algunos navegadores pueden no permitir la ejecución de ciertas acciones durante el evento `onunload`, especialmente si incluyen operaciones asincrónicas.
   
2. **Uso de `sendBeacon`**: Para enviar información a un servidor durante el evento `unload`, se recomienda usar `navigator.sendBeacon`, ya que garantiza que la solicitud se envíe incluso si la página se cierra rápidamente.

3. **Interferencia del Usuario**: Los usuarios pueden cerrar su navegador o pestañas de manera inesperada, lo que puede afectar la ejecución de código en el evento `onunload`.

4. **Eventos `beforeunload` y `unload`**: Es común confundir `beforeunload` con `unload`. Mientras que `beforeunload` se utiliza para mostrar un mensaje de confirmación al usuario, `unload` se ejecuta cuando la navegación realmente ocurre.

## Resumen en una línea
El evento `onunload` en JavaScript permite ejecutar código justo antes de que un usuario abandone una página, facilitando tareas como el almacenamiento de datos y la limpieza de recursos.