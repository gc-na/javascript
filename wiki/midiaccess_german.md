<!--
Meta Description: # MIDIAccess in JavaScript: Ein umfassender Leitfaden ## Synopsis MIDIAccess ist eine Schnittstelle in JavaScript, die den Zugriff auf MIDI-Geräte (Mu...
Meta Keywords: midi, die, midiaccess, zugriff, auf
-->

# MIDIAccess in JavaScript: Ein umfassender Leitfaden

## Synopsis
MIDIAccess ist eine Schnittstelle in JavaScript, die den Zugriff auf MIDI-Geräte (Musical Instrument Digital Interface) ermöglicht. Sie erlaubt Entwicklern, MIDI-Daten zu senden und zu empfangen, um interaktive Musik-Anwendungen und -Spiele zu erstellen.

## Dokumentation
Die MIDIAccess-Schnittstelle ist Teil der Web MIDI API und bietet eine Möglichkeit, mit MIDI-Geräten zu kommunizieren. Sie ermöglicht den Zugriff auf die angeschlossenen MIDI-Eingangs- und Ausgangsgeräte sowie die Verwaltung von MIDI-Datenströmen.

### Zweck
MIDIAccess wird verwendet, um den Zugriff auf MIDI-Hardware zu ermöglichen. Dies kann sowohl für die Erstellung von Musiksoftware als auch für die Entwicklung von Spielen, die MIDI-Daten verwenden, nützlich sein.

### Verwendung
Um MIDIAccess zu verwenden, müssen Sie zunächst die `navigator.requestMIDIAccess()`-Methode aufrufen, die ein Promise zurückgibt. Wenn das Promise erfüllt wird, erhalten Sie ein `MIDIAccess`-Objekt, das Informationen über die verbundenen MIDI-Geräte bereitstellt.

#### Beispielcode für den Zugriff auf MIDI-Geräte:

```javascript
navigator.requestMIDIAccess()
  .then(onMIDISuccess, onMIDIFailure);

function onMIDISuccess(midiAccess) {
    console.log("MIDI-Zugriff erfolgreich:", midiAccess);
    // Hier können Sie auf Eingänge und Ausgänge zugreifen
}

function onMIDIFailure() {
    console.error("MIDI-Zugriff fehlgeschlagen.");
}
```

### Details
Das `MIDIAccess`-Objekt enthält zwei wichtige Eigenschaften:
- `inputs`: Eine Sammlung von MIDI-Eingabegeräten.
- `outputs`: Eine Sammlung von MIDI-Ausgabegeräten.

Sie können die Geräte durch Iteration über diese Sammlungen ansprechen und Daten senden oder empfangen.

## Beispiele
### Zugriff auf MIDI-Geräte
```javascript
navigator.requestMIDIAccess().then(midiAccess => {
    const inputs = midiAccess.inputs;
    inputs.forEach(input => {
        console.log(`MIDI-Eingang gefunden: ${input.name}`);
        input.onmidimessage = handleMIDIMessage;
    });
});

function handleMIDIMessage(message) {
    console.log(`MIDI-Nachricht empfangen: ${message.data}`);
}
```

### Senden von MIDI-Daten
```javascript
navigator.requestMIDIAccess().then(midiAccess => {
    const outputs = midiAccess.outputs;
    const output = outputs.get(0); // Erstes Ausgangsgerät auswählen
    if (output) {
        const noteOnMessage = [0x90, 60, 0x7f]; // Note On: C4
        output.send(noteOnMessage); // Senden der Note
    }
});
```

## Erklärung
Ein häufiges Problem beim Arbeiten mit MIDIAccess ist, dass nicht alle Browser die Web MIDI API unterstützen. Es ist ratsam, die Kompatibilität der Browser zu überprüfen, bevor Sie diese Funktionalität implementieren. Zusätzlich sollten Benutzer darum gebeten werden, die Berechtigungen für den Zugriff auf MIDI-Geräte zu gewähren, da dies erforderlich ist, um die API nutzen zu können.

Ein weiteres häufiges Problem ist die Handhabung von MIDI-Nachrichten und die korrekte Interpretation der Daten. MIDI-Daten bestehen aus verschiedenen Bytes, die unterschiedliche Informationen repräsentieren (z.B. Noten, Steuerbefehle).

## Ein-Satz-Zusammenfassung
MIDIAccess ist eine JavaScript-Schnittstelle, die den Zugriff auf und die Interaktion mit MIDI-Geräten ermöglicht, um kreative Multimedia-Anwendungen zu entwickeln.