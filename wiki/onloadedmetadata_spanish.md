<!--
Meta Description: # Evento onloadedmetadata en JavaScript: Todo lo que Necesitas Saber ## Sinopsis El evento `onloadedmetadata` en JavaScript es un evento crucial que s...
Meta Keywords: video, que, evento, audio, onloadedmetadata
-->

# Evento onloadedmetadata en JavaScript: Todo lo que Necesitas Saber

## Sinopsis
El evento `onloadedmetadata` en JavaScript es un evento crucial que se dispara cuando la información de metadatos de un recurso multimedia, como un video o audio, ha sido cargada. Este evento permite a los desarrolladores manejar dinámicamente los datos relacionados con el contenido multimedia.

## Documentación
### Propósito
El evento `onloadedmetadata` se utiliza para ejecutar código cuando se han cargado los metadatos de un elemento `<video>` o `<audio>`. Estos metadatos incluyen información como la duración del medio, las dimensiones de un video y otros datos relevantes.

### Uso
Para utilizar el evento `onloadedmetadata`, sigue estos pasos:

1. **Selecciona el elemento multimedia**: Obtén una referencia al elemento `<video>` o `<audio>` en tu documento HTML.
2. **Agrega un listener**: Usa `addEventListener` para escuchar el evento `loadedmetadata`.
3. **Define la función de manejo**: Crea una función que se ejecutará cuando el evento ocurra.

### Detalles
El evento se dispara una vez que se han cargado los metadatos, pero antes de que el medio esté listo para ser reproducido. Esto significa que puedes acceder a propiedades como `duration` y `videoWidth` inmediatamente después de que se dispare el evento.

## Ejemplos
### Ejemplo Básico de Uso
```html
<video id="miVideo" controls>
    <source src="video.mp4" type="video/mp4">
    Tu navegador no soporta el elemento de video.
</video>

<script>
    const video = document.getElementById('miVideo');
    video.addEventListener('loadedmetadata', function() {
        console.log('Duración del video:', video.duration);
        console.log('Ancho del video:', video.videoWidth);
        console.log('Alto del video:', video.videoHeight);
    });
</script>
```

### Ejemplo con Audio
```html
<audio id="miAudio" controls>
    <source src="audio.mp3" type="audio/mp3">
    Tu navegador no soporta el elemento de audio.
</audio>

<script>
    const audio = document.getElementById('miAudio');
    audio.addEventListener('loadedmetadata', function() {
        console.log('Duración del audio:', audio.duration);
    });
</script>
```

## Explicación
### Errores Comunes
- **No usar el evento correctamente**: Asegúrate de que el evento se adjunte después de que el elemento multimedia esté en el DOM.
- **Expectativas incorrectas sobre la carga**: Recuerda que `onloadedmetadata` no significa que el medio esté listo para reproducirse; solo indica que los metadatos están disponibles.

### Notas Adicionales
El evento `onloadedmetadata` es diferente de `oncanplay`, que indica que el medio puede comenzar a reproducirse. Utiliza `onloadedmetadata` para obtener información sobre el contenido antes de la reproducción.

## Resumen en Una Línea
El evento `onloadedmetadata` en JavaScript permite acceder a la información de metadatos de elementos multimedia una vez que han sido cargados.