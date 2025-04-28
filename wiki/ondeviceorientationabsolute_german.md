<!--
Meta Description: # ondeviceorientationabsolute: JavaScript-Event für Geräteorientierung ## Synopsis Das `ondeviceorientationabsolute` Event in JavaScript ermöglicht En...
Meta Keywords: die, event, der, das, alpha
-->

# ondeviceorientationabsolute: JavaScript-Event für Geräteorientierung

## Synopsis
Das `ondeviceorientationabsolute` Event in JavaScript ermöglicht Entwicklern den Zugriff auf die absolute Geräteorientierung, wodurch die Ausrichtung eines Geräts im dreidimensionalen Raum erfasst wird. Dies ist besonders nützlich für Anwendungen, die Augmented Reality, Spiele oder interaktive Benutzeroberflächen nutzen.

## Documentation
Das `ondeviceorientationabsolute` Event ist ein Teil der DeviceOrientation API und wird ausgelöst, wenn sich die Orientierung eines Geräts ändert. Die absolute Orientierung bezieht sich auf die Ausrichtung des Geräts im Bezug auf das Erdmagnetfeld, was eine genauere Positionierung im Raum ermöglicht.

### Zweck
Der Hauptzweck des `ondeviceorientationabsolute` Events besteht darin, Entwicklern zu ermöglichen, die Ausrichtung eines Geräts relativ zur Erdoberfläche zu bestimmen. Dies kann für verschiedene Anwendungen wie Navigation, Spiele oder AR verwendet werden.

### Verwendung
Um `ondeviceorientationabsolute` zu verwenden, muss zunächst sichergestellt werden, dass das Gerät die DeviceOrientation API unterstützt. Der Zugriff auf die API erfordert in der Regel auch die Erlaubnis des Benutzers.

Hier ist ein einfaches Beispiel, wie das Event implementiert werden kann:

```javascript
if (window.DeviceOrientationEvent && typeof DeviceOrientationEvent.requestPermission === 'function') {
    DeviceOrientationEvent.requestPermission()
        .then(function(permissionState) {
            if (permissionState === 'granted') {
                window.addEventListener('deviceorientationabsolute', function(event) {
                    console.log('Alpha: ' + event.alpha); // Drehung um die Z-Achse
                    console.log('Beta: ' + event.beta);   // Drehung um die X-Achse
                    console.log('Gamma: ' + event.gamma); // Drehung um die Y-Achse
                });
            }
        })
        .catch(function(error) {
            console.error('Permission denied:', error);
        });
} else {
    console.log('DeviceOrientationEvent is not supported on this device.');
}
```

## Examples
### Beispiel 1: Grundlegende Nutzung
In diesem Beispiel wird die absolute Orientierung des Gerätes erfasst und in der Konsole ausgegeben.

```javascript
window.addEventListener('deviceorientationabsolute', function(event) {
    alert('Alpha: ' + event.alpha + ', Beta: ' + event.beta + ', Gamma: ' + event.gamma);
});
```

### Beispiel 2: Visualisierung der Orientierung
In diesem Beispiel wird die Orientierung verwendet, um die Rotation eines Elements auf der Seite zu steuern.

```javascript
const box = document.getElementById('box');
window.addEventListener('deviceorientationabsolute', function(event) {
    box.style.transform = `rotateZ(${event.alpha}deg) rotateX(${event.beta}deg) rotateY(${event.gamma}deg)`;
});
```

## Explanation
### Häufige Stolpersteine
- **Browser-Support:** Nicht alle Browser unterstützen die DeviceOrientation API vollständig. Überprüfen Sie die Kompatibilität, bevor Sie diese Funktion implementieren.
- **Benutzererlaubnis:** Mit der Einführung von Datenschutzbestimmungen müssen Benutzer die Verwendung der DeviceOrientation API ausdrücklich genehmigen.
- **Geräteeinstellungen:** Einige Geräte müssen möglicherweise in ihren Einstellungen so konfiguriert werden, dass die Sensoren aktiviert sind.

### Zusätzliche Hinweise
- Die Werte für Alpha, Beta und Gamma sind in Grad angegeben. Alpha ist die Drehung um die Z-Achse, Beta um die X-Achse und Gamma um die Y-Achse.
- Das Event kann häufig ausgelöst werden, daher ist eine angemessene Optimierung und Verarbeitung der Daten wichtig, um Leistungsprobleme zu vermeiden.

## One Line Summary
Das `ondeviceorientationabsolute` Event in JavaScript ermöglicht den Zugriff auf die absolute Ausrichtung eines Geräts im Raum und ist entscheidend für interaktive Anwendungen.