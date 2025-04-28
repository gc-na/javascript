<!--
Meta Description: # SpeechSynthesis in JavaScript: Text-to-Speech für Webanwendungen ## Synopsis SpeechSynthesis ist eine Web API in JavaScript, die es Entwicklern ermö...
Meta Keywords: die, sie, speechsynthesis, der, und
-->

# SpeechSynthesis in JavaScript: Text-to-Speech für Webanwendungen

## Synopsis
SpeechSynthesis ist eine Web API in JavaScript, die es Entwicklern ermöglicht, Texte in Sprache umzuwandeln. Diese Funktion eröffnet neue Möglichkeiten für barrierefreie Anwendungen und interaktive Benutzererlebnisse.

## Dokumentation
Die SpeechSynthesis API gehört zur Web Speech API und ist ein wesentlicher Bestandteil moderner Webanwendungen. Mit dieser API können Sie Text in Sprache umwandeln und verschiedene Stimmen und Sprachen nutzen. Die API besteht hauptsächlich aus der `SpeechSynthesis`-Klasse und der `SpeechSynthesisUtterance`-Klasse.

### Zweck
Der Hauptzweck der SpeechSynthesis API ist es, die Interaktion zwischen Benutzern und Anwendungen durch Sprachsynthese zu verbessern. Sie ist besonders nützlich für:
- Barrierefreiheit: Unterstützung für sehbehinderte Benutzer.
- Lernanwendungen: Vorlesen von Texten zur Verbesserung des Leseverständnisses.
- Interaktive Anwendungen: Sprachbasierte Benutzeroberflächen.

### Verwendung
Um die SpeechSynthesis API zu verwenden, müssen Sie zunächst eine Instanz von `SpeechSynthesisUtterance` erstellen und dann diese Instanz an die SpeechSynthesis-Instanz übergeben. Hier sind die grundlegenden Schritte:

1. **Erstellen Sie eine Instanz von SpeechSynthesisUtterance**:
   ```javascript
   const utterance = new SpeechSynthesisUtterance('Hallo, Welt!');
   ```

2. **Wählen Sie eine Stimme aus (optional)**:
   Sie können eine spezifische Stimme auswählen, die in der Browsersprache verfügbar ist.

3. **Starten Sie die Sprachausgabe**:
   ```javascript
   window.speechSynthesis.speak(utterance);
   ```

### Details
- **Stimmen**: Die API bietet eine Vielzahl von Stimmen, die je nach Browser und Betriebssystem variieren können. Sie können die verfügbaren Stimmen mit `speechSynthesis.getVoices()` abrufen.
- **Sprache**: Stellen Sie die Sprache der Sprachausgabe mit der `lang`-Eigenschaft der `SpeechSynthesisUtterance`-Instanz ein.
- **Ereignisse**: Sie können Ereignisse wie `onend`, `onstart` und `onerror` verwenden, um auf verschiedene Zustände der Sprachausgabe zu reagieren.

## Beispiele

### Einfaches Beispiel
Ein einfaches Beispiel zur Verwendung von SpeechSynthesis:
```javascript
const utterance = new SpeechSynthesisUtterance('Willkommen auf meiner Website!');
window.speechSynthesis.speak(utterance);
```

### Auswahl einer Stimme
Hier ist ein Beispiel, wie Sie eine spezifische Stimme auswählen können:
```javascript
const utterance = new SpeechSynthesisUtterance('Das ist ein Beispiel mit einer bestimmten Stimme.');
const voices = window.speechSynthesis.getVoices();
utterance.voice = voices[0]; // Wählen Sie die erste verfügbare Stimme
window.speechSynthesis.speak(utterance);
```

## Erklärung
Ein häufiges Problem bei der Verwendung der SpeechSynthesis API ist, dass nicht alle Browser die gleiche Anzahl an Stimmen unterstützen. Es kann auch zu Verzögerungen kommen, wenn Stimmen geladen werden. Ein weiterer häufiger Stolperstein ist das Timing der Sprachausgabe, wenn sie sofort nach dem Laden der Seite gestartet wird. Stellen Sie sicher, dass die Stimmen geladen sind, bevor Sie die Sprachausgabe initiieren, indem Sie auf das `voiceschanged`-Ereignis warten.

## Ein Satz Zusammenfassung
Die SpeechSynthesis API in JavaScript ermöglicht es Entwicklern, Texte in Sprache umzuwandeln und so interaktive und barrierefreie Webanwendungen zu erstellen.