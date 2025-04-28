<!--
Meta Description: # ondurationchange in JavaScript: Verwendung und Beispiele ## Synopsis Das `ondurationchange`-Ereignis in JavaScript wird verwendet, um eine Aktion au...
Meta Keywords: das, audio, die, ondurationchange, ereignis
-->

# ondurationchange in JavaScript: Verwendung und Beispiele

## Synopsis
Das `ondurationchange`-Ereignis in JavaScript wird verwendet, um eine Aktion auszulösen, wenn sich die Dauer eines HTMLMediaElement (z. B. `<audio>` oder `<video>`) ändert. Dies ist besonders nützlich für dynamische Medienanwendungen.

## Dokumentation
Das `ondurationchange`-Ereignis gehört zur HTMLMediaElement-Schnittstelle und wird ausgelöst, wenn die Dauer eines Medieninhalts (Audio oder Video) aktualisiert wird. Dies kann geschehen, wenn der Inhalt geladen wird oder sich die Quelle ändert.

### Verwendung
Um das `ondurationchange`-Ereignis zu verwenden, müssen Sie zunächst ein HTMLMediaElement erstellen und dann einen Event-Listener hinzufügen, der auf das `durationchange`-Ereignis reagiert. Hier ist die grundlegende Syntax:

```javascript
mediaElement.ondurationchange = function() {
    // Aktion, die ausgeführt werden soll
};
```

### Details
- **Typ**: Event
- **Event-Typ**: `durationchange`
- **Betrifft**: HTMLMediaElement (wie `<audio>` und `<video>`)

Das `durationchange`-Ereignis wird nicht ausgelöst, wenn die Dauer eines Medieninhalts bereits bekannt ist. Es tritt nur auf, wenn die Dauer zum ersten Mal ermittelt wird oder sich aufgrund von Änderungen in der Quelle ändert.

## Beispiele
Hier sind einige grundlegende Beispiele zur Verwendung des `ondurationchange`-Ereignisses:

### Beispiel 1: Grundlegende Verwendung
```html
<video id="myVideo" controls>
    <source src="movie.mp4" type="video/mp4">
    Ihr Browser unterstützt das Video-Tag nicht.
</video>

<script>
    const video = document.getElementById('myVideo');

    video.ondurationchange = function() {
        console.log('Die Dauer des Videos hat sich geändert:', video.duration);
    };
</script>
```

### Beispiel 2: Reaktion auf Quellenänderung
```html
<audio id="myAudio" controls>
    <source src="audio.mp3" type="audio/mpeg">
    Ihr Browser unterstützt das Audio-Tag nicht.
</audio>

<script>
    const audio = document.getElementById('myAudio');

    audio.ondurationchange = function() {
        console.log('Die Dauer des Audios hat sich geändert:', audio.duration);
    };

    // Ändern der Quelle, um das Ereignis auszulösen
    audio.src = "new-audio.mp3";
    audio.load(); // lädt die neue Quelle
</script>
```

## Erklärung
Ein häufiges Missverständnis ist, dass das `ondurationchange`-Ereignis auch ausgelöst wird, wenn die Medienquelle nicht vollständig geladen ist. In der Realität wird das Ereignis nur ausgelöst, wenn die Dauer des Mediums erfolgreich ermittelt wurde. Auch das Ändern des `src`-Attributs eines Medien-Elements und das anschließende Aufrufen von `load()` kann das Ereignis auslösen.

Ein weiterer Punkt, den es zu beachten gilt, ist, dass beim ersten Laden des Mediums die Dauer möglicherweise nicht sofort verfügbar ist, was zu einer Verzögerung bei der Auslösung des Ereignisses führen kann.

## One Line Summary
Das `ondurationchange`-Ereignis in JavaScript ermöglicht es Entwicklern, auf Änderungen der Medien-Dauer zu reagieren, was für dynamische Multimedia-Anwendungen von Bedeutung ist.