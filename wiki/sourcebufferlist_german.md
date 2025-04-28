<!--
Meta Description: # SourceBufferList in JavaScript: Eine umfassende Übersicht ## Synopsis `SourceBufferList` ist eine wichtige Schnittstelle der Media Source Extensions...
Meta Keywords: mediasource, die, sourcebufferlist, sourcebuffer, von
-->

# SourceBufferList in JavaScript: Eine umfassende Übersicht

## Synopsis
`SourceBufferList` ist eine wichtige Schnittstelle der Media Source Extensions (MSE) in JavaScript, die eine Sammlung von `SourceBuffer`-Objekten repräsentiert, die für das Streaming von Multimedia-Inhalten verwendet werden.

## Dokumentation

### Zweck
`SourceBufferList` wird verwendet, um mehrere `SourceBuffer`-Instanzen zu verwalten, die zur Bearbeitung von Medien-Datenströmen in Webanwendungen benötigt werden. Es ermöglicht Entwicklern, mehrere Quellpuffer zu erstellen und zu verwalten, um unterschiedliche Medienformate oder Zeitabschnitte innerhalb eines Streams zu verarbeiten.

### Verwendung
`SourceBufferList` wird typischerweise in Verbindung mit der `MediaSource`-Schnittstelle verwendet. Sobald ein `MediaSource`-Objekt erstellt wurde, können `SourceBuffer`-Objekte hinzugefügt werden, um Medieninhalte dynamisch zu streamen.

```javascript
const mediaSource = new MediaSource();
const sourceBufferList = mediaSource.sourceBuffers;
```

### Details
- `SourceBufferList` ist eine `ReadOnly`-Liste, was bedeutet, dass Sie nicht direkt Elemente hinzufügen oder entfernen können. Stattdessen wird die `addSourceBuffer`-Methode von `MediaSource` verwendet, um `SourceBuffer`-Instanzen zu erstellen.
- Die Länge der `SourceBufferList` kann über die `length`-Eigenschaft abgerufen werden.
- Jedes `SourceBuffer` in der Liste kann verschiedene Mediendaten enthalten, die zu einem Gesamtstream gehören.

## Beispiele

### Beispiel 1: Erstellen eines MediaSource und Zugreifen auf SourceBufferList
```javascript
const mediaSource = new MediaSource();
const videoElement = document.querySelector('video');

videoElement.src = URL.createObjectURL(mediaSource);

mediaSource.addEventListener('sourceopen', () => {
    const sourceBuffer = mediaSource.addSourceBuffer('video/mp4; codecs="avc1.64001E, mp4a.40.2"');
    console.log(mediaSource.sourceBuffers); // Zugriff auf SourceBufferList
});
```

### Beispiel 2: Abrufen der Anzahl der SourceBuffer
```javascript
mediaSource.addEventListener('sourceopen', () => {
    const sourceBuffer1 = mediaSource.addSourceBuffer('video/mp4; codecs="avc1.64001E"');
    const sourceBuffer2 = mediaSource.addSourceBuffer('audio/mp4; codecs="mp4a.40.2"');

    console.log(mediaSource.sourceBuffers.length); // Gibt 2 zurück
});
```

## Erklärung
- **Gemeinsame Fallstricke**: Stellen Sie sicher, dass das `MediaSource`-Objekt geöffnet ist, bevor Sie `SourceBuffer`-Objekte hinzufügen. Andernfalls kann es zu Fehlern kommen.
- **Kompatibilität**: `SourceBufferList` ist nicht in allen Browsern gleich implementiert. Überprüfen Sie die Browserkompatibilität, bevor Sie diese Technologie in Produktionsumgebungen verwenden.
- **Leistungsaspekte**: Übermäßige Nutzung von `SourceBuffer` kann die Leistung beeinträchtigen. Es ist wichtig, unnötige Puffer zu entfernen, wenn sie nicht mehr benötigt werden, um die Speicherauslastung zu optimieren.

## Ein-Satz-Zusammenfassung
`SourceBufferList` ist eine Schnittstelle in JavaScript, die eine Sammlung von `SourceBuffer`-Objekten verwaltet, um das Streaming von Multimedia-Inhalten über die Media Source Extensions zu ermöglichen.