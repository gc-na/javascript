<!--
Meta Description: # SpeechSynthesisVoice en JavaScript: Guía Completa para Desarrolladores ## Sinopsis El objeto `SpeechSynthesisVoice` en JavaScript representa una voz...
Meta Keywords: voz, voces, speechsynthesisvoice, que, speechsynthesis
-->

# SpeechSynthesisVoice en JavaScript: Guía Completa para Desarrolladores

## Sinopsis
El objeto `SpeechSynthesisVoice` en JavaScript representa una voz específica que puede ser utilizada por la API de síntesis de voz (`SpeechSynthesis`). Esta API permite a los desarrolladores implementar funcionalidades de texto a voz en aplicaciones web, mejorando la accesibilidad y la interacción del usuario.

## Documentación

### Propósito
`SpeechSynthesisVoice` es parte de la API de `SpeechSynthesis`, que permite la conversión de texto a voz en navegadores compatibles. Este objeto proporciona información sobre las voces disponibles en el sistema, como su nombre, idioma, y características específicas.

### Uso
Para utilizar `SpeechSynthesisVoice`, primero es necesario acceder a la lista de voces disponibles a través de la propiedad `getVoices()` del objeto `speechSynthesis`. Una vez que tengas la lista, puedes seleccionar una voz específica para utilizarla en la síntesis de voz.

### Detalles
- **Propiedades Principales**:
  - `name`: El nombre de la voz.
  - `lang`: El idioma de la voz (ej., "es-ES" para español de España).
  - `default`: Un booleano que indica si la voz es la predeterminada.
  
- **Métodos**: `SpeechSynthesisVoice` no tiene métodos propios, pero se utiliza junto con el objeto `SpeechSynthesisUtterance` para crear y reproducir el texto.

## Ejemplos

### Ejemplo 1: Listar voces disponibles
```javascript
let voces = [];
speechSynthesis.onvoiceschanged = function() {
    voces = speechSynthesis.getVoices();
    voces.forEach(voz => {
        console.log(`Nombre: ${voz.name}, Idioma: ${voz.lang}`);
    });
};
```

### Ejemplo 2: Sintetizar texto utilizando una voz específica
```javascript
function hablar(texto) {
    const utterance = new SpeechSynthesisUtterance(texto);
    const voces = speechSynthesis.getVoices();
    const voz = voces.find(voz => voz.name === "Google español");

    if (voz) {
        utterance.voice = voz;
    }
    
    speechSynthesis.speak(utterance);
}

hablar("Hola, ¿cómo estás?");
```

## Explicación
Al trabajar con `SpeechSynthesisVoice`, es importante tener en cuenta que la lista de voces puede no estar disponible inmediatamente al cargar la página. Por ello, es recomendable utilizar el evento `onvoiceschanged` para asegurarse de que las voces están listas antes de intentar acceder a ellas. Además, no todos los navegadores ofrecen la misma cantidad de voces o idiomas, lo que puede resultar en una experiencia inconsistente entre diferentes entornos.

## Resumen en una Línea
`SpeechSynthesisVoice` en JavaScript permite acceder a diferentes voces de síntesis de voz, facilitando la implementación de funcionalidades de texto a voz en aplicaciones web.