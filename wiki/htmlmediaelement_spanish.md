<!--
Meta Description: # HTMLMediaElement en JavaScript: Todo lo que Necesitas Saber ## Sinopsis HTMLMediaElement es una interfaz fundamental en JavaScript que permite a los...
Meta Keywords: video, audio, que, del, htmlmediaelement
-->

# HTMLMediaElement en JavaScript: Todo lo que Necesitas Saber

## Sinopsis
HTMLMediaElement es una interfaz fundamental en JavaScript que permite a los desarrolladores interactuar con medios embebidos en documentos HTML, como audio y video. Proporciona métodos y propiedades que facilitan el control de la reproducción y manipulación de estos elementos multimedia.

## Documentación
HTMLMediaElement es una interfaz que extiende a los elementos de audio y video en HTML5. Permite a los desarrolladores acceder y controlar múltiples aspectos de la reproducción de medios, como la carga, reproducción, pausa, y volumen, entre otros.

### Propósito
El propósito principal de HTMLMediaElement es ofrecer una API unificada para interactuar con medios. Esto incluye la manipulación de propiedades como `currentTime`, `duration`, `paused`, y métodos como `play()`, `pause()`, y `load()`.

### Uso
Para utilizar HTMLMediaElement en JavaScript, se debe acceder a un elemento `<audio>` o `<video>` del DOM. A continuación, se presentan algunas de sus propiedades y métodos más utilizados:

- **Propiedades**:
  - `src`: Establece o devuelve la URL del archivo de audio o video.
  - `currentTime`: Establece o devuelve la posición actual de reproducción (en segundos).
  - `duration`: Devuelve la duración total del medio (en segundos).
  - `paused`: Devuelve un valor booleano que indica si la reproducción está en pausa.

- **Métodos**:
  - `play()`: Inicia la reproducción del medio.
  - `pause()`: Pausa la reproducción del medio.
  - `load()`: Carga el medio en el elemento.

## Ejemplos

### Ejemplo Básico de Uso
```html
<video id="miVideo" width="640" height="360" controls>
  <source src="video.mp4" type="video/mp4">
  Tu navegador no soporta el elemento de video.
</video>

<script>
  const video = document.getElementById('miVideo');
  
  // Reproducir video
  video.play();

  // Pausar video
  video.pause();

  // Obtener la duración del video
  console.log(`Duración del video: ${video.duration} segundos`);
</script>
```

### Ejemplo de Control de Tiempo
```html
<audio id="miAudio" controls>
  <source src="audio.mp3" type="audio/mpeg">
  Tu navegador no soporta el elemento de audio.
</audio>

<script>
  const audio = document.getElementById('miAudio');

  // Establecer el tiempo actual
  audio.currentTime = 30; // Empieza a reproducir desde el segundo 30
</script>
```

## Explicación
Al trabajar con HTMLMediaElement, es importante tener en cuenta algunos aspectos:

- **Compatibilidad del Navegador**: Asegúrate de que el formato del archivo multimedia sea compatible con todos los navegadores que deseas soportar.
- **Eventos**: HTMLMediaElement emite varios eventos (como `play`, `pause`, `ended`, etc.) que puedes utilizar para crear interacciones más avanzadas.
- **CORS**: Si estás cargando medios desde un dominio diferente, puede que necesites configurar correctamente las políticas de CORS para evitar problemas de acceso.

## Resumen en una Línea
HTMLMediaElement es una interfaz en JavaScript que permite controlar y manipular elementos de audio y video en documentos HTML.