<!--
Meta Description: # cancelAnimationFrame: Controlando la Animación en JavaScript ## Sinopsis `cancelAnimationFrame` es un método de JavaScript utilizado para detener la...
Meta Keywords: animación, que, cancelanimationframe, cancelar, requestanimationframe
-->

# cancelAnimationFrame: Controlando la Animación en JavaScript

## Sinopsis
`cancelAnimationFrame` es un método de JavaScript utilizado para detener la ejecución de una animación que fue previamente programada con `requestAnimationFrame`. Este comando es fundamental para optimizar el rendimiento de las aplicaciones web, permitiendo gestionar eficientemente los ciclos de animación.

## Documentación
El método `cancelAnimationFrame` se utiliza cuando deseas cancelar una animación programada con `requestAnimationFrame`. Este método toma como argumento el ID de la animación que deseas cancelar, el cual se devuelve al llamar a `requestAnimationFrame`. 

### Propósito
El propósito principal de `cancelAnimationFrame` es evitar que se ejecute una función de animación que ya no es necesaria, lo que ayuda a conservar recursos del navegador y mejorar el rendimiento de la aplicación.

### Uso
La sintaxis básica de `cancelAnimationFrame` es la siguiente:

```javascript
cancelAnimationFrame(id);
```

- **id**: Un entero que representa el identificador de la animación que deseas cancelar, obtenido de `requestAnimationFrame`.

### Detalles
- Este método es parte de la API de animaciones del navegador y se encuentra disponible en la mayoría de los navegadores modernos.
- Si se pasa un ID que no corresponde a ninguna animación en curso, no se producirá ningún efecto adverso.
- Es importante almacenar el ID devuelto por `requestAnimationFrame` si se desea cancelar la animación en el futuro.

## Ejemplos

### Ejemplo 1: Cancelar una Animación Simple
```javascript
let animationId;

function animate() {
    // Lógica de animación
    console.log('Animando...');
    animationId = requestAnimationFrame(animate);
}

// Iniciar la animación
animate();

// Cancelar la animación después de 2000 ms
setTimeout(() => {
    cancelAnimationFrame(animationId);
    console.log('Animación cancelada.');
}, 2000);
```

### Ejemplo 2: Cancelar Condicionalmente
```javascript
let animationId;
let running = true;

function animate() {
    if (running) {
        console.log('Animando...');
        animationId = requestAnimationFrame(animate);
    }
}

// Iniciar la animación
animate();

// Cancelar la animación al hacer clic en un botón
document.getElementById('cancelBtn').addEventListener('click', () => {
    running = false;
    cancelAnimationFrame(animationId);
    console.log('Animación cancelada.');
});
```

## Explicación
Es fácil caer en la trampa de no cancelar las animaciones que ya no son necesarias, lo que puede causar un uso innecesario de la CPU y afectar el rendimiento de la aplicación. Asegúrate de guardar el ID de la animación y de llamar a `cancelAnimationFrame` cuando la animación ya no sea relevante. También es esencial entender que el método no provocará errores si se llama con un ID inválido, pero simplemente no tendrá efecto.

## Resumen en Una Línea
`cancelAnimationFrame` permite detener una animación programada con `requestAnimationFrame`, optimizando el rendimiento de las aplicaciones web en JavaScript.