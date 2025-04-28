<!--
Meta Description: # onprogress in JavaScript: Fortschrittsereignisse für asynchrone Operationen ## Synopsis Das `onprogress`-Ereignis in JavaScript ermöglicht Entwickle...
Meta Keywords: xhr, event, onprogress, fortschritt, var
-->

# onprogress in JavaScript: Fortschrittsereignisse für asynchrone Operationen

## Synopsis
Das `onprogress`-Ereignis in JavaScript ermöglicht Entwicklern, den Fortschritt von asynchronen Operationen, wie z.B. Dateiübertragungen oder Datenanfragen, zu überwachen. Es wird häufig in Verbindung mit dem `XMLHttpRequest`-Objekt und der Fetch-API verwendet.

## Dokumentation
Das `onprogress`-Ereignis wird ausgelöst, wenn der Fortschritt einer asynchronen Operation aktualisiert wird. Es bietet Entwicklern die Möglichkeit, Benutzer über den Status von Downloads oder Uploads zu informieren. Dieses Ereignis ist besonders nützlich in Web-Anwendungen, die große Datenmengen verarbeiten, da es eine bessere Benutzererfahrung ermöglicht.

### Verwendung
Um das `onprogress`-Ereignis zu verwenden, müssen Sie es an das `XMLHttpRequest`-Objekt oder Fetch-API-Anfragen anhängen. Hier ist ein Beispiel für die Verwendung mit `XMLHttpRequest`:

```javascript
var xhr = new XMLHttpRequest();
xhr.open("GET", "your-url-here", true);

xhr.onprogress = function(event) {
    if (event.lengthComputable) {
        var percentComplete = (event.loaded / event.total) * 100;
        console.log("Fortschritt: " + percentComplete + "%");
    }
};

xhr.onload = function() {
    console.log("Laden abgeschlossen!");
};

xhr.send();
```

## Beispiele
### Beispiel 1: Fortschritt bei einem Datei-Upload
```javascript
var formData = new FormData();
formData.append("file", fileInput.files[0]);

var xhr = new XMLHttpRequest();
xhr.open("POST", "upload-url-here", true);

xhr.upload.onprogress = function(event) {
    if (event.lengthComputable) {
        var percentComplete = (event.loaded / event.total) * 100;
        console.log("Upload Fortschritt: " + percentComplete + "%");
    }
};

xhr.onload = function() {
    console.log("Upload abgeschlossen!");
};

xhr.send(formData);
```

### Beispiel 2: Fortschritt bei einem Download
```javascript
var xhr = new XMLHttpRequest();
xhr.open("GET", "download-url-here", true);

xhr.onprogress = function(event) {
    if (event.lengthComputable) {
        var percentComplete = (event.loaded / event.total) * 100;
        console.log("Download Fortschritt: " + percentComplete + "%");
    }
};

xhr.onload = function() {
    console.log("Download abgeschlossen!");
};

xhr.send();
```

## Erklärung
Ein häufiger Fehler bei der Verwendung des `onprogress`-Ereignisses ist die Annahme, dass `event.lengthComputable` immer `true` ist. In einigen Fällen, z.B. bei Streaming-Daten, kann dies `false` sein, was bedeutet, dass der Fortschritt nicht genau gemessen werden kann. Entwickler sollten diesen Fall berücksichtigen und entsprechende Fallback-Mechanismen implementieren.

Darüber hinaus kann das `onprogress`-Ereignis mehrmals während einer Übertragung ausgelöst werden, was bedeutet, dass der Fortschritt mehrmals aktualisiert wird. Es ist wichtig, sicherzustellen, dass die Benutzeroberfläche entsprechend aktualisiert wird, um eine konsistente Benutzererfahrung zu gewährleisten.

## Zusammenfassung in einem Satz
Das `onprogress`-Ereignis in JavaScript ermöglicht es Entwicklern, den Fortschritt asynchroner Operationen wie Dateiübertragungen zu verfolgen und die Benutzer über den Status der jeweiligen Vorgänge zu informieren.