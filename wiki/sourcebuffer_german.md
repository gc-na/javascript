<!--
Meta Description: # SourceBuffer in JavaScript: Ein Leitfaden für Entwickler ## Synopsis `SourceBuffer` ist eine Schnittstelle der Media Source Extensions (MSE) API in ...
Meta Keywords: sourcebuffer, ist, die, und, ein
-->

# SourceBuffer in JavaScript: Ein Leitfaden für Entwickler

## Synopsis
`SourceBuffer` ist eine Schnittstelle der Media Source Extensions (MSE) API in JavaScript, die es ermöglicht, Mediendaten in einem Streaming-Kontext dynamisch hinzuzufügen und zu verwalten.

## Dokumentation
`SourceBuffer` wird verwendet, um Mediendaten (z.B. Audio- und Videodaten) zu einem `MediaSource`-Objekt hinzuzufügen. Dies ist besonders nützlich für das Streaming von Medieninhalten, da es Entwicklern ermöglicht, Daten in kleinen Stücken zu verarbeiten, anstatt sie als vollständige Datei zu laden. 

### Zweck
Die Hauptfunktion von `SourceBuffer` besteht darin, Mediendaten in einem kontrollierten und effizienten Verfahren zu puffern und zu manipulieren. Dies ermöglicht eine reibungslose Wiedergabe und das Streaming von Inhalten, während gleichzeitig die Bandbreitennutzung optimiert wird.

### Verwendung
Um `SourceBuffer` zu verwenden, müssen Sie zuerst ein `MediaSource`-Objekt erstellen und es mit einem `<video>` oder `<audio>` Element verknüpfen. Anschließend können Sie mit der Methode `addSourceBuffer()` ein oder mehrere `SourceBuffer`-Objekte hinzufügen.

### Eigenschaften und Methoden
- **appendBuffer(data)**: Fügt dem `SourceBuffer` ein ArrayBuffer oder ArrayBufferView hinzu.
- **remove(start, end)**: Entfernt Daten aus dem `SourceBuffer` im angegebenen Bereich.
- **timestampOffset**: Gibt den Zeitstempel für die ersten Mediendaten im Puffer an.
- **mode**: Bestimmt, ob der Puffer im "segments" oder "sequence" Modus arbeitet.

## Beispiele
### Grundlegende Verwendung
```javascript
const videoElement = document.querySelector('video');
const mediaSource = new MediaSource();

videoElement.src = URL.createObjectURL(mediaSource);

mediaSource.addEventListener('sourceopen', () => {
    const sourceBuffer = mediaSource.addSourceBuffer('video/mp4; codecs="avc1.64001F, mp4a.40.2"');

    fetch('video.mp4')
        .then(response => response.arrayBuffer())
        .then(data => {
            sourceBuffer.appendBuffer(data);
        });
});
```

### Entfernen von Daten
```javascript
sourceBuffer.remove(startTime, endTime);
```

## Erklärung
Ein häufiges Problem beim Arbeiten mit `SourceBuffer` ist das Timing. Es ist wichtig, sicherzustellen, dass Sie nicht versuchen, Daten hinzuzufügen, während der Puffer noch mit dem Verarbeiten vorheriger Daten beschäftigt ist. Achten Sie darauf, die `updateend`-Ereignisse zu überwachen, um sicherzustellen, dass der `SourceBuffer` bereit ist, neue Daten zu empfangen.

Ein weiterer häufiger Fehler ist die Verwendung eines falschen MIME-Typs oder eines inkompatiblen Codecs beim Erstellen des `SourceBuffer`. Stellen Sie sicher, dass die angegebenen Codecs mit dem Medientyp kompatibel sind.

## Ein-Satz-Zusammenfassung
`SourceBuffer` ist eine JavaScript-Schnittstelle, die das dynamische Hinzufügen und Verwalten von Mediendaten in Streaming-Anwendungen ermöglicht.