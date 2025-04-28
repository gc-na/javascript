<!--
Meta Description: # onstalled in JavaScript: Ereignisse beim Puffer-Download ## Synopsis Das `onstalled`-Ereignis in JavaScript wird ausgelöst, wenn der Download eines ...
Meta Keywords: onstalled, ist, ereignis, console, das
-->

# onstalled in JavaScript: Ereignisse beim Puffer-Download

## Synopsis
Das `onstalled`-Ereignis in JavaScript wird ausgelöst, wenn der Download eines Datenstroms vorübergehend ausgesetzt wird, typischerweise bei der Verwendung von `XMLHttpRequest` oder Fetch-API für Netzwerkaufrufe.

## Documentation
Das `onstalled`-Ereignis ist Teil des `ProgressEvent` und wird verwendet, um den Status eines Netzwerkdownloads zu überwachen. Wenn der Download aus irgendeinem Grund nicht fortgesetzt werden kann, wird dieses Ereignis aktiviert. Dies kann aufgrund von Netzwerkproblemen, Verzögerungen im Server oder anderen unerwarteten Bedingungen auftreten.

### Verwendung
Um das `onstalled`-Ereignis zu verwenden, müssen Sie einen Netzwerkaufruf mit `XMLHttpRequest` oder der Fetch-API durchführen und einen Event-Listener für das `onstalled`-Ereignis hinzufügen. Hier ist ein einfaches Beispiel für die Verwendung mit `XMLHttpRequest`.

### Details
- **Ereignistyp:** `ProgressEvent`
- **Ziel:** `XMLHttpRequest` oder `fetch`-Aufrufe
- **Auslösebedingungen:** Wenn der Datenfluss gestoppt ist
- **Verwendung:** Überwachen von Netzwerkaktivitäten und Fehlerbehandlung

## Beispiele
### Beispiel 1: Verwendung mit XMLHttpRequest
```javascript
const xhr = new XMLHttpRequest();
xhr.open('GET', 'https://example.com/data');

xhr.onprogress = function(event) {
    console.log(`Fortschritt: ${event.loaded} von ${event.total} Bytes`);
};

xhr.onstalled = function(event) {
    console.log('Download ist vorübergehend ausgesetzt.');
};

xhr.onload = function() {
    console.log('Download erfolgreich abgeschlossen.');
};

xhr.onerror = function() {
    console.error('Ein Fehler ist aufgetreten.');
};

xhr.send();
```

### Beispiel 2: Verwendung mit Fetch-API
```javascript
async function fetchData() {
    const controller = new AbortController();
    const signal = controller.signal;

    fetch('https://example.com/data', { signal })
        .then(response => {
            // Hier können Sie den Stream überwachen
            const reader = response.body.getReader();
            reader.read().then(function processText({ done, value }) {
                if (done) {
                    console.log('Download abgeschlossen.');
                    return;
                }
                console.log('Daten empfangen:', value);
                reader.read().then(processText);
            });
        })
        .catch(err => {
            if (err.name === 'AbortError') {
                console.log('Fetch wurde abgebrochen.');
            } else {
                console.error('Ein Fehler ist aufgetreten:', err);
            }
        });
}

// Um den Fetch-Vorgang abzubrechen und das onstalled-ähnliche Verhalten zu simulieren
const abortController = new AbortController();
fetchData();
```

## Erklärung
Ein häufiger Stolperstein beim Umgang mit dem `onstalled`-Ereignis ist, dass Entwickler möglicherweise nicht alle möglichen Netzwerkbedingungen berücksichtigen, die zu einem Aussetzen des Downloads führen können. Es ist wichtig, auch auf andere Ereignisse wie `onerror` und `onload` zu reagieren, um eine umfassende Fehlerbehandlung zu gewährleisten. 

Darüber hinaus sollten Sie beachten, dass nicht alle Browser das `onstalled`-Ereignis gleich implementieren, was zu Inkonsistenzen führen kann. Es ist ratsam, die Kompatibilität in der jeweiligen Browserdokumentation zu überprüfen.

## Ein-Satz-Zusammenfassung
Das `onstalled`-Ereignis in JavaScript signalisiert, dass ein Netzwerkdownload vorübergehend ausgesetzt wurde, und ermöglicht Entwicklern, den Status von Datenübertragungen zu überwachen.