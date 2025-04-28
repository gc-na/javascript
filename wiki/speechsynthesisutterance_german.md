<!--
Meta Description: # SpeechSynthesisUtterance in JavaScript: Text-to-Speech im Web ## Synopsis `SpeechSynthesisUtterance` ist ein JavaScript-Objekt, das es Entwicklern e...
Meta Keywords: die, speechsynthesisutterance, text, und, ist
-->

# SpeechSynthesisUtterance in JavaScript: Text-to-Speech im Web

## Synopsis
`SpeechSynthesisUtterance` ist ein JavaScript-Objekt, das es Entwicklern ermöglicht, Text in Sprache umzuwandeln, indem es die Web Speech API nutzt. Es ist ein entscheidendes Element für die Implementierung von Text-to-Speech-Funktionen in Webanwendungen.

## Dokumentation
`SpeechSynthesisUtterance` ist Teil der Web Speech API und dient zur Speicherung von Text, der in Sprache umgewandelt werden soll. Es ermöglicht Entwicklern, verschiedene Attribute wie Sprache, Lautstärke, Tonhöhe und Sprechgeschwindigkeit festzulegen.

### Verwendung
Um `SpeechSynthesisUtterance` zu verwenden, muss zunächst ein neues Objekt erstellt werden, indem der zu sprechende Text übergeben wird. Danach kann das Objekt an die `SpeechSynthesis`-Instanz übergeben werden, um den Text abzuspielen.

### Attribute
- `text`: Der Text, der in Sprache umgewandelt werden soll.
- `lang`: Die Sprache des Textes (z.B. "de-DE" für Deutsch).
- `volume`: Die Lautstärke des gesprochenen Textes (Werte zwischen 0 und 1).
- `rate`: Die Geschwindigkeit der Sprachausgabe (typischerweise zwischen 0.1 und 10).
- `pitch`: Die Tonhöhe der Stimme (typischerweise zwischen 0 und 2).

### Beispielcode
Hier ist ein einfaches Beispiel für die Verwendung von `SpeechSynthesisUtterance`:

```javascript
// Erstelle eine neue Instanz von SpeechSynthesisUtterance
const utterance = new SpeechSynthesisUtterance("Hallo, willkommen zu meiner Webseite!");

// Setze Sprachattribute
utterance.lang = "de-DE";
utterance.volume = 1; // Voller Lautstärke
utterance.rate = 1; // Normale Geschwindigkeit
utterance.pitch = 1; // Normale Tonhöhe

// Starte die Sprachsynthese
window.speechSynthesis.speak(utterance);
```

## Erklärung
Obwohl `SpeechSynthesisUtterance` relativ einfach zu verwenden ist, gibt es einige häufige Stolpersteine, auf die Entwickler stoßen können:

- **Browserkompatibilität**: Nicht alle Browser unterstützen die Web Speech API. Es ist wichtig, die Unterstützung für die Zielbrowser zu überprüfen.
- **Zugriffsrechte**: Manche Browser erfordern, dass die Sprachausgabe nur in einem Benutzerinteraktionskontext (wie einem Klick-Event) ausgelöst wird.
- **Sprachvariationen**: Die Verfügbarkeit verschiedener Stimmen und Sprachen kann je nach Browser und Betriebssystem unterschiedlich sein.

## Ein-Satz-Zusammenfassung
`SpeechSynthesisUtterance` ist ein JavaScript-Objekt, das es Entwicklern ermöglicht, Text in Sprache umzuwandeln und dabei verschiedene Eigenschaften wie Sprache und Lautstärke anzupassen.