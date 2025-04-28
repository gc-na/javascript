<!--
Meta Description: # oncuechange en JavaScript: Comprendiendo el Evento de Cambio de Cue ## Sinopsis El evento `oncuechange` en JavaScript se utiliza para detectar cambi...
Meta Keywords: video, evento, oncuechange, los, que
-->

# oncuechange en JavaScript: Comprendiendo el Evento de Cambio de Cue

## Sinopsis
El evento `oncuechange` en JavaScript se utiliza para detectar cambios en la pista de subtítulos o descripciones en elementos multimedia, como `<video>` o `<audio>`. Este evento permite a los desarrolladores reaccionar a los cambios en el estado de los cues, mejorando la interactividad y la accesibilidad de las aplicaciones web.

## Documentación
### Propósito
El evento `oncuechange` se activa cuando hay un cambio en el cue actual que se está mostrando en relación con los subtítulos o descripciones de un medio. Esto es útil para implementar lógica adicional, como mostrar u ocultar información en la interfaz de usuario cuando un nuevo cue aparece.

### Uso
Para utilizar el evento `oncuechange`, se debe adjuntar un manejador de eventos al elemento multimedia. El evento se puede escuchar de la siguiente manera:

```javascript
const videoElement = document.querySelector('video');

videoElement.oncuechange = function() {
    // Lógica a ejecutar cuando cambia el cue
    const activeCues = videoElement.textTracks[0].activeCues;
    if (activeCues.length > 0) {
        console.log(activeCues[0].text); // Muestra el texto del cue activo
    }
};
```

### Detalles
- **Elemento objetivo**: Este evento se aplica a los elementos `<video>` y `<audio>` que contienen pistas de texto.
- **Compatibilidad**: Asegúrate de que el navegador en uso soporte el objeto `TextTrack` y el evento `oncuechange`, ya que no todos los navegadores pueden tener el mismo nivel de soporte.

## Ejemplos
### Ejemplo básico
```html
<video controls>
    <source src="video.mp4" type="video/mp4">
    <track kind="subtitles" src="subtitles.vtt" srclang="es" label="Español">
    Tu navegador no soporta el elemento de video.
</video>

<script>
    const video = document.querySelector('video');
    video.oncuechange = function() {
        const cues = video.textTracks[0].activeCues;
        if (cues.length > 0) {
            console.log(cues[0].text); // Muestra el texto del cue activo
        }
    };
</script>
```

### Ejemplo avanzado
```html
<video controls>
    <source src="video.mp4" type="video/mp4">
    <track kind="descriptions" src="descriptions.vtt" srclang="es" label="Descripciones">
    Tu navegador no soporta el elemento de video.
</video>

<div id="description"></div>

<script>
    const video = document.querySelector('video');
    const descriptionDiv = document.getElementById('description');

    video.oncuechange = function() {
        const cues = video.textTracks[0].activeCues;
        descriptionDiv.innerHTML = cues.length > 0 ? cues[0].text : '';
    };
</script>
```

## Explicación
Al trabajar con `oncuechange`, es importante tener en cuenta que:
- **Soporte de navegador**: No todos los navegadores pueden manejar el evento de la misma manera, así que siempre verifica la compatibilidad.
- **Pistas de texto**: Asegúrate de que el medio tenga pistas de texto adecuadas definidas para que el evento funcione.
- **Accesibilidad**: Usar este evento puede mejorar la accesibilidad para usuarios que dependen de subtítulos o descripciones.

## Resumen en una línea
El evento `oncuechange` en JavaScript permite reaccionar a los cambios en los cues de subtítulos o descripciones en elementos multimedia, mejorando la interactividad en aplicaciones web.