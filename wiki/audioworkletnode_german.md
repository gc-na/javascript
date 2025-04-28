<!--
Meta Description: # AudioWorkletNode in JavaScript: Eine umfassende Anleitung ## Synopsis Der `AudioWorkletNode` ist ein zentraler Bestandteil der Web Audio API, der es...
Meta Keywords: audioworkletnode, audiocontext, sie, und, channel
-->

# AudioWorkletNode in JavaScript: Eine umfassende Anleitung

## Synopsis
Der `AudioWorkletNode` ist ein zentraler Bestandteil der Web Audio API, der es Entwicklern ermöglicht, benutzerdefinierte Audioprozessierung und -effekte in Echtzeit zu implementieren. Er wird verwendet, um Audioprocessing-Worklets zu erstellen, die die Leistung und Flexibilität der Audiobearbeitung im Web erheblich verbessern.

## Dokumentation
### Zweck
`AudioWorkletNode` wird verwendet, um benutzerdefinierte Audioprozessoren zu erstellen, die in einer Audio-Rendering-Umgebung ausgeführt werden. Im Gegensatz zu `ScriptProcessorNode`, das veraltet ist, bietet `AudioWorkletNode` eine höhere Leistung und genauere Zeitsteuerung.

### Verwendung
Um `AudioWorkletNode` zu verwenden, müssen Sie zunächst eine `AudioWorkletProcessor`-Klasse definieren und diese in das AudioContext laden. Anschließend können Sie einen `AudioWorkletNode` erstellen, um den Prozessor in einem Audiographen zu nutzen.

### Details
1. **Erstellung eines AudioWorkletProcessor**: Sie müssen eine JavaScript-Datei erstellen, die die `AudioWorkletProcessor`-Klasse erweitert und die `process`-Methode implementiert.
2. **AudioContext**: Um den `AudioWorkletNode` zu verwenden, benötigen Sie einen `AudioContext`, in dem Sie den Prozessor registrieren können.
3. **Parameterübergabe**: Über den Konstruktor von `AudioWorkletNode` können Sie Parameter an den Prozessor übergeben, um die Verarbeitung anzupassen.

## Beispiele
### Beispiel 1: Einfacher AudioWorkletNode
```javascript
// Definieren des AudioWorkletProcessors
class MyAudioProcessor extends AudioWorkletProcessor {
  process(inputs, outputs, parameters) {
    const output = outputs[0];
    for (let channel = 0; channel < output.length; ++channel) {
      output[channel].fill(0); // Ausgabe auf Null setzen
    }
    return true; // Weiterverarbeitung erlauben
  }
}

// Registrieren des Processors
registerProcessor('my-audio-processor', MyAudioProcessor);

// Erstellen eines AudioContext und Hinzufügen des Nodes
const audioContext = new AudioContext();
await audioContext.audioWorklet.addModule('my-audio-processor.js');
const myNode = new AudioWorkletNode(audioContext, 'my-audio-processor');
myNode.connect(audioContext.destination);
```

### Beispiel 2: Verwendung von Parametern
```javascript
class GainProcessor extends AudioWorkletProcessor {
  static get parameterDescriptors() {
    return [{
      name: 'gain',
      defaultValue: 1,
      minValue: 0,
      maxValue: 1,
    }];
  }

  process(inputs, outputs, parameters) {
    const output = outputs[0];
    const gain = parameters.gain[0];

    for (let channel = 0; channel < output.length; ++channel) {
      for (let i = 0; i < output[channel].length; ++i) {
        output[channel][i] *= gain; // Gain anwenden
      }
    }
    return true;
  }
}

registerProcessor('gain-processor', GainProcessor);

// Nutzung des GainProcessors
const gainNode = new AudioWorkletNode(audioContext, 'gain-processor', {
  processorOptions: { gain: 0.5 }
});
gainNode.connect(audioContext.destination);
```

## Erklärung
### Häufige Fallstricke
1. **Kompatibilität**: Stellen Sie sicher, dass der Browser `AudioWorklet` unterstützt, da nicht alle Browser diese Funktion übernehmen.
2. **Thread-Sicherheit**: Beachten Sie, dass `AudioWorkletProcessor` im Audio-Rendering-Thread läuft, was bedeutet, dass Sie keine DOM-Operationen oder andere nicht thread-sichere Operationen durchführen sollten.
3. **Verzögerung**: Achten Sie darauf, dass eine falsche Handhabung von Eingangs- und Ausgangsbuffer zu unerwarteten Verzögerungen oder Audioartefakten führen kann.

## Ein-Satz-Zusammenfassung
Der `AudioWorkletNode` ermöglicht die Erstellung und Integration benutzerdefinierter Audioprozessoren in der Web Audio API und bietet Entwicklern eine leistungsstarke Möglichkeit zur Echtzeit-Audiobearbeitung.