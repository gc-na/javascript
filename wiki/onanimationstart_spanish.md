<!--
Meta Description: # onanimationstart: Evento en JavaScript para Animaciones CSS ## Sinopsis El evento `onanimationstart` en JavaScript se activa cuando una animación CS...
Meta Keywords: animación, onanimationstart, evento, que, html
-->

# onanimationstart: Evento en JavaScript para Animaciones CSS

## Sinopsis
El evento `onanimationstart` en JavaScript se activa cuando una animación CSS comienza a ejecutarse en un elemento. Este evento es útil para detectar el inicio de animaciones y ejecutar acciones específicas cuando esto ocurre.

## Documentación
### Propósito
El evento `onanimationstart` permite a los desarrolladores manejar situaciones en las que se inicia una animación en un elemento del DOM, ofreciendo la oportunidad de ejecutar código en ese momento.

### Uso
El uso del evento `onanimationstart` se puede realizar directamente en el HTML o mediante JavaScript. Este evento proporciona información sobre la animación que ha comenzado, incluyendo el nombre de la animación y el elemento que la ha disparado.

### Detalles
- **Sintaxis**: 
  ```javascript
  element.onanimationstart = function(event) {
      // Código a ejecutar cuando comienza la animación
  };
  ```

- **Propiedades del Evento**:
  - `animationName`: Nombre de la animación que ha comenzado.
  - `elapsedTime`: Tiempo transcurrido desde el inicio de la animación.
  - `target`: El elemento sobre el que se inició la animación.

## Ejemplos
### Ejemplo Básico
```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <title>Ejemplo de onanimationstart</title>
    <style>
        .animar {
            width: 100px;
            height: 100px;
            background-color: red;
            animation: mover 2s;
        }

        @keyframes mover {
            from { transform: translateX(0); }
            to { transform: translateX(200px); }
        }
    </style>
</head>
<body>
    <div class="animar"></div>
    <script>
        const caja = document.querySelector('.animar');
        caja.onanimationstart = function(event) {
            console.log('La animación ha comenzado:', event.animationName);
        };
    </script>
</body>
</html>
```

### Ejemplo con Múltiples Animaciones
```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <title>Ejemplo de onanimationstart con múltiples animaciones</title>
    <style>
        .animar {
            width: 100px;
            height: 100px;
            background-color: blue;
            animation: mover 2s, girar 1s;
        }

        @keyframes mover {
            from { transform: translateX(0); }
            to { transform: translateX(200px); }
        }

        @keyframes girar {
            from { transform: rotate(0deg); }
            to { transform: rotate(360deg); }
        }
    </style>
</head>
<body>
    <div class="animar"></div>
    <script>
        const caja = document.querySelector('.animar');
        caja.onanimationstart = function(event) {
            console.log('La animación ha comenzado:', event.animationName);
        };
    </script>
</body>
</html>
```

## Explicación
### Errores Comunes
- **No se dispara el evento**: Asegúrate de que la animación esté correctamente definida en CSS y que el elemento tenga la clase que activa la animación.
- **No se escucha el evento**: Verifica que estés asignando correctamente el evento `onanimationstart` al elemento adecuado.

### Notas Adicionales
Recuerda que el evento `onanimationstart` solo se activa para animaciones que usen la propiedad `animation` en CSS y no para transiciones (`transition`).

## Resumen en una Línea
El evento `onanimationstart` en JavaScript se activa al inicio de una animación CSS, permitiendo ejecutar código específico en ese momento.