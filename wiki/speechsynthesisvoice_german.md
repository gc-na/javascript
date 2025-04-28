<!--
Meta Description: # SpeechSynthesisVoice in JavaScript: Text-to-Speech mit Sprachsynthese ## Synopsis `SpeechSynthesisVoice` ist eine Schnittstelle der Web Speech API i...
Meta Keywords: die, der, stimmen, stimme, speechsynthesisvoice
-->

# SpeechSynthesisVoice in JavaScript: Text-to-Speech mit Sprachsynthese

## Synopsis
`SpeechSynthesisVoice` ist eine Schnittstelle der Web Speech API in JavaScript, die Informationen über verfügbare Stimmen für die Sprachsynthese bereitstellt und es Entwicklern ermöglicht, Text in Sprache umzuwandeln.

## Documentation
### Zweck
Die `SpeechSynthesisVoice`-Schnittstelle ermöglicht es Entwicklern, verschiedene Stimmen zu nutzen, die von der Sprachsynthese-Engine des Browsers unterstützt werden. Jede Stimme hat spezifische Eigenschaften wie Name, Sprache, und Geschlecht, die bei der Auswahl der richtigen Stimme für die Text-to-Speech-Anwendung helfen.

### Nutzung
Um `SpeechSynthesisVoice` zu verwenden, müssen Sie zunächst die verfügbaren Stimmen mit der `speechSynthesis.getVoices()`-Methode abrufen. Diese Methode gibt ein Array von `SpeechSynthesisVoice`-Objekten zurück, die dann zur Konfiguration der Sprachsynthese verwendet werden können.

#### Eigenschaften
- **name**: Der Name der Stimme.
- **lang**: Die Sprache, in der die Stimme spricht.
- **localService**: Ein Boolean, der angibt, ob die Stimme lokal verfügbar ist.
- **default**: Ein Boolean, der angibt, ob die Stimme die Standardstimme ist.

### Beispiel
Hier ist ein einfaches Beispiel, wie man `SpeechSynthesisVoice` in einer Webanwendung nutzen kann:

```javascript
// Funktion zum Abrufen und Auflisten der verfügbaren Stimmen
function listVoices() {
    const voices = speechSynthesis.getVoices();
    voices.forEach(voice => {
        console.log(`Stimme: ${voice.name}, Sprache: ${voice.lang}`);
    });
}

// Warten, bis die Stimmen geladen sind
speechSynthesis.onvoiceschanged = listVoices;

// Text-to-Speech mit einer bestimmten Stimme
function speak(text) {
    const utterance = new SpeechSynthesisUtterance(text);
    // Stimme auswählen
    const voices = speechSynthesis.getVoices();
    utterance.voice = voices.find(voice => voice.name === 'Google Deutsch');

    speechSynthesis.speak(utterance);
}

// Beispielaufruf
speak('Hallo, wie geht es Ihnen?');
```

## Erklärung
Ein häufiges Problem bei der Verwendung von `SpeechSynthesisVoice` ist, dass die Stimmen möglicherweise nicht sofort verfügbar sind, wenn Ihr Skript geladen wird. Daher ist es wichtig, die `onvoiceschanged`-Ereignislistener-Methode zu verwenden, um sicherzustellen, dass die Stimmen vollständig geladen sind, bevor Sie sie verwenden.

Ein weiterer wichtiger Punkt ist, dass die Verfügbarkeit und Anzahl der Stimmen je nach Browser und Betriebssystem variieren können. Stellen Sie sicher, dass Sie Ihre Anwendung in verschiedenen Umgebungen testen, um eine konsistente Benutzererfahrung zu gewährleisten.

## One Line Summary
`SpeechSynthesisVoice` ist eine Schnittstelle in JavaScript, die Entwicklern hilft, verschiedene Stimmen für die Text-to-Speech-Funktionalität zu nutzen.