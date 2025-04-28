<!--
Meta Description: # AudioScheduledSourceNode in JavaScript: Ein umfassender Leitfaden ## Synopsis Der `AudioScheduledSourceNode` ist eine grundlegende Schnittstelle der...
Meta Keywords: audiocontext, audio, die, der, und
-->

# AudioScheduledSourceNode in JavaScript: Ein umfassender Leitfaden

## Synopsis
Der `AudioScheduledSourceNode` ist eine grundlegende Schnittstelle der Web Audio API in JavaScript, die es ermöglicht, Audioquellen zeitgesteuert abzuspielen und zu manipulieren. Diese Schnittstelle ist entscheidend für die Verarbeitung und Wiedergabe von Audio in modernen Webanwendungen.

## Dokumentation
### Zweck
`AudioScheduledSourceNode` dient als Basis für das Abspielen von Audioquellen, die zu einem bestimmten Zeitpunkt im Audio-Graphen der Web Audio API gestartet werden können. Dazu gehören Klingen wie `AudioBufferSourceNode` und `MediaElementAudioSourceNode`, die sich beide auf die Verwendung von Audio-Daten aus verschiedenen Quellen konzentrieren.

### Verwendung
Um einen `AudioScheduledSourceNode` zu erstellen, müssen Sie eine Instanz von `AudioContext` generieren. Danach können Sie entweder einen `AudioBufferSourceNode` für vorab geladene Audiodaten oder einen `MediaElementAudioSourceNode` für Audioelemente im DOM verwenden.

### Details
- **Eigenschaften**: `AudioScheduledSourceNode` enthält essentielle Eigenschaften wie `startTime`, `stopTime`, und `playbackState`, die den aktuellen Status der Audioquelle beschreiben.
- **Methoden**: Zu den Methoden zählen `start()`, `stop()`, und `onended`, um die Wiedergabe zu steuern und auf das Ende der Wiedergabe zu reagieren.
- **Ereignisse**: Das `onended`-Ereignis wird ausgelöst, wenn die Audioquelle zu Ende ist, was für die Synchronisation und Steuerung von Audioeffekten nützlich ist.

## Beispiele
### Beispiel 1: Grundlegende Verwendung von AudioBufferSourceNode

```javascript
// Erstellen eines AudioContext
const audioContext = new (window.AudioContext || window.webkitAudioContext)();

// Laden eines Audio Buffers
fetch('audio-file.mp3')
  .then(response => response.arrayBuffer())
  .then(data => audioContext.decodeAudioData(data))
  .then(buffer => {
    const source = audioContext.createBufferSource();
    source.buffer = buffer;

    // Starten der Wiedergabe
    source.start(0);
    source.connect(audioContext.destination);
  })
  .catch(error => console.error('Error with decoding audio data', error));
```

### Beispiel 2: Verwendung von MediaElementAudioSourceNode

```javascript
// Erstellen eines AudioContext
const audioContext = new (window.AudioContext || window.webkitAudioContext)();

// Erstellen eines Audio-Elements
const audioElement = new Audio('audio-file.mp3');
const source = audioContext.createMediaElementSource(audioElement);

// Verbinden mit dem AudioContext
source.connect(audioContext.destination);

// Starten der Wiedergabe
audioElement.play();
```

## Erklärung
Ein häufiger Fehler beim Arbeiten mit `AudioScheduledSourceNode` ist das falsche Timing beim Starten oder Stoppen der Audioquelle. Stellen Sie sicher, dass Sie `start()` und `stop()` zu den richtigen Zeitpunkten aufrufen, um unerwartete Ergebnisse zu vermeiden. Auch die Verwendung von `AudioContext` außerhalb eines Benutzerinteraktionsereignisses kann dazu führen, dass der AudioContext in den "stopped" Zustand wechselt, was die Wiedergabe verhindert.

## Zusammenfassung in einem Satz
`AudioScheduledSourceNode` ist eine zentrale Schnittstelle der Web Audio API in JavaScript, die eine präzise und zeitgesteuerte Audio-Wiedergabe ermöglicht.