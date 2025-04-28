<!--
Meta Description: # MIDIOutputMap in JavaScript: Eine umfassende Einführung ## Zusammenfassung MIDIOutputMap ist ein JavaScript-Objekt, das eine Sammlung von MIDI-Ausga...
Meta Keywords: midi, midioutputmap, ist, ausgabe, ein
-->

# MIDIOutputMap in JavaScript: Eine umfassende Einführung

## Zusammenfassung
MIDIOutputMap ist ein JavaScript-Objekt, das eine Sammlung von MIDI-Ausgabe-Ports repräsentiert und Entwicklern ermöglicht, MIDI-Daten über Webanwendungen zu senden.

## Dokumentation
### Zweck
MIDIOutputMap ist Teil der Web MIDI API, die es Webanwendungen ermöglicht, mit MIDI-Geräten zu kommunizieren. Es bietet eine strukturierte Möglichkeit, auf verfügbare MIDI-Ausgabe-Ports zuzugreifen, die in einer Anwendung verwendet werden können.

### Verwendung
MIDIOutputMap wird typischerweise in Verbindung mit der `navigator.requestMIDIAccess()`-Methode verwendet, die den Zugriff auf MIDI-Geräte ermöglicht. Die Ausgabe-Ports können dann verwendet werden, um MIDI-Nachrichten an externe Geräte zu senden, wie z.B. Synthesizer oder digitale Audio-Workstations.

### Details
- **Typ:** MIDIOutputMap ist ein Objekt, das eine Map von MIDI-Ausgabe-Ports darstellt.
- **Zugriff:** Um auf das MIDIOutputMap-Objekt zuzugreifen, muss zunächst der Zugriff auf MIDI-Geräte angefordert werden.
- **MIDIOutputPort:** Jedes Element in der MIDIOutputMap ist ein MIDIOutputPort, das spezifische Methoden zum Senden von MIDI-Daten bereitstellt.

## Beispiele
### Beispiel 1: Zugriff auf MIDI-Ausgabe-Ports
```javascript
navigator.requestMIDIAccess().then((access) => {
    const outputs = access.outputs;
    outputs.forEach((output) => {
        console.log(`MIDI-Ausgabe-Name: ${output.name}`);
    });
});
```

### Beispiel 2: Senden von MIDI-Nachrichten
```javascript
navigator.requestMIDIAccess().then((access) => {
    const output = access.outputs.get('output-id'); // Ersetzen Sie 'output-id' mit der tatsächlichen ID
    const noteOnMessage = [0x90, 60, 0x7f]; // Note on, Mittlerer C, volle Lautstärke
    output.send(noteOnMessage);
});
```

## Erklärung
Ein häufiges Problem bei der Verwendung von MIDIOutputMap ist das Timing beim Senden von MIDI-Nachrichten. Es ist wichtig sicherzustellen, dass MIDI-Geräte korrekt angeschlossen und bereit sind, bevor Nachrichten gesendet werden. Ein weiteres häufiges Missverständnis ist, dass alle MIDI-Geräte sofort nach dem Anfordern des Zugriffs verfügbar sind; in Wirklichkeit kann es einige Zeit dauern, bis die Geräte initialisiert sind. Außerdem sollten Entwickler sicherstellen, dass sie die richtige Ausgabe-ID verwenden, um Fehler beim Senden zu vermeiden.

## Zusammenfassung in einem Satz
MIDIOutputMap ist ein nützliches JavaScript-Objekt zur Verwaltung und Kommunikation mit MIDI-Ausgabe-Ports in Webanwendungen.