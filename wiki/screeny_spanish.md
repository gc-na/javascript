<!--
Meta Description: # screenY en JavaScript: Comprendiendo la Propiedad de la Posición Vertical de la Pantalla ## Sinopsis La propiedad `screenY` en JavaScript es utiliza...
Meta Keywords: del, screeny, pantalla, posición, con
-->

# screenY en JavaScript: Comprendiendo la Propiedad de la Posición Vertical de la Pantalla

## Sinopsis
La propiedad `screenY` en JavaScript es utilizada para obtener la coordenada vertical de la posición del puntero del mouse en relación con la pantalla. Es una herramienta esencial para el desarrollo de aplicaciones web que requieren interacciones precisas basadas en la ubicación del cursor.

## Documentación
La propiedad `screenY` forma parte del objeto `MouseEvent` y se utiliza en el contexto de eventos del mouse. Su propósito principal es devolver la posición vertical del puntero del mouse en píxeles desde la parte superior de la pantalla.

### Uso
Para acceder a `screenY`, es necesario capturar un evento del mouse, como `click`, `mousemove`, o `mousedown`. La propiedad devuelve un valor numérico que representa la altura desde la parte superior de la pantalla hasta la posición del cursor.

#### Sintaxis
```javascript
event.screenY;
```

### Detalles
- **Tipo de Valor**: `Number`
- **Escala**: La coordenada es relativa a la pantalla, no al área de visualización del navegador.
- **Compatibilidad**: `screenY` es compatible con la mayoría de los navegadores modernos.

## Ejemplos

### Ejemplo 1: Uso Básico de screenY
```javascript
document.addEventListener('mousemove', function(event) {
    console.log('Posición vertical del mouse en la pantalla: ' + event.screenY + 'px');
});
```

### Ejemplo 2: Captura de click
```javascript
document.addEventListener('click', function(event) {
    alert('Has hecho clic en la posición: ' + event.screenY + 'px desde la parte superior de la pantalla.');
});
```

## Explicación
Es importante tener en cuenta que `screenY` puede comportarse de manera diferente en dispositivos con pantallas múltiples o configuraciones de pantalla extendida. Además, si el navegador está maximizado o minimizado, el valor de `screenY` reflejará la posición real del cursor en relación con la pantalla física, no con la ventana del navegador.

### Errores Comunes
- **Confusión con clientY**: A menudo, los desarrolladores novatos confunden `screenY` con `clientY`. Mientras que `clientY` devuelve la posición vertical en relación con la ventana del navegador, `screenY` lo hace respecto a toda la pantalla.
- **No considerar el desplazamiento**: Al utilizar `screenY`, es crucial recordar que este valor no se ve afectado por el desplazamiento de la página.

## Resumen en Una Línea
La propiedad `screenY` en JavaScript proporciona la posición vertical del puntero del mouse en relación con la pantalla, facilitando interacciones precisas en aplicaciones web.