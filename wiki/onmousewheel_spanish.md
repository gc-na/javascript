<!--
Meta Description: # onmousewheel en JavaScript: Controla el desplazamiento del ratón ## Sinopsis El evento `onmousewheel` en JavaScript permite a los desarrolladores de...
Meta Keywords: desplazamiento, del, evento, onmousewheel, event
-->

# onmousewheel en JavaScript: Controla el desplazamiento del ratón

## Sinopsis
El evento `onmousewheel` en JavaScript permite a los desarrolladores detectar y responder a los movimientos de la rueda del ratón, facilitando la implementación de interacciones personalizadas basadas en el desplazamiento vertical o horizontal.

## Documentación
El evento `onmousewheel` se activa cuando el usuario gira la rueda del ratón. Este evento se puede utilizar para crear experiencias interactivas, como el desplazamiento suave de elementos, la navegación en aplicaciones web, o la implementación de zoom en imágenes y mapas.

### Propósito
El objetivo principal de `onmousewheel` es proporcionar una forma de capturar la acción del desplazamiento del ratón y realizar tareas específicas en respuesta a ello.

### Uso
Para utilizar el evento `onmousewheel`, debes añadir un manejador de eventos a un elemento del DOM. Este manejador puede ser una función que recibe un objeto de evento como argumento y se puede utilizar para obtener información sobre el desplazamiento.

### Detalles
- **Compatibilidad**: `onmousewheel` es compatible con la mayoría de los navegadores, pero es recomendable utilizar el evento `wheel` para una compatibilidad más amplia y un comportamiento más predecible.
- **Propiedades del evento**: El objeto del evento `onmousewheel` tiene propiedades como `deltaY`, que indica la cantidad de desplazamiento en el eje vertical, y `deltaX` para el desplazamiento horizontal.

## Ejemplos

### Ejemplo 1: Detectar el desplazamiento vertical
```javascript
document.addEventListener('mousewheel', function(event) {
    if (event.deltaY > 0) {
        console.log('Desplazamiento hacia abajo');
    } else {
        console.log('Desplazamiento hacia arriba');
    }
});
```

### Ejemplo 2: Desplazamiento suave
```javascript
const box = document.getElementById('box');
box.addEventListener('mousewheel', function(event) {
    event.preventDefault(); // Prevenir el comportamiento por defecto
    box.scrollTop += event.deltaY; // Ajustar el desplazamiento del contenedor
});
```

### Ejemplo 3: Zoom con desplazamiento
```javascript
let scale = 1;
document.addEventListener('mousewheel', function(event) {
    event.preventDefault();
    scale += event.deltaY * -0.01; // Ajustar la escala según el desplazamiento
    scale = Math.min(Math.max(0.125, scale), 4); // Limitar la escala
    document.body.style.transform = `scale(${scale})`; // Aplicar la escala
});
```

## Explicación
Al implementar `onmousewheel`, es común enfrentarse a algunos problemas o "gotchas". Uno de los más comunes es el comportamiento por defecto del desplazamiento del ratón, que puede interferir con las interacciones personalizadas. Para evitar esto, se recomienda llamar a `event.preventDefault()` en el manejador del evento. Además, al usar `onmousewheel`, la diferencia entre `deltaY` y `deltaX` puede no ser consistente entre diferentes navegadores, por lo que se sugiere utilizar el evento `wheel` para un manejo más uniforme.

## Resumen en una línea
El evento `onmousewheel` en JavaScript permite capturar y responder a los movimientos de la rueda del ratón, facilitando interacciones personalizadas en aplicaciones web.