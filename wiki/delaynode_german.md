<!--
Meta Description: # DelayNode in JavaScript: Verzögerungseffekte für Audioverarbeitung ## Synopsis Der `DelayNode` ist ein Teil der Web Audio API in JavaScript, der es ...
Meta Keywords: delaynode, der, audiocontext, die, const
-->

# DelayNode in JavaScript: Verzögerungseffekte für Audioverarbeitung

## Synopsis
Der `DelayNode` ist ein Teil der Web Audio API in JavaScript, der es ermöglicht, Audiosignale mit einer einstellbaren Verzögerung zu bearbeiten. Er wird häufig verwendet, um Echo- oder Hall-Effekte in Audioanwendungen zu erzeugen.

## Dokumentation
### Zweck
Der `DelayNode` wird verwendet, um ein Audiosignal um eine spezifische Zeitspanne zu verzögern. Dies ist besonders nützlich in Anwendungen, die Audioeffekte wie Echo oder zeitbasierte Manipulationen erfordern.

### Verwendung
Um einen `DelayNode` zu erstellen, benötigen Sie einen `AudioContext`. Der `DelayNode` kann dann mit verschiedenen Parametern konfiguriert werden, wie der Verzögerungszeit und der maximalen Verzögerungszeit.

```javascript
const audioContext = new AudioContext();
const delayNode = audioContext.createDelay();

// Konfiguration der Verzögerungszeit
delayNode.delayTime.value = 0.5; // Verzögerung in Sekunden
```

### Details
- **delayTime**: Ein `AudioParam`, der die Zeit in Sekunden angibt, um die das Eingangssignal verzögert wird.
- **maxDelayTime**: Ein `AudioParam`, der die maximale Verzögerungszeit festlegt (standardmäßig 1 Sekunde, kann jedoch erhöht werden).

## Beispiele
### Einfaches Beispiel
Hier ist ein einfaches Beispiel, wie ein `DelayNode` erstellt und verwendet wird:

```javascript
const audioContext = new AudioContext();
const oscillator = audioContext.createOscillator();
const delayNode = audioContext.createDelay();

delayNode.delayTime.value = 0.3; // 300 ms Verzögerung

oscillator.connect(delayNode);
delayNode.connect(audioContext.destination);

// Starten des Oszillators
oscillator.start();
```

### Echo-Effekt
Ein Beispiel für die Erstellung eines Echo-Effekts:

```javascript
const audioContext = new AudioContext();
const audioElement = new Audio('path/to/audio.mp3');
const source = audioContext.createMediaElementSource(audioElement);
const delayNode = audioContext.createDelay();

delayNode.delayTime.value = 0.25; // 250 ms Verzögerung

source.connect(delayNode);
delayNode.connect(audioContext.destination);
source.connect(audioContext.destination); // Direktes Signal

audioElement.play();
```

## Erklärung
### Häufige Fallstricke
- **Verzögerungszeit zu kurz**: Wenn die Verzögerungszeit zu kurz ist, kann es sein, dass der Effekt nicht wahrnehmbar ist.
- **Asynchrone Natur**: Die Web Audio API arbeitet asynchron, daher sollten Sie sicherstellen, dass der `AudioContext` vor der Verwendung des `DelayNode` gestartet wird.
- **Browserkompatibilität**: Überprüfen Sie die Kompatibilität des Browsers mit der Web Audio API, da nicht alle älteren Browser unterstützt werden.

### Zusätzliche Hinweise
- Der `DelayNode` kann auch in Kombination mit anderen Audio-Node-Typen verwendet werden, um komplexere Audioeffekte zu erzielen.
- Nutzen Sie die `gainNode`, um die Lautstärke des verzögerten Signals anzupassen.

## Einzeilensummenfassung
Der `DelayNode` in JavaScript ermöglicht es, Audiosignale mit einer einstellbaren Verzögerung zu manipulieren, um Effekte wie Echo zu erzeugen.