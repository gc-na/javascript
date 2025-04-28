<!--
Meta Description: # onhashchange en JavaScript: Maneja Cambios en el Hash de la URL ## Sinopsis El evento `onhashchange` en JavaScript permite a los desarrolladores det...
Meta Keywords: hash, onhashchange, url, para, evento
-->

# onhashchange en JavaScript: Maneja Cambios en el Hash de la URL

## Sinopsis
El evento `onhashchange` en JavaScript permite a los desarrolladores detectar cambios en el fragmento de la URL (hash). Es especialmente útil para aplicaciones de una sola página (SPA) que utilizan hashes para navegar entre diferentes vistas sin recargar la página.

## Documentación
### Propósito
El evento `onhashchange` se activa cuando el fragmento de la URL cambia. Esto es útil para aplicaciones que utilizan el hash para almacenar el estado de la aplicación o para gestionar la navegación entre diferentes secciones.

### Uso
Para utilizar `onhashchange`, se debe asignar una función de controlador que se ejecutará cada vez que se cambie el hash de la URL. Este evento se puede manejar de la siguiente manera:

```javascript
window.onhashchange = function() {
    console.log('El hash ha cambiado a: ' + location.hash);
};
```

### Detalles
- **Compatibilidad**: `onhashchange` es compatible con la mayoría de los navegadores modernos.
- **Propiedad**: `location.hash` devuelve el hash actual de la URL, que incluye el carácter `#`.
- **Desencadenado**: El evento se desencadena cuando se cambia el hash mediante la manipulación de la URL, como `window.location.hash = 'nuevoHash'`.

## Ejemplos
### Ejemplo básico
Aquí hay un ejemplo simple que muestra cómo se puede utilizar el evento `onhashchange`:

```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <title>Ejemplo de onhashchange</title>
</head>
<body>
    <h1>Ejemplo de onhashchange</h1>
    <a href="#seccion1">Sección 1</a>
    <a href="#seccion2">Sección 2</a>
    
    <script>
        window.onhashchange = function() {
            console.log('El hash actual es: ' + location.hash);
            document.body.style.backgroundColor = location.hash === '#seccion1' ? 'lightblue' : 'lightgreen';
        };
    </script>
</body>
</html>
```

### Ejemplo avanzado
En un contexto de SPA, puedes utilizar `onhashchange` para cargar contenido dinámico:

```javascript
window.onhashchange = function() {
    const hash = location.hash.substring(1); // Eliminar el '#'
    cargarContenido(hash);
};

function cargarContenido(seccion) {
    const contenido = document.getElementById('contenido');
    contenido.innerHTML = 'Cargando contenido para: ' + seccion;
}
```

## Explicación
### Errores comunes
- **No detectar cambios**: Si la función `onhashchange` no se activa, asegúrate de que estás cambiando el hash de la URL correctamente.
- **Compatibilidad del navegador**: Algunos navegadores más antiguos pueden no soportar este evento. Para mayor compatibilidad, considera usar `hashchange` como un evento en lugar de asignarlo directamente a `window.onhashchange`.

### Notas adicionales
- `onhashchange` no se activa para cambios en el hash realizados por el usuario, como al hacer clic en enlaces o al escribir directamente en la barra de direcciones, si no se produce un cambio en la URL.
- Si necesitas manejar cambios en la URL de manera más general, considera usar el API de `history` que permite una manipulación más robusta de la historia del navegador.

## Resumen en una línea
El evento `onhashchange` en JavaScript permite detectar y manejar cambios en el fragmento de la URL, facilitando la navegación en aplicaciones de una sola página.