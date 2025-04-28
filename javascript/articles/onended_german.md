<!--
Meta Description: # onended: Ereignis in JavaScript zur Behandlung des Endes von Mediendateien ## Synopsis Der `onended`-Event-Handler ist eine wichtige Funktion in Jav...
Meta Keywords: onended, ist, audio, event, video
-->

# onended: Ereignis in JavaScript zur Behandlung des Endes von Mediendateien

## Synopsis
Der `onended`-Event-Handler ist eine wichtige Funktion in JavaScript, die es Entwicklern ermöglicht, auf das Ende von Medienwiedergaben zu reagieren. Dieser Event wird häufig in Audio- und Videoanwendungen verwendet.

## Dokumentation
Der `onended`-Event wird ausgelöst, wenn ein Mediastream (wie Audio oder Video) zu Ende gespielt wurde. Er kann auf HTMLMediaElementen wie `<audio>` und `<video>` verwendet werden, um benutzerdefinierte Aktionen auszulösen, sobald die Wiedergabe abgeschlossen ist.

### Verwendung
Um den `onended`-Event-Handler zu verwenden, müssen Sie zunächst ein HTMLMediaElement erstellen und dann eine Funktion zuweisen, die ausgeführt wird, wenn der Event ausgelöst wird. Hier ist ein einfaches Beispiel:

```javascript
const audioElement = document.getElementById('myAudio');

audioElement.onended = function() {
    console.log('Die Wiedergabe ist beendet.');
};
```

### Details
- **Typ**: Event-Handler
- **Verfügbar in**: HTML5 Audio und Video
- **Ereignistyp**: `Event`
- **Browserunterstützung**: Alle modernen Browser unterstützen `onended`.

## Beispiele
### Beispiel 1: Einfaches Audio Element
```html
<audio id="myAudio" controls>
    <source src="audiofile.mp3" type="audio/mpeg">
    Ihr Browser unterstützt das Audio-Tag nicht.
</audio>

<script>
    const audioElement = document.getElementById('myAudio');
    
    audioElement.onended = function() {
        alert('Das Audio ist zu Ende.');
    };
</script>
```

### Beispiel 2: Video Element mit Callback
```html
<video id="myVideo" width="320" height="240" controls>
    <source src="videofile.mp4" type="video/mp4">
    Ihr Browser unterstützt das Video-Tag nicht.
</video>

<script>
    const videoElement = document.getElementById('myVideo');
    
    videoElement.onended = function() {
        console.log('Das Video ist zu Ende.');
        // Hier können Sie eine Funktion aufrufen, um das nächste Video zu laden.
    };
</script>
```

## Erklärung
Ein häufiger Stolperstein bei der Verwendung von `onended` ist, dass der Event-Handler möglicherweise nicht wie erwartet funktioniert, wenn der Benutzer die Wiedergabe manuell stoppt oder überspringt. In solchen Fällen wird der `onended`-Event nicht ausgelöst. Es ist auch wichtig, sicherzustellen, dass das Medium vollständig geladen ist, bevor man versucht, `onended` zu verwenden.

Eine weitere Anmerkung ist, dass einige Browser möglicherweise unterschiedliche Verhaltensweisen in Bezug auf die `onended`-Ereignisse aufweisen, insbesondere bei Streaming-Medien. Daher ist es ratsam, umfangreiche Tests in verschiedenen Browsern durchzuführen.

## Ein-Satz-Zusammenfassung
Der `onended`-Event-Handler in JavaScript ermöglicht Entwicklern, Aktionen auszuführen, wenn die Wiedergabe von Audio- oder Videoinhalten abgeschlossen ist.