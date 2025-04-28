<!--
Meta Description: # ScriptProcessorNode in JavaScript: Echtzeit-Audioverarbeitung im Web ## Synopsis Der `ScriptProcessorNode` ist ein wichtiges Audio-API-Element in Ja...
Meta Keywords: der, die, audio, sie, scriptprocessornode
-->

# ScriptProcessorNode in JavaScript: Echtzeit-Audioverarbeitung im Web

## Synopsis
Der `ScriptProcessorNode` ist ein wichtiges Audio-API-Element in JavaScript, das Entwicklern ermöglicht, Audio in Echtzeit zu verarbeiten. Es handelt sich um eine flexible Lösung für die Audioverarbeitung, die insbesondere für Anwendungen in der Web-Audio-API von Bedeutung ist.

## Documentation
Der `ScriptProcessorNode` wird verwendet, um Audio-Daten zu verarbeiten, während sie in einem Audio-Stream fließen. Er ermöglicht es Entwicklern, benutzerdefinierte Audiobearbeitungsalgorithmen zu implementieren, die auf die Daten im Zeitverlauf reagieren können. 

### Zweck
Der Hauptzweck des `ScriptProcessorNode` besteht darin, Echtzeit-Audioverarbeitung zu ermöglichen, die auf die spezifischen Bedürfnisse einer Anwendung zugeschnitten ist. Dies kann die Manipulation von Audio-Daten, das Erstellen von Effekten oder die Implementierung von Synthese-Techniken umfassen.

### Verwendung
Um einen `ScriptProcessorNode` zu verwenden, benötigen Sie zunächst einen `AudioContext`. Der Knoten kann dann erstellt und in den Audio-Graph integriert werden. Hier ist ein einfaches Beispiel, um zu zeigen, wie man ihn einrichtet:

```javascript
// Erstellen eines AudioContext
const audioContext = new (window.AudioContext || window.webkitAudioContext)();

// Erstellen eines ScriptProcessorNode
const scriptProcessor = audioContext.createScriptProcessor(4096, 1, 1);

// Definieren der Audio-Verarbeitungsfunktion
scriptProcessor.onaudioprocess = function(event) {
    const inputBuffer = event.inputBuffer.getChannelData(0);
    const outputBuffer = event.outputBuffer.getChannelData(0);
    
    for (let i = 0; i < inputBuffer.length; i++) {
        // Einfache Verarbeitung: Kopieren der Eingabedaten ins Ausgangspuffer
        outputBuffer[i] = inputBuffer[i];
    }
};

// Anschließen des ScriptProcessorNode an den AudioContext
scriptProcessor.connect(audioContext.destination);
```

### Details
- **Buffer-Größe:** Der erste Parameter von `createScriptProcessor` gibt die Größe des Buffer an, während die zweiten beiden Parameter die Anzahl der Eingangs- und Ausgangskanäle definieren.
- **onaudioprocess:** Eine Callback-Funktion, die aufgerufen wird, wenn der Audio-Buffer bereit ist, verarbeitet zu werden. Hier können Sie Ihre Audioverarbeitungslogik implementieren.

## Examples
Hier sind einige grundlegende Anwendungsbeispiele für den `ScriptProcessorNode`:

1. **Einfache Echo-Effekte:**
   Sie können einen Echo-Effekt implementieren, indem Sie die Ausgabedaten verzögert zurück in den Eingang buffer schreiben.

2. **Audio-Filter:**
   Erstellen Sie benutzerdefinierte Audiofilter, indem Sie die Eingabewerte modifizieren, bevor Sie sie in den Ausgang buffer schreiben.

3. **Synthese:**
   Erzeugen Sie synthetische Klänge durch Manipulation der Audio-Daten in der `onaudioprocess`-Funktion.

## Explanation
**Häufige Fallstricke:**
- **Leistung:** Übermäßige Verarbeitung in `onaudioprocess` kann zu Störungen und Verzögerungen im Audio führen. Halten Sie die Verarbeitung so einfach und effizient wie möglich.
- **Veraltet:** Beachten Sie, dass der `ScriptProcessorNode` als veraltet gilt und durch den `AudioWorkletNode` ersetzt werden sollte, der eine bessere Leistung und Flexibilität bietet.

**Zusätzliche Hinweise:**
- Der `ScriptProcessorNode` ist nicht für produktive Anwendungen empfohlen, da seine Nutzung in modernen Webanwendungen durch `AudioWorklet` ersetzt wird, das eine bessere Kontrolle und Performance bietet.

## One Line Summary
Der `ScriptProcessorNode` in JavaScript ermöglicht die Echtzeit-Verarbeitung von Audiodaten, ist jedoch veraltet und sollte durch den `AudioWorkletNode` ersetzt werden.