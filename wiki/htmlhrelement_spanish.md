<!--
Meta Description: # HTMLHRElement en JavaScript: Guía Completa ## Sinopsis El `HTMLHRElement` es una interfaz de JavaScript que representa el elemento `<hr>` en HTML, u...
Meta Keywords: html, htmlhrelement, línea, elemento, para
-->

# HTMLHRElement en JavaScript: Guía Completa

## Sinopsis
El `HTMLHRElement` es una interfaz de JavaScript que representa el elemento `<hr>` en HTML, utilizado para crear una línea horizontal que separa contenido en documentos web. Este elemento es frecuentemente empleado para mejorar la estructura visual y la legibilidad del contenido.

## Documentación
El `HTMLHRElement` es una parte de la API del DOM (Document Object Model) y proporciona propiedades y métodos que permiten manipular y acceder a los atributos del elemento `<hr>`. 

### Propósito
El propósito principal del `HTMLHRElement` es servir como un separador visual en una página web, mejorando la organización de la información. Además, este elemento puede ser estilizado mediante CSS para ajustarse al diseño deseado.

### Uso
Para acceder a un elemento `<hr>` mediante JavaScript, se puede utilizar métodos como `document.getElementById`, `document.querySelector`, o `document.getElementsByTagName`.

#### Propiedades Comunes
- `align`: Alineación de la línea horizontal.
- `color`: Color de la línea horizontal.
- `size`: Espesor de la línea horizontal.
- `width`: Ancho de la línea horizontal.

#### Métodos Comunes
El `HTMLHRElement` no tiene métodos específicos, pero hereda métodos del `HTMLElement`, como `setAttribute`, `getAttribute`, y `removeAttribute`.

## Ejemplos

### Ejemplo Básico de Creación
```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <title>Ejemplo HTMLHRElement</title>
</head>
<body>
    <h1>Título de la sección</h1>
    <hr id="miLinea">
    <p>Este es un párrafo.</p>

    <script>
        // Accediendo al elemento hr
        const hrElement = document.getElementById('miLinea');
        hrElement.setAttribute('color', 'blue');
        hrElement.setAttribute('size', '5');
    </script>
</body>
</html>
```

### Ejemplo de Estilo
```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <title>Estilo de HTMLHRElement</title>
    <style>
        hr {
            border: 1px solid red;
            width: 50%;
            margin: 20px auto;
        }
    </style>
</head>
<body>
    <h1>Sección 1</h1>
    <hr>
    <h1>Sección 2</h1>
</body>
</html>
```

## Explicación
Al utilizar el `HTMLHRElement`, es importante tener en cuenta que algunas propiedades pueden no ser soportadas por todos los navegadores. Por ejemplo, el atributo `color` no es estándar y puede no tener efecto en algunos navegadores. Es recomendable utilizar CSS para aplicar estilos en lugar de depender de atributos HTML obsoletos. Además, se debe tener cuidado con el tamaño y el grosor de la línea, ya que valores demasiado altos pueden afectar la estética del diseño.

## Resumen en Una Línea
El `HTMLHRElement` permite crear líneas horizontales en HTML y manipularlas mediante JavaScript para mejorar la estructura visual de las páginas web.