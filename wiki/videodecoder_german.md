<!--
Meta Description: # VideoDecoder: JavaScript API zur Video-Dekodierung ## Synopsis Der `VideoDecoder` ist ein JavaScript-API, das Entwicklern ermöglicht, Video-Streams ...
Meta Keywords: error, der, frame, videodecoder, die
-->

# VideoDecoder: JavaScript API zur Video-Dekodierung

## Synopsis
Der `VideoDecoder` ist ein JavaScript-API, das Entwicklern ermöglicht, Video-Streams effizient zu dekodieren, um sie in Webanwendungen wiederzugeben. Diese Schnittstelle ist besonders nützlich für Anwendungen, die Echtzeit-Videoverarbeitung erfordern.

## Documentation
### Zweck
Der `VideoDecoder` wird verwendet, um kodierte Video-Daten in ein Format zu dekodieren, das zur Darstellung auf Bildschirmen geeignet ist. Diese API ist Teil der WebCodecs-Spezifikation und zielt darauf ab, eine niedrige Latenz und hohe Effizienz bei der Videoverarbeitung zu bieten.

### Verwendung
Um den `VideoDecoder` zu verwenden, muss ein neues Objekt mit den erforderlichen Parametern instanziiert werden. Hierzu gehört die Angabe eines Dekodierungs-Handlers, der die dekodierten Frames verarbeitet.

#### Syntax
```javascript
const decoder = new VideoDecoder({
    output: (frame) => {
        // Verarbeitung des dekodierten Frames
    },
    error: (error) => {
        console.error("Dekodierungsfehler:", error);
    }
});
```

### Details
- **output**: Eine Callback-Funktion, die aufgerufen wird, wenn ein neues Video-Frame dekodiert wurde.
- **error**: Eine Callback-Funktion, die aufgerufen wird, wenn ein Fehler während der Dekodierung auftritt.
- **configure()**: Konfiguriert den Dekoder mit spezifischen Codec-Einstellungen.
- **decode()**: Nimmt kodierte Video-Daten und dekodiert sie.
- **close()**: Schließt den Dekoder und gibt Ressourcen frei.

## Examples
### Beispiel 1: Grundlegende Dekodierung
```javascript
const decoder = new VideoDecoder({
    output: (frame) => {
        console.log("Neues Frame dekodiert:", frame);
        frame.close(); // Freigabe des Frames nach der Verwendung
    },
    error: (error) => {
        console.error("Dekodierungsfehler:", error);
    }
});

// Konfiguration des Dekoders mit einem spezifischen Codec
decoder.configure({ codec: 'avc1.64001E' });

// Dekodierung eines kodierten Frame
const encodedData = new Uint8Array([...]); // Beispiel für kodierte Daten
decoder.decode(encodedData);
```

### Beispiel 2: Fehlerbehandlung
```javascript
const decoder = new VideoDecoder({
    output: (frame) => {
        // Frame-Verarbeitung
    },
    error: (error) => {
        console.error("Ein Fehler ist aufgetreten:", error);
    }
});

// Fehlende Konfiguration oder falsch kodierte Daten könnten Fehler verursachen
decoder.decode(new Uint8Array([...]));
```

## Explanation
Ein häufiges Problem bei der Verwendung von `VideoDecoder` ist das Management der Ressourcen, insbesondere das Schließen der Frames nach der Verarbeitung. Entwickler sollten sicherstellen, dass `frame.close()` aufgerufen wird, um Speicherlecks zu vermeiden. Darüber hinaus ist es wichtig, den Dekoder ordnungsgemäß zu konfigurieren, bevor die Dekodierung erfolgt, da dies die Leistung und die Latenz stark beeinflussen kann.

## One Line Summary
Der `VideoDecoder` in JavaScript ermöglicht eine effiziente und latenzarme Dekodierung von Video-Streams für Webanwendungen.