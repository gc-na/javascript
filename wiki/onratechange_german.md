<!--
Meta Description: # onratechange: Ereignis für die Änderung der Wiedergabegeschwindigkeit in JavaScript ## Synopsis Das `onratechange`-Ereignis in JavaScript ermöglicht...
Meta Keywords: video, onratechange, ereignis, die, das
-->

# onratechange: Ereignis für die Änderung der Wiedergabegeschwindigkeit in JavaScript

## Synopsis
Das `onratechange`-Ereignis in JavaScript ermöglicht Entwicklern, auf Änderungen der Wiedergabegeschwindigkeit von Medienelementen wie Audio und Video zu reagieren. Es ist besonders nützlich, um Benutzerinteraktionen zu verfolgen und die Benutzererfahrung zu optimieren.

## Dokumentation
### Zweck
Das `onratechange`-Ereignis wird ausgelöst, wenn die Wiedergabegeschwindigkeit eines Medien-Elements (wie `<audio>` oder `<video>`) geändert wird. Dies ermöglicht Entwicklern, dynamisch auf Änderungen zu reagieren, etwa um das Benutzerinterface zu aktualisieren oder spezifische Funktionen zu aktivieren.

### Verwendung
Um das `onratechange`-Ereignis zu verwenden, müssen Sie einen Event-Listener an das entsprechende Medien-Element anhängen. Sie können dies entweder über JavaScript oder direkt im HTML tun. Hier ist ein Beispiel für die Verwendung in JavaScript:

```javascript
const videoElement = document.querySelector('video');

videoElement.onratechange = function() {
    console.log('Die Wiedergabegeschwindigkeit hat sich geändert. Neue Geschwindigkeit: ' + videoElement.playbackRate);
};
```

### Details
- **Elementtyp**: `HTMLMediaElement` (z. B. `<audio>` oder `<video>`)
- **Ereignis**: `ratechange`
- **Wichtige Eigenschaften**: 
  - `playbackRate`: Gibt die aktuelle Wiedergabegeschwindigkeit an.
  
Das `onratechange`-Ereignis ist Teil der Media Events API und wird in modernen Browsern unterstützt. Es ist wichtig, sicherzustellen, dass der Browser, den Ihre Benutzer verwenden, dieses Ereignis unterstützt.

## Beispiele
### Beispiel 1: Einfaches `onratechange`-Ereignis
```html
<video id="myVideo" controls>
    <source src="movie.mp4" type="video/mp4">
    Ihr Browser unterstützt das Video-Tag nicht.
</video>

<script>
    const video = document.getElementById('myVideo');
    
    video.onratechange = function() {
        console.log('Die Wiedergabegeschwindigkeit ist jetzt: ' + video.playbackRate);
    };
</script>
```

### Beispiel 2: Dynamische Benutzeroberfläche
```html
<video id="myVideo" controls>
    <source src="movie.mp4" type="video/mp4">
</video>
<div id="speedDisplay">Aktuelle Geschwindigkeit: 1.0</div>

<script>
    const video = document.getElementById('myVideo');
    const speedDisplay = document.getElementById('speedDisplay');

    video.onratechange = function() {
        speedDisplay.innerText = 'Aktuelle Geschwindigkeit: ' + video.playbackRate;
    };
</script>
```

## Erklärung
Ein häufiger Fehler beim Arbeiten mit `onratechange` ist, dass Entwickler vergessen, die `playbackRate`-Eigenschaft korrekt zu setzen, bevor das Ereignis ausgelöst wird. Achten Sie darauf, dass die Wiedergabegeschwindigkeit tatsächlich geändert wird, um sicherzustellen, dass das Ereignis ordnungsgemäß funktioniert.

Ein weiteres häufiges Problem ist die Browserkompatibilität. Stellen Sie sicher, dass Sie Ihre Anwendung in verschiedenen Browsern testen, um sicherzustellen, dass das `onratechange`-Ereignis überall korrekt funktioniert.

## Ein Satz Zusammenfassung
Das `onratechange`-Ereignis in JavaScript ermöglicht es Entwicklern, auf Änderungen der Wiedergabegeschwindigkeit von Medieninhalten zu reagieren und die Benutzererfahrung zu verbessern.