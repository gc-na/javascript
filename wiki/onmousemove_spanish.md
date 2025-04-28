<!--
Meta Description: # onmousemove: Evento de JavaScript para Detectar el Movimiento del Ratón ## Sinopsis El evento `onmousemove` en JavaScript permite detectar el movimi...
Meta Keywords: onmousemove, html, ratón, evento, para
-->

# onmousemove: Evento de JavaScript para Detectar el Movimiento del Ratón

## Sinopsis
El evento `onmousemove` en JavaScript permite detectar el movimiento del ratón sobre un elemento del documento. Este evento es útil para crear interacciones dinámicas y mejorar la experiencia del usuario en aplicaciones web.

## Documentación
### Propósito
El evento `onmousemove` se activa cada vez que el ratón se mueve dentro de un elemento específico. Este evento se puede utilizar para realizar diversas acciones, como mostrar información contextual, cambiar estilos o activar animaciones.

### Uso
Para utilizar el evento `onmousemove`, se puede asignar una función de controlador de eventos a un elemento HTML. Esto se puede hacer de varias maneras, incluyendo el uso de HTML, JavaScript puro o bibliotecas como jQuery.

#### Sintaxis básica:
```html
<elemento onmousemove="función()">
```

### Ejemplo utilizando JavaScript puro:
```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ejemplo onmousemove</title>
    <style>
        #area {
            width: 300px;
            height: 300px;
            background-color: lightblue;
            border: 1px solid blue;
        }
    </style>
</head>
<body>
    <div id="area">Mueve el ratón aquí</div>
    <script>
        const area = document.getElementById('area');
        area.onmousemove = function(event) {
            const x = event.clientX;
            const y = event.clientY;
            area.textContent = `X: ${x}, Y: ${y}`;
        };
    </script>
</body>
</html>
```

## Ejemplos
### Ejemplo básico de onmousemove
```html
<div onmousemove="alert('El ratón se movió!')">Pasa el ratón por aquí</div>
```

### Ejemplo de cambio de estilo
```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <title>Cambio de color con onmousemove</title>
</head>
<body>
    <div id="colorBox" style="width:200px; height:200px; background-color:red;"></div>
    <script>
        const box = document.getElementById('colorBox');
        box.onmousemove = function() {
            box.style.backgroundColor = 'green';
        };
        box.onmouseleave = function() {
            box.style.backgroundColor = 'red';
        };
    </script>
</body>
</html>
```

## Explicación
### Problemas Comunes
- **Rendimiento**: Al utilizar `onmousemove`, se ejecutará la función cada vez que el ratón se mueva. Esto puede causar problemas de rendimiento si la función es compleja o si se aplica a un área grande. Es recomendable optimizar la función o utilizar un "debounce" para limitar la frecuencia de la ejecución.
  
- **Accesibilidad**: Algunos usuarios pueden no interactuar con el contenido utilizando un ratón. Asegúrate de que tu aplicación siga siendo accesible para quienes usan teclados o dispositivos de asistencia.

- **Dispositivos táctiles**: En dispositivos móviles, el evento `onmousemove` no se activa. Considera usar eventos como `touchmove` para mejorar la compatibilidad.

## Resumen en Una Línea
El evento `onmousemove` de JavaScript permite detectar y responder al movimiento del ratón sobre un elemento, mejorando así la interactividad en aplicaciones web.