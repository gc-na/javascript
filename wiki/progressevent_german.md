<!--
Meta Description: # ProgressEvent in JavaScript: Ein umfassender Leitfaden ## Synopsis Der `ProgressEvent` in JavaScript ist ein Ereignistyp, der Informationen über den...
Meta Keywords: der, die, progressevent, fortschritt, von
-->

# ProgressEvent in JavaScript: Ein umfassender Leitfaden

## Synopsis
Der `ProgressEvent` in JavaScript ist ein Ereignistyp, der Informationen über den Fortschritt eines laufenden Vorgangs bereitstellt, wie z.B. das Laden von Ressourcen. Er ist besonders nützlich bei der Überwachung von Asynchronen Operationen, wie Downloads oder Uploads.

## Dokumentation
Der `ProgressEvent` wird ausgelöst, wenn der Fortschritt eines Asynchrone Vorgangs aktualisiert wird. Dies geschieht typischerweise bei HTTP-Anfragen oder beim Laden von Mediendateien. Der Event bietet Zugriff auf nützliche Informationen, wie die Anzahl der bisher übertragenen Bytes und die Gesamtanzahl der Bytes, die übertragen werden müssen.

### Eigenschaften
- **loaded**: Die Anzahl der bereits geladenen Bytes.
- **total**: Die Gesamtanzahl der Bytes, die übertragen werden müssen (kann `undefined` sein, wenn die Größe unbekannt ist).
- **lengthComputable**: Ein Boolescher Wert, der angibt, ob die Gesamtgröße bekannt ist.

### Verwendung
Um einen `ProgressEvent` zu nutzen, müssen Sie einen Listener für das Ereignis registrieren, der den Fortschritt verarbeitet. Dies geschieht in der Regel durch die Verwendung von `XMLHttpRequest` oder der Fetch-API mit einem `ReadableStream`.

## Beispiele
### Beispiel 1: Verwenden von XMLHttpRequest
```javascript
const xhr = new XMLHttpRequest();
xhr.open("GET", "https://example.com/large-file", true);

xhr.onprogress = function(event) {
    if (event.lengthComputable) {
        const percentComplete = (event.loaded / event.total) * 100;
        console.log(`Fortschritt: ${percentComplete}%`);
    } else {
        console.log(`Lade: ${event.loaded} Bytes`);
    }
};

xhr.onload = function() {
    console.log("Laden abgeschlossen!");
};

xhr.send();
```

### Beispiel 2: Verwenden der Fetch-API
```javascript
const url = "https://example.com/large-file";

fetch(url)
    .then(response => {
        const reader = response.body.getReader();
        const contentLength = +response.headers.get("Content-Length");
        let receivedLength = 0;

        function read() {
            return reader.read().then(({ done, value }) => {
                if (done) {
                    console.log("Laden abgeschlossen!");
                    return;
                }
                receivedLength += value.length;
                const percentComplete = (receivedLength / contentLength) * 100;
                console.log(`Fortschritt: ${percentComplete}%`);
                return read();
            });
        }

        return read();
    });
```

## Erklärung
Bei der Arbeit mit `ProgressEvent` gibt es einige häufige Fallstricke, die Sie beachten sollten:

- **lengthComputable**: Nicht alle Ereignisse geben eine Gesamtgröße zurück. Wenn `lengthComputable` auf `false` steht, können Sie die prozentuale Vervollständigung nicht berechnen.
- **Browser-Kompatibilität**: Stellen Sie sicher, dass der verwendete Browser `ProgressEvent` unterstützt, insbesondere bei älteren Versionen.
- **Asynchrone Operationen**: Wenn Sie mehrere gleichzeitige Downloads oder Uploads durchführen, achten Sie darauf, dass die `ProgressEvent`-Handler korrekt zugeordnet sind.

## Ein-Satz-Zusammenfassung
Der `ProgressEvent` in JavaScript ermöglicht es Entwicklern, den Fortschritt von asynchronen Vorgängen wie Downloads und Uploads zu überwachen und zu verarbeiten.