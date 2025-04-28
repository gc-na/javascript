<!--
Meta Description: # onloadedmetadata in JavaScript: Verwendung und Beispiele ## Synopsis Das `onloadedmetadata`-Ereignis in JavaScript wird ausgelöst, wenn die Metadate...
Meta Keywords: video, das, wird, onloadedmetadata, die
-->

# onloadedmetadata in JavaScript: Verwendung und Beispiele

## Synopsis
Das `onloadedmetadata`-Ereignis in JavaScript wird ausgelöst, wenn die Metadaten eines Medienobjekts, wie z. B. ein Video oder Audio, erfolgreich geladen wurden. Es ermöglicht Entwicklern den Zugriff auf Informationen über das Medium, wie Dauer und Dimensionen, bevor es abgespielt wird.

## Dokumentation
Das `onloadedmetadata`-Ereignis ist ein Teil der HTMLMediaElement-Schnittstelle und wird häufig in Verbindung mit `<audio>`- und `<video>`-Elementen verwendet. Dieses Ereignis wird ausgelöst, sobald die Metadaten des Medieninhalts (z. B. Dauer, Dimensionen, Titel) vollständig verfügbar sind, was es ermöglicht, diese Informationen zu nutzen, bevor das Medienstück tatsächlich abgespielt wird.

### Verwendung:
Um das `onloadedmetadata`-Ereignis zu nutzen, müssen Sie einen Event-Listener an ein Medienelement anhängen. Hier ist die allgemeine Verwendung:

```javascript
const videoElement = document.querySelector('video');

videoElement.onloadedmetadata = function() {
    console.log('Metadaten sind geladen!');
    console.log('Dauer des Videos: ' + videoElement.duration + ' Sekunden');
};
```

### Details:
- **Ereignistyp**: `Event`
- **Elemente**: `<audio>`, `<video>`
- **Wann wird es ausgelöst?**: Wenn die Metadaten des Medieninhalts geladen sind.
- **Wichtige Eigenschaften**: 
  - `duration`: Gibt die Gesamtdauer des Medieninhalts zurück.
  - `videoWidth` und `videoHeight`: Gibt die Abmessungen des Videos zurück (nur für `<video>`-Elemente).

## Beispiele
Hier sind einige grundlegende Beispiele zur Verwendung von `onloadedmetadata`:

### Beispiel 1: Dauer eines Videos abrufen
```html
<video id="myVideo" controls>
    <source src="video.mp4" type="video/mp4">
    Ihr Browser unterstützt das Video-Tag nicht.
</video>
<script>
    const video = document.getElementById('myVideo');
    
    video.onloadedmetadata = function() {
        console.log('Die Dauer des Videos beträgt: ' + video.duration + ' Sekunden.');
    };
</script>
```

### Beispiel 2: Video-Dimensionen abrufen
```html
<video id="myVideo" controls>
    <source src="video.mp4" type="video/mp4">
    Ihr Browser unterstützt das Video-Tag nicht.
</video>
<script>
    const video = document.getElementById('myVideo');
    
    video.onloadedmetadata = function() {
        console.log('Video Breite: ' + video.videoWidth + 'px');
        console.log('Video Höhe: ' + video.videoHeight + 'px');
    };
</script>
```

## Erklärung
Ein häufiges Problem beim Arbeiten mit `onloadedmetadata` ist, dass es möglicherweise nicht ausgelöst wird, wenn die Quelle des Medieninhalts nicht korrekt ist oder wenn das Medienformat nicht unterstützt wird. Stellen Sie sicher, dass:
- Die Medienquelle korrekt angegeben ist.
- Der Browser das verwendete Medienformat unterstützt.
- Sie das Ereignis vor dem Abspielen des Mediums einrichten.

Ein weiteres häufiges Missverständnis ist, dass das `onloadedmetadata`-Ereignis nicht garantiert wird, dass das Medium erfolgreich geladen wird. Es wird nur ausgelöst, wenn die Metadaten verfügbar sind, was nicht unbedingt bedeutet, dass das Abspielen ohne Probleme funktionieren wird.

## Ein-Satz-Zusammenfassung
Das `onloadedmetadata`-Ereignis in JavaScript ermöglicht den Zugriff auf wichtige Metadaten eines Medienobjekts, sobald diese geladen sind, und ist besonders nützlich für die Vorbereitung des Medieninhalts vor dem Abspielen.