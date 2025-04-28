<!--
Meta Description: # ondeviceorientation: JavaScript-Event zur Erfassung der Geräteorientierung ## Synopsis Das `ondeviceorientation`-Event in JavaScript ermöglicht Entw...
Meta Keywords: die, event, der, auf, das
-->

# ondeviceorientation: JavaScript-Event zur Erfassung der Geräteorientierung

## Synopsis
Das `ondeviceorientation`-Event in JavaScript ermöglicht Entwicklern den Zugriff auf die Orientierung eines Gerätes, indem es Informationen über die Neigung und Drehung des Geräts bereitstellt. Dies wird häufig in Webanwendungen verwendet, die auf mobile Geräte abzielen, um interaktive und immersive Erlebnisse zu schaffen.

## Dokumentation
### Zweck
Das `ondeviceorientation`-Event ist Teil der Device Orientation API, die es Webanwendungen ermöglicht, die physikalische Orientierung eines Gerätes zu ermitteln. Dies ist besonders nützlich für Anwendungen, die Augmented Reality, Spiele oder andere interaktive Features implementieren, die auf der Gerätebewegung basieren.

### Verwendung
Um das `ondeviceorientation`-Event zu nutzen, müssen Sie einen Event-Listener für das `window`-Objekt hinzufügen. Der Listener reagiert auf Änderungen der Geräteorientierung.

**Syntax:**
```javascript
window.addEventListener('deviceorientation', function(event) {
    // Ihre Logik hier
});
```

### Details
Das Event gibt ein `DeviceOrientationEvent`-Objekt weiter, das folgende Eigenschaften enthält:
- `alpha`: Die Drehung um die z-Achse (Kopfbewegung), in Grad.
- `beta`: Die Neigung um die x-Achse (Kippen nach vorne oder hinten), in Grad.
- `gamma`: Die Neigung um die y-Achse (Kippen nach links oder rechts), in Grad.

Die Werte können von 0 bis 360 Grad variieren, wobei negative Werte nicht gültig sind.

## Beispiele
### Grundlegende Verwendung
```javascript
window.addEventListener('deviceorientation', function(event) {
    const alpha = event.alpha; // Drehung um die Z-Achse
    const beta = event.beta;   // Neigung um die X-Achse
    const gamma = event.gamma; // Neigung um die Y-Achse

    console.log(`Alpha: ${alpha}, Beta: ${beta}, Gamma: ${gamma}`);
});
```

### Anwendung in einer Grafik
```javascript
const box = document.getElementById('box');

window.addEventListener('deviceorientation', function(event) {
    box.style.transform = `rotateZ(${event.alpha}deg) rotateX(${event.beta}deg) rotateY(${event.gamma}deg)`;
});
```

## Erklärung
Ein häufiges Problem bei der Verwendung von `ondeviceorientation` ist, dass einige Browser, insbesondere auf mobilen Geräten, die Zustimmung des Benutzers für den Zugriff auf Sensordaten benötigen. Stellen Sie sicher, dass Sie die erforderlichen Berechtigungen einholen, bevor Sie versuchen, auf die Geräteorientierung zuzugreifen. 

Zusätzlich kann es zu unterschiedlichen Ergebnissen kommen, abhängig von der Hardware und den Einstellungen des Geräts. Es ist ratsam, die Werte vor der Verwendung zu normalisieren und zu überprüfen, ob sie innerhalb der erwarteten Bereiche liegen.

## Ein-Satz-Zusammenfassung
Das `ondeviceorientation`-Event in JavaScript ermöglicht den Zugriff auf die physische Orientierung eines Geräts und ist ideal für interaktive Webanwendungen.