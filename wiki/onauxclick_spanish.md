<!--
Meta Description: # onauxclick: Evento de JavaScript para clics auxiliares ## Sinopsis El evento `onauxclick` en JavaScript permite detectar clics auxiliares del mouse,...
Meta Keywords: onauxclick, clic, botón, html, clics
-->

# onauxclick: Evento de JavaScript para clics auxiliares

## Sinopsis
El evento `onauxclick` en JavaScript permite detectar clics auxiliares del mouse, como el clic del botón central o el clic derecho. Es útil para implementar funciones específicas en aplicaciones web que requieren una interacción más allá de los clics primarios.

## Documentación
El evento `onauxclick` se activa cuando se realiza un clic auxiliar en un elemento. Este evento es particularmente relevante para los navegadores que utilizan un mouse con múltiples botones, ya que permite a los desarrolladores manejar diferentes tipos de clics de forma específica.

### Propósito
El propósito de `onauxclick` es proporcionar una manera de responder a interacciones de usuario que no son simplemente clics del botón izquierdo del mouse. Esto incluye el botón central y el botón derecho, dependiendo de la configuración y el entorno del usuario.

### Uso
Para utilizar `onauxclick`, se puede agregar un manejador de eventos a un elemento HTML. Este manejador se activará cada vez que se produzca un clic auxiliar.

### Sintaxis básica
```javascript
elemento.onauxclick = función;
```

## Ejemplos
### Ejemplo 1: Manejo de clics auxiliares
```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <title>Ejemplo onauxclick</title>
</head>
<body>
    <button id="miBoton">Haz clic aquí</button>
    <script>
        const boton = document.getElementById('miBoton');
        boton.onauxclick = function(event) {
            if (event.button === 1) { // Botón central
                alert('Has hecho clic con el botón central.');
            } else if (event.button === 2) { // Botón derecho
                alert('Has hecho clic con el botón derecho.');
            }
        };
    </script>
</body>
</html>
```

### Ejemplo 2: Previniendo el menú contextual con clic derecho
```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <title>Ejemplo onauxclick - Prevenir menú</title>
</head>
<body>
    <div id="miDiv" style="width: 200px; height: 200px; background-color: lightblue;">
        Haz clic derecho aquí
    </div>
    <script>
        const div = document.getElementById('miDiv');
        div.onauxclick = function(event) {
            if (event.button === 2) { // Botón derecho
                event.preventDefault(); // Previene el menú contextual
                alert('Clic derecho deshabilitado.');
            }
        };
    </script>
</body>
</html>
```

## Explicación
### Errores comunes
- **No comprobar el botón correcto**: Es importante verificar qué botón se ha presionado utilizando `event.button` para asegurarse de que la acción se ejecute correctamente según el tipo de clic.
- **No prevenir el comportamiento predeterminado**: Si se desea evitar el menú contextual en clics derechos, es crucial llamar a `event.preventDefault()`.

### Consideraciones adicionales
- `onauxclick` no es compatible con todos los navegadores, por lo que es recomendable verificar la compatibilidad si se planea utilizar en una aplicación de producción.
- Este evento es parte de la especificación estándar de eventos de usuario, por lo que su uso puede variar dependiendo del entorno del usuario.

## Resumen en una línea
El evento `onauxclick` permite manejar clics auxiliares en JavaScript, facilitando interacciones más ricas en aplicaciones web.