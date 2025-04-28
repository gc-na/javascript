<!--
Meta Description: # onended: Evento de Finalización en JavaScript ## Sinopsis El evento `onended` en JavaScript se utiliza para detectar cuándo un medio (como audio o v...
Meta Keywords: video, evento, onended, para, audio
-->

# onended: Evento de Finalización en JavaScript

## Sinopsis
El evento `onended` en JavaScript se utiliza para detectar cuándo un medio (como audio o video) ha terminado de reproducirse. Este evento es fundamental para aplicaciones multimedia, permitiendo a los desarrolladores ejecutar acciones específicas tras la finalización de la reproducción.

## Documentación
El evento `onended` es parte de la interfaz `HTMLMediaElement` que se utiliza en elementos como `<audio>` y `<video>`. Cuando se reproduce un archivo multimedia y este llega a su fin, el evento `onended` se activa, permitiendo a los desarrolladores gestionar lo que sucede después de la reproducción.

### Propósito
El propósito del evento `onended` es proporcionar un mecanismo para ejecutar código JavaScript cuando un medio ha terminado de reproducirse, lo que permite implementar funcionalidades como reiniciar la reproducción, mostrar un mensaje, o iniciar otra acción en la interfaz de usuario.

### Uso
Para utilizar el evento `onended`, se puede asignar una función a la propiedad `onended` del elemento multimedia. También se puede utilizar el método `addEventListener` para añadir un manejador de eventos.

### Detalles
- **Tipo de evento**: `Event`
- **Compatibilidad**: Todos los navegadores modernos soportan el evento `onended`.
- **Elemento**: `<audio>`, `<video>`

## Ejemplos

### Ejemplo 1: Usando la propiedad `onended`
```html
<audio id="miAudio" src="cancion.mp3" controls></audio>
<script>
  const audio = document.getElementById('miAudio');
  audio.onended = function() {
    alert('La canción ha terminado de reproducirse.');
  };
</script>
```

### Ejemplo 2: Usando `addEventListener`
```html
<video id="miVideo" src="video.mp4" controls></video>
<script>
  const video = document.getElementById('miVideo');
  video.addEventListener('ended', function() {
    console.log('El video ha finalizado.');
  });
</script>
```

### Ejemplo 3: Reiniciar la reproducción
```html
<video id="miVideo" src="video.mp4" controls></video>
<script>
  const video = document.getElementById('miVideo');
  video.addEventListener('ended', function() {
    video.currentTime = 0; // Reiniciar el video
    video.play(); // Reproducir nuevamente
  });
</script>
```

## Explicación
Al utilizar el evento `onended`, es importante tener en cuenta que:
- **No se activa si el medio se detiene manualmente**: El evento solo se dispara cuando el medio llega al final de su duración.
- **Varios manejadores**: Se pueden agregar múltiples manejadores para el mismo evento utilizando `addEventListener`, lo que permite una mayor flexibilidad en la gestión de eventos.
- **Compatibilidad con otros eventos**: Es recomendable manejar otros eventos relacionados, como `pause` o `ended`, para una mejor experiencia del usuario.

## Resumen en Una Línea
El evento `onended` en JavaScript permite ejecutar acciones específicas cuando un medio finaliza su reproducción, proporcionando control sobre la experiencia multimedia.