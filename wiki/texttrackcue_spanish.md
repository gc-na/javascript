<!--
Meta Description: # TextTrackCue en JavaScript: Todo lo que Necesitas Saber ## Sinopsis `TextTrackCue` es una interfaz en JavaScript que representa un texto en una pist...
Meta Keywords: cue, texttrackcue, que, texto, video
-->

# TextTrackCue en JavaScript: Todo lo que Necesitas Saber

## Sinopsis
`TextTrackCue` es una interfaz en JavaScript que representa un texto en una pista de texto (subtítulos o descripciones) asociada a un elemento de video o audio HTML. Permite agregar y manipular subtítulos de manera programática, mejorando la accesibilidad y la experiencia del usuario.

## Documentación
### ¿Qué es `TextTrackCue`?
`TextTrackCue` es parte de la API de HTML5 y se utiliza para crear y gestionar cues (indicadores de texto) dentro de pistas de texto para elementos multimedia. Estos cues son textos que aparecen en pantalla durante la reproducción de un video o audio, proporcionando contexto o traducciones.

### Propósito
El propósito principal de `TextTrackCue` es permitir a los desarrolladores añadir, modificar y eliminar subtítulos o descripciones en tiempo real, lo que facilita la creación de aplicaciones multimedia accesibles.

### Uso
Para utilizar `TextTrackCue`, primero debes crear una instancia de `TextTrackCue` y luego agregarla a una pista de texto. La sintaxis básica es la siguiente:

```javascript
let cue = new TextTrackCue(startTime, endTime, text);
```

- **startTime**: Tiempo en segundos donde el cue debe comenzar.
- **endTime**: Tiempo en segundos donde el cue debe terminar.
- **text**: El texto que se mostrará como subtítulo.

### API
La interfaz `TextTrackCue` incluye varias propiedades que permiten manipular los cues:

- **startTime**: Tiempo de inicio del cue.
- **endTime**: Tiempo de finalización del cue.
- **text**: Texto que representa el cue.
- **track**: La pista de texto a la que pertenece el cue.

## Ejemplos
### Ejemplo Básico
A continuación se muestra un ejemplo simple de cómo crear y agregar un cue a un elemento de video:

```html
<video id="video" controls>
  <source src="video.mp4" type="video/mp4">
  <track id="track" kind="subtitles" srclang="es" label="Español">
</video>

<script>
  const video = document.getElementById('video');
  const track = document.getElementById('track').track;

  const cue = new TextTrackCue(0, 5, "¡Hola! Este es un subtítulo.");
  track.addCue(cue);
</script>
```

### Ejemplo de Modificación de un Cue
Puedes modificar un cue existente de la siguiente manera:

```javascript
cue.text = "¡Hola! Este subtítulo ha sido modificado.";
```

## Explicación
### Errores Comunes
- **No agregar cues a la pista**: Asegúrate de que los cues se agreguen a la pista de texto correspondiente utilizando el método `addCue()`.
- **Tiempos incorrectos**: Verifica que los tiempos de inicio y fin sean correctos y no se superpongan con otros cues.

### Notas Adicionales
- Los cues deben ser eliminados manualmente si ya no son necesarios, utilizando el método `removeCue()`.
- `TextTrackCue` es especialmente útil para aplicaciones que requieren accesibilidad, como la inclusión de subtítulos en diferentes idiomas.

## Resumen en una Línea
`TextTrackCue` es una interfaz de JavaScript que permite crear y gestionar subtítulos en pistas de texto para elementos multimedia HTML, mejorando la accesibilidad del contenido.