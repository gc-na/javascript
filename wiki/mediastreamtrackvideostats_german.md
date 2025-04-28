<!--
Meta Description: # MediaStreamTrackVideoStats in JavaScript: Statistiken für Video-Streams ## Synopsis MediaStreamTrackVideoStats ist eine wichtige Schnittstelle in de...
Meta Keywords: die, der, statistiken, video, mediastreamtrackvideostats
-->

# MediaStreamTrackVideoStats in JavaScript: Statistiken für Video-Streams

## Synopsis
MediaStreamTrackVideoStats ist eine wichtige Schnittstelle in der WebRTC-API, die es Entwicklern ermöglicht, detaillierte Statistiken über Video-Streams zu sammeln. Diese Statistiken sind entscheidend für die Überwachung der Videoqualität und die Optimierung der Benutzererfahrung in Echtzeitanwendungen.

## Dokumentation
**Zweck:**  
MediaStreamTrackVideoStats bietet umfassende Informationen über die Leistung von Video-Streams, einschließlich Auflösung, Bildrate und verlorenen Frames. Diese Daten helfen Entwicklern, die Qualität ihrer Videoübertragungen zu analysieren und gegebenenfalls Anpassungen vorzunehmen.

**Verwendung:**  
Um auf MediaStreamTrackVideoStats zuzugreifen, müssen Sie zuerst eine MediaStreamTrack-Instanz erhalten, die einen Video-Stream repräsentiert. Danach können Sie die `getStats()`-Methode verwenden, um die Statistiken abzurufen.

**Details:**  
Die MediaStreamTrackVideoStats-Schnittstelle enthält mehrere wichtige Eigenschaften:

- **frameWidth**: Die Breite des Frames in Pixeln.
- **frameHeight**: Die Höhe des Frames in Pixeln.
- **framesPerSecond**: Die Anzahl der Bilder pro Sekunde, die übertragen werden.
- **framesSent**: Die Gesamtzahl der gesendeten Frames.
- **framesDropped**: Die Gesamtzahl der verlorenen Frames, die nicht gesendet werden konnten.

## Beispiele
### Beispiel 1: Zugriff auf Video-Statistiken
```javascript
navigator.mediaDevices.getUserMedia({ video: true })
  .then(stream => {
    const videoTrack = stream.getVideoTracks()[0];
    return videoTrack.getSettings();
  })
  .then(settings => {
    console.log('Video Einstellungen:', settings);
  })
  .catch(error => {
    console.error('Fehler beim Abrufen des Streams:', error);
  });
```

### Beispiel 2: Abrufen von Statistiken
```javascript
const videoTrack = stream.getVideoTracks()[0];

videoTrack.applyConstraints({
  advanced: [{ frameRate: { ideal: 30, max: 60 } }]
}).then(() => {
  return videoTrack.getStats();
}).then(stats => {
  stats.forEach(report => {
    console.log(`Frame-Rate: ${report.framesPerSecond}`);
    console.log(`Verlorene Frames: ${report.framesDropped}`);
  });
});
```

## Erklärung
Bei der Verwendung von MediaStreamTrackVideoStats sollten Entwickler darauf achten, dass die Statistiken möglicherweise nicht sofort verfügbar sind, insbesondere bei der ersten Anfrage nach dem Start des Video-Streams. Es ist wichtig, die Statistiken regelmäßig abzurufen, um Echtzeitdaten zu erhalten. 

Ein häufiger Fehler besteht darin, zu erwarten, dass die Statistiken immer gleich bleiben. Faktoren wie Netzwerkbedingungen, Hardware-Leistung und Browser-Implementierungen können die Videoqualität beeinflussen und sollten bei der Fehlerbehebung berücksichtigt werden.

## Ein-Satz-Zusammenfassung
MediaStreamTrackVideoStats in JavaScript ermöglicht Entwicklern den Zugriff auf wichtige Leistungsstatistiken von Video-Streams zur Verbesserung der Benutzererfahrung in Echtzeitanwendungen.