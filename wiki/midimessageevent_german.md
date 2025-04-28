<!--
Meta Description: # MIDIMessageEvent in JavaScript: Ein umfassender Leitfaden ## Synopsis Der `MIDIMessageEvent` ist ein wichtiges JavaScript-Event, das Informationen ü...
Meta Keywords: midi, das, die, note, midimessageevent
-->

# MIDIMessageEvent in JavaScript: Ein umfassender Leitfaden

## Synopsis
Der `MIDIMessageEvent` ist ein wichtiges JavaScript-Event, das Informationen über MIDI-Nachrichten über das Web MIDI API überträgt. Dieses Event ermöglicht es Entwicklern, auf MIDI-Daten zu reagieren, die von MIDI-Geräten gesendet werden.

## Dokumentation
### Zweck
Das `MIDIMessageEvent` wird verwendet, um MIDI-Nachrichten zu empfangen, die von MIDI-Geräten gesendet werden. Diese Nachrichten können verschiedene Informationen enthalten, wie Notenanschläge, Steuerbefehle und andere MIDI-Informationen. 

### Verwendung
Um `MIDIMessageEvent` zu verwenden, müssen Sie zunächst sicherstellen, dass das Web MIDI API im Browser verfügbar ist. Sie können dann den `MIDIInput` des MIDI-Geräts verwenden, um MIDI-Nachrichten zu empfangen. Das Event wird ausgelöst, wenn eine neue MIDI-Nachricht verfügbar ist.

### Details
Das `MIDIMessageEvent`-Objekt hat zwei Hauptattribute:
- `data`: Ein `Uint8Array`, das die MIDI-Nachricht enthält.
- `receivedTime`: Ein Zeitstempel, der angibt, wann die Nachricht empfangen wurde.

Um auf MIDI-Nachrichten zu reagieren, können Sie den `onmidimessage`-Event-Handler des MIDIInputs verwenden.

## Beispiele
Hier sind einige grundlegende Beispiele zur Verwendung von `MIDIMessageEvent`:

### Beispiel 1: MIDI-Gerät zur Konsole ausgeben
```javascript
if (navigator.requestMIDIAccess) {
    navigator.requestMIDIAccess().then(function(midiAccess) {
        const inputs = midiAccess.inputs;
        inputs.forEach(function(input) {
            input.onmidimessage = function(event) {
                console.log(event.data);
            };
        });
    });
} else {
    console.log("Web MIDI API wird in diesem Browser nicht unterstützt.");
}
```

### Beispiel 2: Notenanschläge verarbeiten
```javascript
navigator.requestMIDIAccess().then(function(midiAccess) {
    const inputs = midiAccess.inputs;
    inputs.forEach(function(input) {
        input.onmidimessage = function(event) {
            const [status, note, velocity] = event.data;
            if (status === 144) { // Note on
                console.log(`Note ${note} angeschlagen mit Velocity ${velocity}`);
            } else if (status === 128) { // Note off
                console.log(`Note ${note} losgelassen`);
            }
        };
    });
});
```

## Erklärung
Ein häufiger Stolperstein bei der Arbeit mit `MIDIMessageEvent` ist die Kompatibilität des Browsers. Das Web MIDI API wird nicht von allen Browsern unterstützt, sodass es wichtig ist, vor der Verwendung eine Überprüfung durchzuführen. Außerdem sollten Sie sicherstellen, dass das MIDI-Gerät korrekt angeschlossen und konfiguriert ist.

In einigen Fällen können die MIDI-Nachrichten in einem unerwarteten Format gesendet werden. Achten Sie darauf, die richtigen Statuscodes für `note on` und `note off` zu verwenden, um die gewünschten Ereignisse zu verarbeiten.

## Ein-Satz-Zusammenfassung
Der `MIDIMessageEvent` in JavaScript ermöglicht die Verarbeitung und Reaktion auf MIDI-Nachrichten, die über das Web MIDI API gesendet werden.