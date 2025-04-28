<!--
Meta Description: # OscillatorNode in JavaScript: Ein umfassender Leitfaden für die Web Audio API ## Synopsis Der `OscillatorNode` ist ein grundlegendes Element der Web...
Meta Keywords: audiocontext, oscillator, der, oscillatornode, javascript
-->

# OscillatorNode in JavaScript: Ein umfassender Leitfaden für die Web Audio API

## Synopsis
Der `OscillatorNode` ist ein grundlegendes Element der Web Audio API, das zur Erzeugung von periodischen Wellenformen verwendet wird. Er ermöglicht Entwicklern die Synthese von Klängen, die zur Musikproduktion und Sounddesign eingesetzt werden können.

## Documentation
### Zweck
Der `OscillatorNode` wird verwendet, um verschiedene Arten von Wellenformen wie Sinus, Rechteck, Dreieck und Sägezahn zu erzeugen. Diese Wellenformen sind die Bausteine der Klangsynthetisierung und können in Audioanwendungen, Spielen oder interaktiven Medien verwendet werden.

### Verwendung
Um einen `OscillatorNode` zu erstellen, muss zunächst ein `AudioContext` initialisiert werden. Anschließend kann der Knoten durch den Aufruf der Methode `createOscillator()` des `AudioContext` erstellt werden. Der Knoten kann konfiguriert werden, um unterschiedliche Wellenformen und Frequenzen zu erzeugen.

#### Grundlegende Syntax:
```javascript
const audioContext = new (window.AudioContext || window.webkitAudioContext)();
const oscillator = audioContext.createOscillator();
```

#### Wellenform und Frequenz festlegen:
```javascript
oscillator.type = 'sine'; // Typ der Wellenform: 'sine', 'square', 'sawtooth', 'triangle'
oscillator.frequency.setValueAtTime(440, audioContext.currentTime); // Frequenz in Hertz
```

#### Starten und Stoppen des Oszillators:
```javascript
oscillator.start(); // Starten des Oszillators
oscillator.stop(audioContext.currentTime + 2); // Stoppt nach 2 Sekunden
```

## Examples
### Einfaches Beispiel eines Oszillators
Hier ist ein einfaches Beispiel, das einen Sinus-Oszillator erzeugt und für 2 Sekunden abspielt:

```javascript
const audioContext = new (window.AudioContext || window.webkitAudioContext)();
const oscillator = audioContext.createOscillator();

oscillator.type = 'sine';
oscillator.frequency.setValueAtTime(440, audioContext.currentTime);
oscillator.connect(audioContext.destination);
oscillator.start();
oscillator.stop(audioContext.currentTime + 2);
```

### Beispiel mit Rechteck-Wellenform
Hier ist ein Beispiel, das einen Rechteck-Oszillator mit einer Frequenz von 880 Hz erzeugt:

```javascript
const audioContext = new (window.AudioContext || window.webkitAudioContext)();
const oscillator = audioContext.createOscillator();

oscillator.type = 'square';
oscillator.frequency.setValueAtTime(880, audioContext.currentTime);
oscillator.connect(audioContext.destination);
oscillator.start();
oscillator.stop(audioContext.currentTime + 2);
```

## Explanation
Ein häufiges Problem bei der Verwendung von `OscillatorNode` ist, dass der Oszillator nicht den gewünschten Klang erzeugt, wenn er nicht korrekt an den Audio-Ausgang angeschlossen ist. Stellen Sie sicher, dass der Oszillator mit `audioContext.destination` verbunden ist, bevor Sie ihn starten. 

Ein weiterer Punkt ist, dass der `OscillatorNode` nur einmal gestartet werden kann. Wenn Sie versuchen, ihn erneut zu starten, müssen Sie einen neuen Oszillator erstellen. Auch die Frequenz muss innerhalb der hörbaren Reichweite (ungefähr 20 Hz bis 20 kHz) liegen, um hörbare Töne zu erzeugen.

## One Line Summary
Der `OscillatorNode` in JavaScript ermöglicht die Erzeugung von periodischen Wellenformen zur Klangsynthetisierung in der Web Audio API.