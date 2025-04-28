<!--
Meta Description: # MIDIInputMap in JavaScript: Eine umfassende Anleitung ## Synopsis MIDIInputMap ist eine Schnittstelle in der Web MIDI API, die es Entwicklern ermögl...
Meta Keywords: midi, die, midiinputmap, auf, eine
-->

# MIDIInputMap in JavaScript: Eine umfassende Anleitung

## Synopsis
MIDIInputMap ist eine Schnittstelle in der Web MIDI API, die es Entwicklern ermöglicht, MIDI-Eingabegeräte zu verwalten und deren Eingaben in JavaScript-Anwendungen zu verarbeiten.

## Dokumentation
MIDIInputMap ist Teil der Web MIDI API, die Entwicklern die Interaktion mit MIDI-Geräten über das Web ermöglicht. Die MIDIInputMap-Schnittstelle bietet eine Sammlung von MIDIInput-Objekten, die MIDI-Daten von angeschlossenen Eingabegeräten repräsentieren. Diese Objekte ermöglichen es, MIDI-Nachrichten zu empfangen und zu verarbeiten.

### Zweck
Die Hauptfunktion von MIDIInputMap besteht darin, eine einfache und strukturierte Möglichkeit zu bieten, auf alle verfügbaren MIDI-Eingabegeräte zuzugreifen und deren Status zu überwachen.

### Verwendung
Um die MIDIInputMap zu verwenden, müssen Sie zunächst die Web MIDI API aktivieren und auf die MIDI-Eingabegeräte zugreifen. Hier ist ein typischer Ablauf:

1. **Zugriff auf MIDI-Geräte anfordern**: Verwenden Sie die Methode `navigator.requestMIDIAccess()`, um auf die MIDI-Geräte des Benutzers zuzugreifen.
2. **Zugriff auf MIDIInputMap erhalten**: Nachdem der Zugriff gewährt wurde, können Sie die `inputs`-Eigenschaft des `MIDIInputMap`-Objekts verwenden, um eine Liste der verfügbaren MIDI-Eingabegeräte zu erhalten.
3. **Eingabegeräte verwenden**: Sie können die Geräte durch Iteration über die MIDIInputMap und das Hinzufügen von Event-Listenern für die MIDI-Datenverarbeitung verwenden.

### Details
- **MIDIInputMap Eigenschaften**:
  - `size`: Gibt die Anzahl der MIDI-Eingabegeräte in der Map zurück.
  - `get()`: Ermöglicht den Zugriff auf ein bestimmtes MIDIInput-Objekt anhand seiner ID.
  
- **MIDIInput-Objekt**:
  - Jedes MIDIInput-Objekt hat eine `onmidimessage`-Eigenschaft, die eine Funktion erwartet, die aufgerufen wird, wenn eine MIDI-Nachricht empfangen wird.

## Beispiele
Hier sind einige grundlegende Beispiele für die Verwendung von MIDIInputMap in JavaScript:

### Beispiel 1: Zugriff auf MIDI-Geräte
```javascript
navigator.requestMIDIAccess()
  .then((access) => {
    const inputs = access.inputs;
    console.log(`Anzahl der MIDI-Eingabegeräte: ${inputs.size}`);
    inputs.forEach((input) => {
      console.log(`Geräte-ID: ${input.id}, Name: ${input.name}`);
    });
  })
  .catch((error) => {
    console.error('Fehler beim Zugriff auf MIDI-Geräte:', error);
  });
```

### Beispiel 2: Verarbeiten von MIDI-Nachrichten
```javascript
navigator.requestMIDIAccess()
  .then((access) => {
    const inputs = access.inputs;
    inputs.forEach((input) => {
      input.onmidimessage = (message) => {
        console.log(`MIDI-Nachricht empfangen: ${message.data}`);
      };
    });
  });
```

## Erklärung
Ein häufiges Missverständnis ist, dass MIDI-Geräte automatisch erkannt werden. Stellen Sie sicher, dass die Benutzer die Berechtigung erteilen, um auf ihre MIDI-Geräte zuzugreifen. Außerdem kann es zu Verzögerungen kommen, wenn viele MIDI-Geräte angeschlossen sind oder wenn die Verbindung instabil ist. 

Darüber hinaus sollten Entwickler beim Arbeiten mit MIDI-Nachrichten darauf achten, dass diese in einem bestimmten Format (z.B. [status, note, velocity]) gesendet werden, um die korrekte Verarbeitung zu gewährleisten.

## Ein-Satz-Zusammenfassung
MIDIInputMap ist eine leistungsstarke Schnittstelle in der Web MIDI API, die Entwicklern den Zugriff auf und die Verarbeitung von MIDI-Eingabegeräten in JavaScript-Anwendungen ermöglicht.