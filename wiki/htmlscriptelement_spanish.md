<!--
Meta Description: # HTMLScriptElement: Elemento de Script en HTML y su Uso en JavaScript ## Sinopsis El `HTMLScriptElement` es una interfaz que representa un elemento `...
Meta Keywords: script, que, html, javascript, src
-->

# HTMLScriptElement: Elemento de Script en HTML y su Uso en JavaScript

## Sinopsis
El `HTMLScriptElement` es una interfaz que representa un elemento `<script>` en un documento HTML. Este elemento se utiliza para incluir y ejecutar código JavaScript en páginas web, permitiendo la manipulación dinámica del contenido y la interacción con el usuario.

## Documentación
El `HTMLScriptElement` es parte del DOM (Document Object Model) y proporciona propiedades y métodos para manipular elementos `<script>` en el HTML. Su propósito principal es permitir la inclusión de scripts que pueden ser ejecutados por el navegador.

### Propiedades Importantes
- **src**: Especifica la URL del archivo JavaScript externo que se va a cargar.
- **type**: Define el tipo de contenido del script (por defecto es "text/javascript").
- **async**: Un booleano que indica si el script debe ser ejecutado de forma asíncrona.
- **defer**: Un booleano que indica si el script debe ser ejecutado después de que el documento ha sido completamente analizado.

### Métodos
- **remove()**: Elimina el elemento `<script>` del DOM.

### Uso
Para incluir un script en un documento HTML, se puede usar la etiqueta `<script>` directamente en el HTML o mediante JavaScript creando un nuevo objeto `HTMLScriptElement` y añadiéndolo al DOM.

```html
<script src="script.js"></script>
```

O mediante JavaScript:

```javascript
const script = document.createElement('script');
script.src = 'script.js';
document.head.appendChild(script);
```

## Ejemplos

### Ejemplo 1: Incluir un Script Externo
```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <title>Ejemplo HTMLScriptElement</title>
    <script src="script.js"></script>
</head>
<body>
    <h1>Hola Mundo</h1>
</body>
</html>
```

### Ejemplo 2: Crear un Script Dinámicamente
```javascript
const script = document.createElement('script');
script.src = 'script.js';
script.type = 'text/javascript';
document.body.appendChild(script);
```

### Ejemplo 3: Usar `async` y `defer`
```html
<script src="script.js" async></script>
<script src="script.js" defer></script>
```

## Explicación
Es importante tener en cuenta que el uso de scripts puede afectar el rendimiento de una página web. Los scripts que no están marcados con `async` o `defer` bloquearán la carga del contenido hasta que se descargue y ejecute el script, lo que puede causar retrasos en la visualización de la página. Usar `async` permite que el script se descargue y ejecute de forma asíncrona, mientras que `defer` garantiza que el script se ejecute una vez que el documento esté completamente cargado.

### Errores Comunes
- No especificar el atributo `src` puede resultar en un script vacío que no se ejecuta.
- Usar scripts sin `async` o `defer` puede causar bloqueos en la carga de la página.
- Olvidar manejar el orden de ejecución de scripts que dependen unos de otros.

## Resumen en una Línea
`HTMLScriptElement` es la interfaz que permite la manipulación de elementos `<script>` en HTML, facilitando la inclusión y ejecución de código JavaScript en páginas web.