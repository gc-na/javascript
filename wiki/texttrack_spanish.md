<!--
Meta Description: # TextTrack en JavaScript: Guía Completa ## Sinopsis `TextTrack` es una interfaz de JavaScript que permite la manipulación de pistas de texto en eleme...
Meta Keywords: video, pistas, texto, que, texttrack
-->

# TextTrack en JavaScript: Guía Completa

## Sinopsis
`TextTrack` es una interfaz de JavaScript que permite la manipulación de pistas de texto en elementos de medios HTML, como subtítulos y descripciones. Esta funcionalidad es crucial para mejorar la accesibilidad y la experiencia del usuario en aplicaciones multimedia.

## Documentación

### Propósito
La interfaz `TextTrack` es parte de la API de HTML5 y permite acceder a las pistas de texto asociadas con elementos `<video>` y `<audio>`. Estas pistas pueden incluir subtítulos, descripciones, y otros tipos de texto que acompañan al contenido multimedia.

### Uso
Para utilizar `TextTrack`, primero debes asegurarte de que un elemento de video o audio tenga asociadas pistas de texto. Estas pistas se pueden agregar utilizando el elemento `<track>`, que permite especificar el tipo de texto y el idioma.

#### Estructura básica de un elemento `<video>` con pistas de texto:
```html
<video controls>
    <source src="video.mp4" type="video/mp4">
    <track src="subtitulos.vtt" kind="subtitles" srclang="es" label="Español">
    Tu navegador no soporta videos HTML5.
</video>
```

### Accediendo a `TextTrack` en JavaScript
Puedes acceder a las pistas de texto a través de la propiedad `textTracks` de un elemento `<video>` o `<audio>`. Esto retorna una lista de objetos `TextTrack`.

```javascript
const video = document.querySelector('video');
const textTracks = video.textTracks;

for (let i = 0; i < textTracks.length; i++) {
    console.log(textTracks[i].label); // Muestra la etiqueta de cada pista de texto
}
```

## Ejemplos

### Ejemplo 1: Listar Pistas de Texto
```javascript
const video = document.querySelector('video');

video.addEventListener('loadedmetadata', () => {
    const tracks = video.textTracks;
    for (let track of tracks) {
        console.log(`Tipo: ${track.kind}, Lenguaje: ${track.srclang}, Etiqueta: ${track.label}`);
    }
});
```

### Ejemplo 2: Habilitar y Deshabilitar Pistas
```javascript
const video = document.querySelector('video');
const tracks = video.textTracks;

function toggleSubtitles() {
    for (let track of tracks) {
        track.mode = (track.mode === 'showing') ? 'hidden' : 'showing';
    }
}

document.getElementById('toggle-button').addEventListener('click', toggleSubtitles);
```

## Explicación
Al utilizar `TextTrack`, es importante tener en cuenta que:

- **Compatibilidad**: No todos los navegadores pueden soportar las mismas características de `TextTrack`, por lo que se recomienda verificar la compatibilidad.
- **Modos de Pista**: Las pistas pueden tener diferentes modos: `disabled`, `hidden` y `showing`. Asegúrate de configurar correctamente el modo para que las pistas se muestren o se oculten según sea necesario.
- **Carga de Pistas**: Asegúrate de que las pistas de texto estén correctamente cargadas antes de intentar acceder a ellas, lo que generalmente se puede manejar mediante eventos como `loadedmetadata`.

## Resumen en una Línea
`TextTrack` es una interfaz de JavaScript que permite gestionar y manipular pistas de texto en elementos de medios HTML, mejorando la accesibilidad del contenido multimedia.