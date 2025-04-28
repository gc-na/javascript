<!--
Meta Description: # SpeechSynthesisUtterance: La API de Síntesis de Voz en JavaScript ## Sinopsis `SpeechSynthesisUtterance` es una interfaz de la API de síntesis de vo...
Meta Keywords: voz, speechsynthesisutterance, que, utterance, síntesis
-->

# SpeechSynthesisUtterance: La API de Síntesis de Voz en JavaScript

## Sinopsis
`SpeechSynthesisUtterance` es una interfaz de la API de síntesis de voz en JavaScript que permite crear y gestionar objetos de texto que se convertirán en voz. Esta funcionalidad es parte del conjunto de herramientas de accesibilidad en los navegadores modernos, permitiendo a los desarrolladores integrar la conversión de texto a voz en sus aplicaciones web.

## Documentación

### Propósito
La interfaz `SpeechSynthesisUtterance` es utilizada para representar un texto que se desea convertir en habla. Esta API permite a los desarrolladores especificar el contenido del texto, la voz a utilizar, el idioma, la velocidad y el tono de la voz, facilitando así una experiencia de usuario más rica e inclusiva.

### Uso
Para utilizar `SpeechSynthesisUtterance`, debes seguir estos pasos básicos:

1. **Instanciar el objeto**: Crea una nueva instancia de `SpeechSynthesisUtterance`.
2. **Configurar propiedades**: Ajusta las propiedades como `text`, `lang`, `rate`, `pitch`, y `voice`.
3. **Iniciar la síntesis**: Utiliza el objeto `speechSynthesis` para hablar el texto.

### Detalles
- **Propiedades**:
  - `text`: El texto que se convertirá en voz.
  - `lang`: El idioma de la voz (por ejemplo, "es-ES" para español de España).
  - `rate`: La velocidad de la voz (valor entre 0.1 y 10).
  - `pitch`: El tono de la voz (valor entre 0 y 2).
  - `voice`: La voz específica a utilizar, que puede ser seleccionada de la lista de voces disponibles.

- **Métodos**:
  - `speechSynthesis.speak(utterance)`: Inicia la síntesis de voz.
  - `speechSynthesis.cancel()`: Cancela cualquier síntesis de voz en curso.

## Ejemplos

### Ejemplo Básico
```javascript
// Crear una instancia de SpeechSynthesisUtterance
const utterance = new SpeechSynthesisUtterance("Hola, cómo estás?");

// Establecer propiedades
utterance.lang = "es-ES"; // Español de España
utterance.rate = 1; // Velocidad normal
utterance.pitch = 1; // Tono normal

// Iniciar la síntesis de voz
window.speechSynthesis.speak(utterance);
```

### Ejemplo con Voz Específica
```javascript
// Crear una instancia
const utterance = new SpeechSynthesisUtterance("Bienvenido a nuestro sitio web.");

// Obtener la lista de voces disponibles
const voices = window.speechSynthesis.getVoices();
utterance.voice = voices.find(voice => voice.name === "Google español"); // Seleccionar una voz específica

// Iniciar la síntesis
window.speechSynthesis.speak(utterance);
```

## Explicación
Al trabajar con `SpeechSynthesisUtterance`, es importante tener en cuenta que la disponibilidad de voces varía según el navegador y el sistema operativo. Asegúrate de cargar las voces utilizando `speechSynthesis.onvoiceschanged` para garantizar que obtienes la lista actualizada de voces disponibles.

También, ten presente que algunos navegadores pueden requerir que la síntesis de voz se inicie como resultado de una interacción del usuario, como un clic en un botón, debido a políticas de autoplay.

## Resumen en una línea
`SpeechSynthesisUtterance` es la interfaz en JavaScript que permite convertir texto en voz, mejorando la accesibilidad y la interacción en aplicaciones web.