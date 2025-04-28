<!--
Meta Description: # JavaScript onseeked: Ereignis für Mediensteuerung verstehen ## Synopsis Das `onseeked`-Ereignis in JavaScript wird ausgelöst, wenn ein Benutzer die ...
Meta Keywords: onseeked, das, video, ereignis, videoelement
-->

# JavaScript onseeked: Ereignis für Mediensteuerung verstehen

## Synopsis
Das `onseeked`-Ereignis in JavaScript wird ausgelöst, wenn ein Benutzer die Position eines Medien-Elements (z.B. Video oder Audio) erfolgreich geändert hat. Dieses Ereignis ist besonders nützlich für die Implementierung von Benutzeroberflächen zur Mediensteuerung.

## Dokumentation
Das `onseeked`-Ereignis gehört zur HTMLMediaElement-Schnittstelle und wird aktiviert, nachdem ein Benutzer eine neue Zeitposition in einem Medien-Element festgelegt hat. Das Ereignis signalisiert, dass das Medien-Element nun an der neuen Position bereit ist, wiedergegeben zu werden.

### Zweck
- Verfolgen von Änderungen der Wiedergabeposition.
- Aktualisieren von Benutzeroberflächen-Elementen (z.B. Zeitanzeigen, Schaltflächen) nach einem Seek-Vorgang.

### Verwendung
Um das `onseeked`-Ereignis zu verwenden, müssen Sie einen Event-Listener an ein HTMLMediaElement (z.B. `<video>`, `<audio>`) anhängen. 

```javascript
const videoElement = document.getElementById('meinVideo');

videoElement.onseeked = function() {
    console.log('Die Wiedergabeposition wurde geändert.');
};
```

### Details
- Das `onseeked`-Ereignis wird nur ausgelöst, wenn der Seek-Vorgang abgeschlossen ist. 
- Es ist wichtig, zwischen `onseeked` und `onseeking` zu unterscheiden. Während `onseeking` ausgelöst wird, wenn ein Seek-Vorgang begonnen hat, signalisiert `onseeked` das Ende des Vorgangs.

## Beispiele
Hier sind einige grundlegende Beispiele, wie Sie das `onseeked`-Ereignis implementieren können:

### Beispiel 1: Einfaches Logging
```html
<video id="meinVideo" controls>
    <source src="video.mp4" type="video/mp4">
    Ihr Browser unterstützt das Video-Tag nicht.
</video>

<script>
const videoElement = document.getElementById('meinVideo');

videoElement.onseeked = function() {
    console.log('Die Wiedergabeposition wurde geändert zu: ' + videoElement.currentTime);
};
</script>
```

### Beispiel 2: Benutzeroberfläche aktualisieren
```html
<video id="meinVideo" controls>
    <source src="video.mp4" type="video/mp4">
    Ihr Browser unterstützt das Video-Tag nicht.
</video>
<div id="aktuelleZeit">Aktuelle Zeit: 0s</div>

<script>
const videoElement = document.getElementById('meinVideo');
const aktuelleZeit = document.getElementById('aktuelleZeit');

videoElement.onseeked = function() {
    aktuelleZeit.textContent = 'Aktuelle Zeit: ' + videoElement.currentTime.toFixed(2) + 's';
};
</script>
```

## Erklärung
Ein häufiger Stolperstein bei der Verwendung von `onseeked` ist, dass viele Entwickler möglicherweise `onseeking` verwenden, um den Status des Suchvorgangs zu überprüfen. Dies kann zu Verwirrung führen, da `onseeking` häufig ausgelöst wird, bevor der eigentliche Seek-Vorgang abgeschlossen ist. Stellen Sie sicher, dass Sie `onseeked` verwenden, um genaue Informationen über die neue Wiedergabeposition zu erhalten.

Das `onseeked`-Ereignis ist auch nicht für alle Medien-Elemente verfügbar. Stellen Sie sicher, dass das Element, an das Sie den Listener anhängen, sowohl Audio- als auch Videoformate unterstützt.

## Ein-Satz-Zusammenfassung
Das `onseeked`-Ereignis in JavaScript wird verwendet, um auf die Änderung der Wiedergabeposition eines Medien-Elements zu reagieren, nachdem ein Benutzer einen Seek-Vorgang abgeschlossen hat.