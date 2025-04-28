<!--
Meta Description: # onloadeddata in JavaScript: Ein umfassender Leitfaden ## Synopsis Das `onloadeddata`-Ereignis in JavaScript wird ausgelöst, wenn die Daten eines Med...
Meta Keywords: das, ereignis, onloadeddata, die, video
-->

# onloadeddata in JavaScript: Ein umfassender Leitfaden

## Synopsis
Das `onloadeddata`-Ereignis in JavaScript wird ausgelöst, wenn die Daten eines Media-Elements (wie Video oder Audio) erfolgreich geladen wurden und die ersten Daten verfügbar sind. Dieses Ereignis ist besonders nützlich, um sicherzustellen, dass Medieninhalte bereit sind, bevor sie wiedergegeben oder weiterverarbeitet werden.

## Dokumentation
### Zweck
Das `onloadeddata`-Ereignis signalisiert den Zeitpunkt, an dem die ersten Frames eines Medieninhalts (z.B. eines Videos oder Audios) geladen sind. Es ermöglicht Entwicklern, auf diese Änderung zu reagieren, um beispielsweise eine Benutzeroberfläche anzupassen oder die Wiedergabe zu starten.

### Verwendung
Um das `onloadeddata`-Ereignis zu verwenden, können Sie einen Event-Listener für ein `<video>`- oder `<audio>`-Element hinzufügen. Das folgende Beispiel demonstriert, wie das Ereignis implementiert wird:

```javascript
const videoElement = document.getElementById('meinVideo');

videoElement.onloadeddata = function() {
    console.log('Die Mediendaten wurden erfolgreich geladen.');
    // Weitere Aktionen, z.B. die Wiedergabe starten
    videoElement.play();
};
```

### Details
- **Event-Objekt**: Das `onloadeddata`-Ereignis wird mit einem Event-Objekt ausgelöst, das Informationen über das Ereignis enthält.
- **Browserunterstützung**: Das Ereignis wird von allen modernen Browsern unterstützt, einschließlich Chrome, Firefox, Safari und Edge.
- **Ereignisfluss**: `onloadeddata` wird nach dem `loadstart`- und vor dem `canplay`-Ereignis ausgelöst.

## Beispiele
### Beispiel 1: Einfaches Video-Element
```html
<video id="meinVideo" width="600" controls>
    <source src="film.mp4" type="video/mp4">
    Ihr Browser unterstützt das Video-Tag nicht.
</video>
<script>
    const videoElement = document.getElementById('meinVideo');
    videoElement.onloadeddata = function() {
        console.log('Video-Daten geladen.');
        videoElement.play();
    };
</script>
```

### Beispiel 2: Audio-Element mit Benutzerinteraktion
```html
<audio id="meinAudio" controls>
    <source src="musik.mp3" type="audio/mpeg">
    Ihr Browser unterstützt das Audio-Tag nicht.
</audio>
<script>
    const audioElement = document.getElementById('meinAudio');
    audioElement.onloadeddata = function() {
        console.log('Audio-Daten geladen.');
        document.getElementById('playButton').disabled = false; // Aktiviert einen Play-Button
    };
</script>
<button id="playButton" disabled onclick="audioElement.play()">Abspielen</button>
```

## Erklärung
### Häufige Fehler und Hinweise
- **Ereignis-Abhängigkeiten**: Stellen Sie sicher, dass das `onloadeddata`-Ereignis nicht mit dem `loadedmetadata`-Ereignis verwechselt wird, das ausgelöst wird, sobald die Metadaten geladen sind.
- **Korrekte Elementreferenz**: Vergewissern Sie sich, dass das Media-Element im DOM vorhanden ist, bevor Sie darauf zugreifen. Andernfalls könnte ein Fehler auftreten.
- **Browserkompatibilität**: Obwohl die meisten modernen Browser `onloadeddata` unterstützen, sollten Sie immer die Kompatibilität mit älteren Browsern überprüfen, wenn Ihre Anwendung eine breite Zielgruppe hat.

## Ein-Satz-Zusammenfassung
Das `onloadeddata`-Ereignis in JavaScript ermöglicht Entwicklern, auf das erfolgreiche Laden von Mediendaten eines Video- oder Audio-Elements zu reagieren.