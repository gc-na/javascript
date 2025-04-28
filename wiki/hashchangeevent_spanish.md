<!--
Meta Description: # Evento HashChange en JavaScript: Comprendiendo el Cambio de Hash en URLs ## Sinopsis El evento `HashChange` en JavaScript permite detectar cambios e...
Meta Keywords: hash, evento, hashchange, para, url
-->

# Evento HashChange en JavaScript: Comprendiendo el Cambio de Hash en URLs

## Sinopsis
El evento `HashChange` en JavaScript permite detectar cambios en la parte del hash de la URL de una página web, facilitando la creación de aplicaciones de una sola página (SPA) y la navegación sin recargas.

## Documentación

### Propósito
El evento `HashChange` se utiliza para escuchar y reaccionar a los cambios en la parte del hash de la URL del navegador (es decir, la parte que sigue al símbolo `#`). Es especialmente útil para aplicaciones que utilizan el hash para manejar estados o secciones, permitiendo una experiencia de usuario más fluida sin tener que recargar la página.

### Uso
Para utilizar el evento `HashChange`, se debe agregar un listener al objeto `window` que escuche el evento `hashchange`. Este listener se ejecutará cada vez que cambie el hash de la URL.

#### Sintaxis
```javascript
window.addEventListener('hashchange', function(event) {
    // Código a ejecutar cuando el hash cambie
});
```

### Detalles
- **Compatibilidad**: El evento `HashChange` es compatible con la mayoría de los navegadores modernos, aunque se recomienda verificar la compatibilidad para versiones más antiguas.
- **Propiedades del Evento**: El objeto del evento `HashChangeEvent` tiene las siguientes propiedades:
  - `oldURL`: La URL anterior antes del cambio de hash.
  - `newURL`: La URL nueva después del cambio de hash.

## Ejemplos

### Ejemplo Básico
```javascript
// Agregar un listener para el evento hashchange
window.addEventListener('hashchange', function(event) {
    console.log('URL anterior:', event.oldURL);
    console.log('Nueva URL:', event.newURL);
});

// Cambiar el hash de la URL
location.hash = 'nueva-seccion';
```

### Ejemplo con Navegación
```javascript
// Función para cargar contenido basado en el hash
function cargarContenido() {
    const seccion = location.hash.substring(1); // Obtener el hash sin el '#'
    const contenido = document.getElementById('contenido');
    
    if (seccion === 'inicio') {
        contenido.innerHTML = '<h1>Inicio</h1>';
    } else if (seccion === 'acerca') {
        contenido.innerHTML = '<h1>Acerca de</h1>';
    } else {
        contenido.innerHTML = '<h1>Página no encontrada</h1>';
    }
}

// Escuchar cambios en el hash
window.addEventListener('hashchange', cargarContenido);

// Cargar contenido inicial
cargarContenido();
```

## Explicación

### Errores Comunes
- **No escuchar el evento**: Si no se agrega un listener para el evento `hashchange`, el código que depende de este evento no se ejecutará.
- **Modificar el hash sin intención**: Cambiar el hash de la URL sin un propósito claro puede llevar a una experiencia de usuario confusa.

### Notas Adicionales
- Es recomendable usar el evento `hashchange` solo para cambios en el hash, y no para otras partes de la URL.
- Para aplicaciones más complejas, considera usar la API de `History` junto con `hashchange` para un control más fino sobre la navegación del estado.

## Resumen en Una Línea
El evento `HashChange` en JavaScript permite detectar y responder a cambios en el hash de la URL, facilitando la navegación en aplicaciones web sin recargas.