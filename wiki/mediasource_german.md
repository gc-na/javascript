<!--
Meta Description: # MediaSource in JavaScript: Dynamische Medienströme für das Web ## Synopsis Die `MediaSource`-API in JavaScript ermöglicht Entwicklern, dynamische Me...
Meta Keywords: mediasource, die, und, video, sourcebuffer
-->

# MediaSource in JavaScript: Dynamische Medienströme für das Web

## Synopsis
Die `MediaSource`-API in JavaScript ermöglicht Entwicklern, dynamische Mediendaten für die Wiedergabe in HTML5-Video- und Audioelementen zu erstellen und zu verwalten.

## Dokumentation
Die `MediaSource`-API ist Teil der HTML5-Spezifikation und bietet eine Programmierschnittstelle, um Mediendaten in Echtzeit zu verarbeiten. Mit `MediaSource` können Entwickler Medienfragmente hinzufügen, entfernen und die Wiedergabe von Streams steuern, was besonders nützlich ist für Anwendungen wie Live-Streaming, adaptive Bitrate-Streaming und die Integration von benutzerdefinierten Medieninhalten.

### Verwendung
Um `MediaSource` zu verwenden, erstellen Sie ein neues `MediaSource`-Objekt und verknüpfen es mit einem `<video>`- oder `<audio>`-Element. Anschließend können Sie Quellen zu dem Objekt hinzufügen, um Medieninhalte dynamisch zu steuern.

### API-Methoden und Eigenschaften
- **`MediaSource`**: Konstruktor, um ein neues `MediaSource`-Objekt zu erstellen.
- **`addSourceBuffer(mimeType)`**: Fügt einen neuen `SourceBuffer` für den angegebenen MIME-Typ hinzu.
- **`sourceBuffers`**: Eine Liste der `SourceBuffer`-Objekte, die dem `MediaSource`-Objekt zugeordnet sind.
- **`duration`**: Gibt die Gesamtdauer des Streams an.
- **`readyState`**: Gibt den aktuellen Zustand der `MediaSource`-Instanz an (z. B. `open`, `closed`).

## Beispiele
### Beispiel 1: Grundlegende Verwendung von MediaSource
```javascript
const video = document.querySelector('video');
const mediaSource = new MediaSource();

video.src = URL.createObjectURL(mediaSource);

mediaSource.addEventListener('sourceopen', () => {
    const sourceBuffer = mediaSource.addSourceBuffer('video/webm; codecs="vp8, vorbis"');
    // Hier können Daten zum SourceBuffer hinzugefügt werden
});
```

### Beispiel 2: Hinzufügen von Mediendaten
```javascript
fetch('video.webm')
    .then(response => response.arrayBuffer())
    .then(data => {
        sourceBuffer.appendBuffer(data);
    });
```

## Erklärung
Ein häufiges Problem bei der Verwendung von `MediaSource` kann sein, dass die `sourceBuffer`-Instanz nicht mehr bereit ist, Daten zu empfangen, wenn Sie versuchen, Daten hinzuzufügen. Entwickeln Sie eine Logik, um sicherzustellen, dass Sie nur Daten anhängen, wenn der `sourceBuffer` in einem `updating`-Zustand ist. Ein weiteres wichtiges Detail ist, dass das `MediaSource`-Objekt seine `readyState`-Eigenschaft überwachen sollte, um sicherzustellen, dass es im `open`-Zustand ist, bevor weitere `SourceBuffer`-Objekte hinzugefügt werden.

## Zusammenfassung in einem Satz
Die `MediaSource`-API in JavaScript ermöglicht die dynamische Verwaltung von Medieninhalten für HTML5-Video- und Audioelemente und ist ideal für adaptive Streaming-Anwendungen.