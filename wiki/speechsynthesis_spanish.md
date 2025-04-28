<!--
Meta Description: # SpeechSynthesis en JavaScript: Guía Completa para Conversión de Texto a Voz ## Sinopsis SpeechSynthesis es una interfaz de la Web Speech API en Java...
Meta Keywords: voz, speechsynthesis, utterance, texto, que
-->

# SpeechSynthesis en JavaScript: Guía Completa para Conversión de Texto a Voz

## Sinopsis
SpeechSynthesis es una interfaz de la Web Speech API en JavaScript que permite la conversión de texto a voz en aplicaciones web. Facilita la creación de experiencias interactivas y accesibles al permitir que el contenido sea leído en voz alta.

## Documentación
### Propósito
La interfaz SpeechSynthesis permite a los desarrolladores integrar capacidades de síntesis de voz en sus aplicaciones web, mejorando la accesibilidad y ofreciendo una forma interactiva de presentar información.

### Uso
Para utilizar SpeechSynthesis, primero se debe crear una instancia de la clase `SpeechSynthesisUtterance`, que representa el texto que se desea convertir a voz. Luego, se utiliza el método `speak()` de la interfaz `speechSynthesis` para iniciar la lectura.

### Detalles
- **Crear un objeto `SpeechSynthesisUtterance`**: Este objeto representa el texto que se desea pronunciar y puede incluir propiedades como `lang`, `pitch`, `rate` y `volume` para personalizar la salida de voz.
  
- **Métodos clave**:
  - `speak()`: Inicia la reproducción del texto.
  - `cancel()`: Detiene cualquier síntesis de voz en curso.
  - `pause()`: Pausa la síntesis de voz.
  - `resume()`: Reanuda la síntesis de voz pausada.

- **Propiedades**:
  - `text`: El texto que se pronunciará.
  - `lang`: El idioma de la voz.
  - `volume`: El volumen de la voz (0 a 1).
  - `rate`: La velocidad de la voz (0.1 a 10).
  - `pitch`: El tono de la voz (0 a 2).

## Ejemplos
### Ejemplo Básico
```javascript
const utterance = new SpeechSynthesisUtterance('Hola, bienvenido a la guía de SpeechSynthesis en JavaScript.');
speechSynthesis.speak(utterance);
```

### Ejemplo con Propiedades Personalizadas
```javascript
const utterance = new SpeechSynthesisUtterance('Este es un ejemplo de voz personalizada.');
utterance.lang = 'es-ES';
utterance.volume = 1; // Máximo volumen
utterance.rate = 1;   // Velocidad normal
utterance.pitch = 1;  // Tono normal
speechSynthesis.speak(utterance);
```

### Ejemplo de Pausar y Reanudar
```javascript
const utterance = new SpeechSynthesisUtterance('Este texto se pausará en 3 segundos.');
speechSynthesis.speak(utterance);

setTimeout(() => {
    speechSynthesis.pause();
    setTimeout(() => {
        speechSynthesis.resume();
    }, 2000); // Reanuda después de 2 segundos
}, 3000); // Pausa después de 3 segundos
```

## Explicación
- **Compatibilidad**: No todos los navegadores son compatibles con la API de SpeechSynthesis. Es importante verificar la compatibilidad antes de implementar esta funcionalidad en una aplicación.
  
- **Voces disponibles**: Las voces disponibles pueden variar entre los navegadores y sistemas operativos. Se puede utilizar `speechSynthesis.getVoices()` para listar las voces disponibles en el navegador actual.

- **Eventos**: La interfaz `SpeechSynthesisUtterance` también permite el uso de eventos como `onend`, `onerror`, y `onpause` para manejar la lógica de la aplicación durante la síntesis de voz.

- **Problemas comunes**: Un error común es no verificar si hay voces disponibles antes de intentar hablar. Asegúrate de llamar a `getVoices()` y esperar a que el array esté listo.

## Resumen en una Línea
SpeechSynthesis es una poderosa herramienta de JavaScript que permite convertir texto a voz, mejorando la accesibilidad y la interactividad en aplicaciones web.