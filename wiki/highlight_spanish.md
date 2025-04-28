<!--
Meta Description: # Resaltar Texto en JavaScript: Cómo Utilizar la Función de Resaltado ## Sinopsis El resaltado en JavaScript se refiere a la capacidad de marcar o des...
Meta Keywords: resaltar, texto, resaltado, html, javascript
-->

# Resaltar Texto en JavaScript: Cómo Utilizar la Función de Resaltado

## Sinopsis
El resaltado en JavaScript se refiere a la capacidad de marcar o destacar texto en un documento web, mejorando así la visibilidad y la interactividad del contenido. Esto puede lograrse a través de métodos de manipulación del DOM y estilos CSS.

## Documentación
El resaltado de texto en JavaScript se utiliza comúnmente para mejorar la experiencia del usuario al interactuar con contenido específico. Puedes resaltar texto utilizando varias técnicas, incluyendo la manipulación de elementos HTML y la aplicación de estilos CSS.

### Propósito
El propósito principal de resaltar texto es llamar la atención del usuario sobre ciertas partes de un contenido, como palabras clave, frases importantes o resultados de búsqueda.

### Uso
Para resaltar texto en JavaScript, se puede utilizar el método `innerHTML` para envolver el texto que se desea resaltar en una etiqueta `<span>` con una clase CSS que aplique el estilo de resaltado. A continuación, se proporciona un ejemplo básico de cómo hacerlo.

## Ejemplos

### Ejemplo 1: Resaltar Texto Básico
```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ejemplo de Resaltado</title>
    <style>
        .resaltado {
            background-color: yellow;
            font-weight: bold;
        }
    </style>
</head>
<body>
    <p id="texto">Este es un texto que quiero resaltar.</p>
    <button onclick="resaltarTexto()">Resaltar Texto</button>

    <script>
        function resaltarTexto() {
            const textoElemento = document.getElementById('texto');
            textoElemento.innerHTML = textoElemento.innerHTML.replace('resaltar', '<span class="resaltado">resaltar</span>');
        }
    </script>
</body>
</html>
```

### Ejemplo 2: Resaltar Palabras Clave en un Párrafo
```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Resaltar Palabras Clave</title>
    <style>
        .resaltado {
            background-color: orange;
            color: white;
        }
    </style>
</head>
<body>
    <p id="parrafo">JavaScript es un lenguaje de programación que permite crear páginas web interactivas.</p>
    <button onclick="resaltarPalabra('JavaScript')">Resaltar 'JavaScript'</button>

    <script>
        function resaltarPalabra(palabra) {
            const parrafoElemento = document.getElementById('parrafo');
            const regex = new RegExp(`(${palabra})`, 'gi');
            parrafoElemento.innerHTML = parrafoElemento.innerHTML.replace(regex, '<span class="resaltado">$1</span>');
        }
    </script>
</body>
</html>
```

## Explicación
Al resaltar texto, es importante tener en cuenta que la manipulación del `innerHTML` puede llevar a la pérdida de eventos o comportamientos de otros elementos dentro del mismo contenedor. Además, el uso de expresiones regulares puede ser sensible a mayúsculas y minúsculas, así que es recomendable usar la opción 'i' (insensible a mayúsculas) en la expresión regular.

Otro punto a considerar es el rendimiento, ya que el cambio de `innerHTML` en grandes volúmenes de contenido puede ser menos eficiente que métodos alternativos como `document.createElement` si se requiere un resaltado más dinámico y complejo.

## Resumen en una Línea
El resaltado en JavaScript permite marcar texto en documentos web para mejorar la visibilidad y la interactividad del contenido.