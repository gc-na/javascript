<!--
Meta Description: # Evento onstorage en JavaScript: Todo lo que Necesitas Saber ## Sinopsis El evento `onstorage` en JavaScript permite a los desarrolladores detectar c...
Meta Keywords: evento, que, onstorage, localstorage, event
-->

# Evento onstorage en JavaScript: Todo lo que Necesitas Saber

## Sinopsis
El evento `onstorage` en JavaScript permite a los desarrolladores detectar cambios en el almacenamiento local del navegador (localStorage) desde diferentes ventanas o pestañas. Es un evento crucial para aplicaciones web que requieren sincronización de datos en tiempo real entre múltiples instancias.

## Documentación
### Propósito
El evento `onstorage` se dispara en la ventana de un navegador cuando se modifica el almacenamiento local en otra ventana o pestaña que utiliza el mismo origen. Esto es especialmente útil para mantener actualizados los datos en aplicaciones web que utilizan `localStorage` para almacenar información en el lado del cliente.

### Uso
El evento `onstorage` se puede manejar de la siguiente manera:

1. **Definir el manejador de eventos**: Puedes asignar una función al evento `storage` en el objeto `window`.
2. **Escuchar el evento**: Al asignar el manejador, este se activará automáticamente cuando ocurra un cambio en `localStorage`.

### Detalles
- **Compatibilidad**: El evento `onstorage` es compatible con la mayoría de los navegadores modernos, incluyendo Chrome, Firefox, Safari y Edge.
- **Acceso a datos**: El evento proporciona acceso a la información que ha cambiado, incluyendo la clave que se ha modificado, el nuevo valor, y el antiguo valor.
- **Ámbito**: El evento no se activa en la misma ventana que realiza el cambio, solo en otras ventanas o pestañas.

## Ejemplos
### Ejemplo Básico de Uso
```javascript
// Escuchar el evento onstorage
window.addEventListener('storage', function(event) {
    console.log('Cambio detectado:');
    console.log('Clave:', event.key);
    console.log('Nuevo valor:', event.newValue);
    console.log('Valor antiguo:', event.oldValue);
});

// Cambiar un valor en localStorage en otra pestaña
localStorage.setItem('nombre', 'Juan');
```

### Ejemplo de Sincronización
```javascript
// Manejador de evento para mostrar cambios en tiempo real
window.addEventListener('storage', function(event) {
    if (event.key === 'contador') {
        document.getElementById('contador').innerText = event.newValue;
    }
});

// Actualizar el contador en otra pestaña
let contador = 0;
setInterval(() => {
    contador++;
    localStorage.setItem('contador', contador);
}, 1000);
```

## Explicación
### Errores Comunes
- **No se dispara en la misma ventana**: Un error común es esperar que el evento se dispare en la misma ventana donde se realiza el cambio. Esto no sucede; el evento solo se activa en otras ventanas o pestañas.
- **Olvidar manejar datos nulos**: Al trabajar con `localStorage`, es importante verificar que las claves y los valores no sean nulos para evitar errores en la aplicación.

### Notas Adicionales
- **Performance**: Usar `localStorage` y el evento `onstorage` puede ser costoso en términos de rendimiento si se realizan muchas operaciones en un corto período de tiempo. Se recomienda usarlo con moderación.
- **Limitaciones de almacenamiento**: Ten en cuenta que el almacenamiento local tiene un límite de tamaño (generalmente alrededor de 5-10 MB), y esto puede variar según el navegador.

## Resumen en Una Línea
El evento `onstorage` en JavaScript permite detectar cambios en el almacenamiento local desde diferentes ventanas o pestañas, facilitando la sincronización de datos en aplicaciones web.