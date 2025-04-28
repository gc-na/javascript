<!--
Meta Description: # El evento onload en JavaScript: Guía completa ## Sinopsis El evento `onload` en JavaScript se utiliza para ejecutar código una vez que un recurso, c...
Meta Keywords: onload, que, evento, javascript, una
-->

# El evento onload en JavaScript: Guía completa

## Sinopsis
El evento `onload` en JavaScript se utiliza para ejecutar código una vez que un recurso, como una página web o una imagen, ha sido completamente cargado. Este evento es fundamental para garantizar que todos los elementos de la página estén disponibles antes de que se ejecute cualquier script.

## Documentación
El evento `onload` se asocia a un objeto del DOM, como `window`, `document` o elementos específicos. Su principal propósito es permitir que los desarrolladores ejecuten funciones que dependen de la carga completa del contenido. 

### Uso
El evento `onload` se puede definir de varias formas:

1. **A través de HTML**:
   ```html
   <body onload="miFuncion()">
   ```

2. **A través de JavaScript**:
   ```javascript
   window.onload = function() {
       // Código a ejecutar
   };
   ```

3. **Usando addEventListener**:
   ```javascript
   window.addEventListener('load', function() {
       // Código a ejecutar
   });
   ```

### Detalles
- **Objetos compatibles**: `window`, `document`, imágenes (`<img>`), frames (`<iframe>`), entre otros.
- **Secuencia de ejecución**: El código dentro del evento `onload` se ejecuta después de que todos los elementos del DOM, CSS, imágenes, y otros recursos han sido completamente cargados.
- **Eventos alternativos**: Para un control más granular, se puede usar el evento `DOMContentLoaded`, que se dispara una vez que el DOM está completamente cargado, sin esperar a que se carguen todos los recursos.

## Ejemplos
### Ejemplo 1: Usando `onload` en HTML
```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <title>Ejemplo de onload</title>
</head>
<body onload="alert('Página cargada!')">
</body>
</html>
```

### Ejemplo 2: Usando `onload` en JavaScript
```javascript
window.onload = function() {
    console.log("La página ha sido cargada completamente.");
};
```

### Ejemplo 3: Usando `addEventListener`
```javascript
window.addEventListener('load', function() {
    document.getElementById('miElemento').innerHTML = "¡Contenido actualizado!";
});
```

## Explicación
Al trabajar con el evento `onload`, es importante tener en cuenta algunos puntos:

- **Ejecutar múltiples funciones**: Si se asigna más de una función al evento `onload` utilizando la notación directa (como `window.onload = ...`), solo se ejecutará la última asignada. Para evitar esto, se recomienda utilizar `addEventListener`.

- **Rendimiento**: El uso excesivo del evento `onload` en recursos pesados puede afectar el rendimiento de la aplicación, ya que hay que esperar a que se carguen todos los elementos. Para un mejor control, considera usar `DOMContentLoaded` para scripts que no dependen de imágenes o recursos externos.

- **Compatibilidad**: `onload` es ampliamente compatible con todos los navegadores modernos, pero siempre es bueno verificar si se necesita soporte para navegadores más antiguos.

## Resumen en una línea
El evento `onload` en JavaScript permite ejecutar código una vez que todos los recursos de una página web han sido completamente cargados.