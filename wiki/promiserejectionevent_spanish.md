<!--
Meta Description: # PromiseRejectionEvent en JavaScript: Manejo de Errores Asíncronos ## Sinopsis El evento `PromiseRejectionEvent` en JavaScript permite a los desarrol...
Meta Keywords: evento, que, error, errores, event
-->

# PromiseRejectionEvent en JavaScript: Manejo de Errores Asíncronos

## Sinopsis
El evento `PromiseRejectionEvent` en JavaScript permite a los desarrolladores manejar rechazos de promesas no capturados, proporcionando información sobre el error que ocurrió y el contexto en el que sucedió.

## Documentación

### Propósito
`PromiseRejectionEvent` es un evento que se genera cuando una promesa se rechaza y no se captura mediante un manejador de errores. Este evento se utiliza principalmente para mejorar el manejo de errores asíncronos en aplicaciones JavaScript, permitiendo a los desarrolladores registrar, notificar o realizar acciones específicas cuando se producen errores no controlados.

### Uso
Para utilizar `PromiseRejectionEvent`, debes escuchar el evento `unhandledrejection` en el objeto `window`. Este evento proporciona un objeto que incluye la razón del rechazo y la promesa que falló.

### Detalles
- **Propiedades**: El evento `PromiseRejectionEvent` tiene dos propiedades principales:
  - `reason`: La razón del rechazo, que puede ser de cualquier tipo (ejemplo, un objeto de error).
  - `promise`: La promesa que fue rechazada.
  
- **Escucha del evento**: Puedes registrar un manejador para el evento como se muestra a continuación:

```javascript
window.addEventListener('unhandledrejection', function(event) {
    console.log('Promesa rechazada:', event.promise);
    console.log('Razón del rechazo:', event.reason);
});
```

## Ejemplos

### Ejemplo Básico
```javascript
window.addEventListener('unhandledrejection', function(event) {
    console.log('Promesa rechazada:', event.promise);
    console.log('Razón del rechazo:', event.reason);
});

function promesaFallida() {
    return new Promise((resolve, reject) => {
        reject(new Error('Algo salió mal'));
    });
}

promesaFallida(); // Lanza un evento unhandledrejection
```

### Ejemplo con Manejo de Errores
```javascript
window.addEventListener('unhandledrejection', function(event) {
    alert('Se produjo un error: ' + event.reason.message);
});

async function promesaConManejo() {
    try {
        await promesaFallida();
    } catch (error) {
        console.error('Error capturado:', error);
    }
}

promesaConManejo(); // No lanzará un evento unhandledrejection
```

## Explicación
Un error común al trabajar con promesas es no manejar adecuadamente los rechazos. Si una promesa se rechaza y no hay un manejador de errores (usando `.catch()` o un bloque `try/catch` en una función `async`), se generará un evento `PromiseRejectionEvent`. Esto puede llevar a que errores importantes pasen desapercibidos, lo que podría afectar la experiencia del usuario.

Es importante recordar que el evento `unhandledrejection` solo se activa para promesas que no han sido manejadas. Si capturas el error adecuadamente, no se generará el evento.

## Resumen en Una Línea
`PromiseRejectionEvent` permite manejar los rechazos de promesas no capturados en JavaScript, proporcionando información esencial para el manejo de errores asíncronos.