<!--
Meta Description: # WaveShaperNode in JavaScript: Ein Leitfaden für die Audiobearbeitung ## Synopsis Der **WaveShaperNode** ist ein zentraler Bestandteil der Web Audio ...
Meta Keywords: der, audiocontext, die, waveshapernode, erstellen
-->

# WaveShaperNode in JavaScript: Ein Leitfaden für die Audiobearbeitung

## Synopsis
Der **WaveShaperNode** ist ein zentraler Bestandteil der Web Audio API in JavaScript, der es Entwicklern ermöglicht, Audiowellenformen zu formen und zu verzerren, um kreative Klänge zu erzeugen.

## Documentation
### Zweck
Der **WaveShaperNode** wird verwendet, um den Klang eines AudioSignals durch nichtlineare Verzerrungen zu modifizieren. Dies geschieht durch die Anwendung einer benutzerdefinierten Wellenform, die in einem sogenannten "Kurven"-Array definiert ist. 

### Verwendung
Um einen **WaveShaperNode** zu erstellen, benötigen Sie eine Instanz des `AudioContext`. Danach können Sie den Node mit der Methode `createWaveShaper()` des **AudioContext** erstellen. Der Node kann dann mit Audioquellen verbunden werden, um den Klang zu verändern.

### Details
- **Parameter**: Der **WaveShaperNode** akzeptiert eine `curve`-Eigenschaft, die ein Float32Array ist und die Form der Verzerrung definiert. 
- **Oversampling**: Die `oversample`-Eigenschaft kann auf "none", "2x" oder "4x" gesetzt werden, um die Qualität der Verzerrung zu steuern.
- **Verbindung**: Der Node kann mit anderen AudioNodes wie dem `GainNode` oder `AnalyserNode` verbunden werden, um komplexe Audioverarbeitungs-Pipelines zu erstellen.

## Beispiele
### Grundlegende Verwendung
```javascript
// Erstellen eines AudioContext
const audioContext = new (window.AudioContext || window.webkitAudioContext)();

// Erstellen des WaveShaperNode
const waveShaper = audioContext.createWaveShaper();

// Definieren der Verzerrungskurve
const curve = new Float32Array(44100);
for (let i = 0; i < 44100; ++i) {
    const x = (i * 2.0) / 44100 - 1; // Normalisierte Werte zwischen -1 und 1
    curve[i] = (Math.PI + 1) * x / (Math.PI + Math.abs(x)); // Erstellen einer sanften Verzerrung
}
waveShaper.curve = curve;

// Audioquelle erstellen
const oscillator = audioContext.createOscillator();
oscillator.type = "sine";
oscillator.frequency.setValueAtTime(440, audioContext.currentTime); // A4
oscillator.connect(waveShaper);
waveShaper.connect(audioContext.destination);

// Starten der Audioquelle
oscillator.start();
```

## Erklärung
### Häufige Fallstricke
- **Leere Kurven**: Stellen Sie sicher, dass die `curve`-Eigenschaft korrekt gesetzt ist, da ein leeres Float32Array zu unerwartetem Verhalten führen kann.
- **AudioContext aktivieren**: Der **AudioContext** muss aktiv sein, bevor Sie Audioquellen oder Nodes verwenden können. In vielen Browsern muss der AudioContext durch eine Benutzerinteraktion (z.B. einen Button-Klick) aktiviert werden.
- **Oversampling-Optionen**: Verwenden Sie Oversampling, um die Klangqualität zu verbessern, insbesondere bei komplexen Verzerrungen, da dies Artefakte in der Audioausgabe reduzieren kann.

## Einzeiler Zusammenfassung
Der **WaveShaperNode** in JavaScript ermöglicht die kreative Bearbeitung von Audiosignalen durch nichtlineare Verzerrungen und benutzerdefinierte Wellenformen.