<!--
Meta Description: # onwheel: Manejo de Eventos de Rueda en JavaScript ## Sinopsis El evento `onwheel` en JavaScript permite a los desarrolladores gestionar interaccione...
Meta Keywords: del, desplazamiento, evento, event, onwheel
-->

# onwheel: Manejo de Eventos de Rueda en JavaScript

## Sinopsis
El evento `onwheel` en JavaScript permite a los desarrolladores gestionar interacciones del usuario con la rueda del ratón. Este evento es fundamental para crear experiencias de usuario fluidas en aplicaciones web, especialmente en interfaces que requieren desplazamiento.

## Documentación
### Propósito
El evento `onwheel` se utiliza para detectar el movimiento de la rueda del ratón. Este evento proporciona información sobre la dirección y la cantidad de desplazamiento, lo que permite implementar funcionalidades como desplazamiento suave, zoom, y navegación en listas o imágenes.

### Uso
Para utilizar el evento `onwheel`, se puede agregar un listener a un elemento del DOM. Esto se puede hacer utilizando el método `addEventListener`, o directamente asignando una función al evento `onwheel` del elemento.

### Detalles
- **Propiedades del Evento**:
  - `deltaX`: Cantidad de desplazamiento horizontal.
  - `deltaY`: Cantidad de desplazamiento vertical.
  - `deltaZ`: Cantidad de desplazamiento en el eje Z (generalmente 0).
  - `deltaMode`: Indica la unidad de los valores de desplazamiento (0 para píxeles, 1 para líneas, 2 para páginas).
  
### Sintaxis Básica
```javascript
elemento.onwheel = function(event) {
    // Manejo del evento aquí
};
```

O usando `addEventListener`:
```javascript
elemento.addEventListener('wheel', function(event) {
    // Manejo del evento aquí
});
```

## Ejemplos
### Ejemplo 1: Manejo Básico del Evento
```javascript
const contenedor = document.getElementById('miContenedor');

contenedor.onwheel = function(event) {
    console.log(`Desplazamiento en Y: ${event.deltaY}`);
    event.preventDefault(); // Evita el desplazamiento por defecto
};
```

### Ejemplo 2: Desplazamiento Suave
```javascript
const contenedor = document.getElementById('miContenedor');

contenedor.addEventListener('wheel', function(event) {
    contenedor.scrollBy({
        top: event.deltaY,
        left: event.deltaX,
        behavior: 'smooth'
    });
    event.preventDefault();
});
```

## Explicación
### Errores Comunes
- **No Prevenir el Comportamiento por Defecto**: Es importante usar `event.preventDefault()` si no se desea el comportamiento de desplazamiento por defecto del navegador.
- **No Considerar Delta Y**: Ignorar el uso de `deltaY` puede llevar a resultados inesperados en el desplazamiento vertical.

### Notas Adicionales
- La compatibilidad con `onwheel` es bastante buena en navegadores modernos, pero se recomienda considerar alternativas o polyfills para soportar navegadores más antiguos.

## Resumen en Una Línea
El evento `onwheel` en JavaScript permite manejar interacciones del usuario con la rueda del ratón, facilitando el control del desplazamiento en aplicaciones web.