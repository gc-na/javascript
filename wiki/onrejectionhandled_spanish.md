<!--
Meta Description: # onrejectionhandled: Manejo de Promesas en JavaScript ## Sinopsis El evento `onrejectionhandled` en JavaScript permite a los desarrolladores gestiona...
Meta Keywords: onrejectionhandled, promesa, error, promesas, evento
-->

# onrejectionhandled: Manejo de Promesas en JavaScript

## Sinopsis
El evento `onrejectionhandled` en JavaScript permite a los desarrolladores gestionar rechazos de promesas que han sido manejadas de manera explícita. Este evento se activa cuando una promesa rechazada es manejada en un bloque `catch` o mediante un manejador `then`, lo que proporciona una forma de realizar acciones adicionales en caso de un rechazo.

## Documentación
El evento `onrejectionhandled` es parte del objeto global `window` y se utiliza para detectar cuando una promesa que fue rechazada ha sido finalmente manejada. Es especialmente útil para monitorear el comportamiento de promesas en aplicaciones grandes y complejas.

### Propósito
El evento `onrejectionhandled` permite a los desarrolladores:
- Supervisar el manejo de errores en promesas.
- Realizar acciones específicas cuando una promesa rechazada es finalmente manejada.
- Mejorar la depuración y el seguimiento de errores en la aplicación.

### Uso
Para utilizar `onrejectionhandled`, simplemente asigna una función a `window.onrejectionhandled`. Esta función se ejecutará cada vez que se maneje un rechazo de promesa.

```javascript
window.onrejectionhandled = function(event) {
    console.log('Se ha manejado un rechazo de promesa:', event.promise);
};
```

### Detalles
- Este evento es emitido después de que un rechazo de promesa ha sido manejado.
- Se puede utilizar para registrar información adicional o realizar tareas de limpieza.
- Es importante tener en cuenta que `onrejectionhandled` no se activa si el rechazo no es manejado.

## Ejemplos

### Ejemplo 1: Uso básico de onrejectionhandled

```javascript
// Asignar el evento
window.onrejectionhandled = function(event) {
    console.log('Rechazo manejado:', event.promise);
};

// Crear una promesa que se rechaza
let promesa = new Promise((resolve, reject) => {
    reject('Error en la promesa');
});

// Manejar el rechazo
promesa.catch(error => {
    console.log('Error capturado:', error);
});
```

### Ejemplo 2: Manejo de múltiples promesas

```javascript
window.onrejectionhandled = function(event) {
    console.log('Rechazo manejado:', event.promise);
};

let promesa1 = new Promise((resolve, reject) => {
    reject('Primer error');
});

let promesa2 = new Promise((resolve, reject) => {
    reject('Segundo error');
});

// Manejo de rechazos
promesa1.catch(error => {
    console.log('Error en promesa 1:', error);
});

promesa2.catch(error => {
    console.log('Error en promesa 2:', error);
});
```

## Explicación
Al utilizar `onrejectionhandled`, es crucial recordar que:
- El evento no se activará si el rechazo no es manejado. Por lo tanto, asegúrate de que todas tus promesas tengan un manejador de errores para evitar pérdidas de información sobre excepciones.
- Este evento puede ayudar a identificar y solucionar problemas en el flujo de manejo de promesas, especialmente en aplicaciones grandes donde las promesas pueden ser difíciles de rastrear.

## Resumen en una línea
El evento `onrejectionhandled` en JavaScript permite gestionar y supervisar el manejo de promesas rechazadas, facilitando la depuración y el seguimiento de errores.