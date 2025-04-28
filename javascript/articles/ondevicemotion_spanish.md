<!--
Meta Description: # ondevicemotion: Captura de Movimiento en JavaScript ## Sinopsis `ondevicemotion` es un evento en JavaScript que permite a los desarrolladores detect...
Meta Keywords: que, del, evento, dispositivo, ondevicemotion
-->

# ondevicemotion: Captura de Movimiento en JavaScript

## Sinopsis
`ondevicemotion` es un evento en JavaScript que permite a los desarrolladores detectar y reaccionar a los cambios de movimiento y orientación del dispositivo, proporcionando acceso a los datos de aceleración y rotación.

## Documentación
El evento `ondevicemotion` se activa cuando el dispositivo experimenta un cambio en su aceleración o orientación. Este evento es particularmente útil para aplicaciones móviles y juegos que requieren interacción basada en movimiento.

### Propósito
El propósito del evento `ondevicemotion` es permitir a los desarrolladores obtener información sobre la aceleración y la rotación del dispositivo, lo que permite crear experiencias interactivas y dinámicas.

### Uso
Para utilizar `ondevicemotion`, se debe agregar un listener de eventos al objeto `window`. Este listener ejecutará una función cada vez que se detecte un cambio en el movimiento del dispositivo.

#### Sintaxis básica:
```javascript
window.addEventListener('devicemotion', function(event) {
    // Tu código aquí
});
```

### Detalles
El evento `devicemotion` proporciona un objeto `MotionEvent` que contiene la siguiente información:

- `acceleration`: Un objeto que representa la aceleración del dispositivo en tres ejes (x, y, z) en metros por segundo al cuadrado (m/s²).
- `accelerationIncludingGravity`: Similar a `acceleration`, pero incluye la aceleración debida a la gravedad.
- `rotationRate`: Un objeto que describe la velocidad de rotación del dispositivo en grados por segundo (dps) en tres ejes (alpha, beta, gamma).
- `interval`: El intervalo de tiempo entre los eventos en milisegundos.

## Ejemplos

### Ejemplo 1: Captura de Aceleración
```javascript
window.addEventListener('devicemotion', function(event) {
    const acceleration = event.acceleration;
    console.log(`Aceleración: x=${acceleration.x}, y=${acceleration.y}, z=${acceleration.z}`);
});
```

### Ejemplo 2: Captura de Rotación
```javascript
window.addEventListener('devicemotion', function(event) {
    const rotationRate = event.rotationRate;
    console.log(`Tasa de rotación: alpha=${rotationRate.alpha}, beta=${rotationRate.beta}, gamma=${rotationRate.gamma}`);
});
```

## Explicación
Al trabajar con el evento `ondevicemotion`, es importante tener en cuenta lo siguiente:

- **Permisos de usuario**: En algunos navegadores, es posible que se necesiten permisos para acceder a los datos de movimiento del dispositivo debido a preocupaciones de privacidad.
- **Rendimiento**: La captura de eventos de movimiento puede ser intensiva en recursos, por lo que se recomienda optimizar el código y limitar la frecuencia de lectura de datos.
- **Compatibilidad**: Asegúrate de probar tu aplicación en diferentes dispositivos y navegadores, ya que la implementación del evento puede variar.

## Resumen en una línea
El evento `ondevicemotion` en JavaScript permite detectar cambios en el movimiento y la orientación del dispositivo, facilitando el desarrollo de aplicaciones interactivas.