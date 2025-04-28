<!--
Meta Description: # webkitSpeechGrammarList: Todo lo que necesitas saber sobre esta característica de JavaScript para el reconocimiento de voz ## Sinopsis `webkitSpeech...
Meta Keywords: voz, webkitspeechgrammarlist, reconocimiento, una, que
-->

# webkitSpeechGrammarList: Todo lo que necesitas saber sobre esta característica de JavaScript para el reconocimiento de voz

## Sinopsis
`webkitSpeechGrammarList` es una interfaz de JavaScript que permite a los desarrolladores definir gramáticas personalizadas para mejorar el reconocimiento de voz en aplicaciones web, facilitando la interacción por voz en navegadores compatibles.

## Documentación
### Propósito
`webkitSpeechGrammarList` se utiliza en el contexto de la API de reconocimiento de voz (Speech Recognition API) en navegadores web. Permite a los desarrolladores especificar gramáticas que guían el reconocimiento de palabras y frases, mejorando la precisión en la interpretación de comandos de voz.

### Uso
Para utilizar `webkitSpeechGrammarList`, primero es necesario instanciar el objeto `SpeechRecognition`. A continuación, se puede crear una lista de gramáticas y añadirlas a la propiedad `grammars` del objeto de reconocimiento. Es importante notar que `webkitSpeechGrammarList` es una propiedad específica de WebKit y puede no estar disponible en todos los navegadores.

### Detalles
- **Constructor**: `webkitSpeechGrammarList()`
- **Propiedad**: `grammars` - Permite almacenar un conjunto de gramáticas para el reconocimiento de voz.
- **Métodos**: 
  - `addFromString(grammar: string, weight: number)`: Añade una gramática en formato de cadena.
  - `addFromURI(uri: string, weight: number)`: Añade una gramática desde una URI.

## Ejemplos
### Ejemplo básico de uso
```javascript
// Verificamos si la API de reconocimiento de voz es compatible
if ('webkitSpeechRecognition' in window) {
    var recognition = new webkitSpeechRecognition();
    recognition.continuous = true;
    recognition.interimResults = true;

    // Creamos una lista de gramáticas
    var grammarList = new webkitSpeechGrammarList();
    var grammar = '#JSGF V1.0; grammar colors; public <color> = rojo | azul | verde ;';
    grammarList.addFromString(grammar, 1);

    recognition.grammars = grammarList;

    recognition.onresult = function(event) {
        var lastResult = event.results[event.results.length - 1];
        console.log('Resultado: ' + lastResult[0].transcript);
    };

    recognition.start();
} else {
    console.log('API de reconocimiento de voz no soportada.');
}
```

## Explicación
### Errores comunes
- **Compatibilidad de navegadores**: `webkitSpeechGrammarList` es específico de navegadores basados en WebKit, como Chrome, y puede no funcionar en otros navegadores. Es recomendable verificar la compatibilidad antes de implementar.
- **Formato de gramática**: Asegúrate de que la gramática esté en el formato correcto, siguiendo la sintaxis de JSGF (Java Speech Grammar Format).
- **Limitaciones de la API**: La API puede no funcionar correctamente en entornos con mucho ruido o con acentos pronunciados que no estén bien definidos en las gramáticas.

## Resumen en una línea
`webkitSpeechGrammarList` es una interfaz de JavaScript que permite definir gramáticas personalizadas para el reconocimiento de voz, mejorando la precisión en la interpretación de comandos de voz en aplicaciones web.