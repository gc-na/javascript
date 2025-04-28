<!--
Meta Description: # Hintergrundabfrage in JavaScript: HintergrundFetchRecord ## Synopsis Der `BackgroundFetchRecord` ist ein Teil der Background Fetch API in JavaScript...
Meta Keywords: die, der, den, downloads, ist
-->

# Hintergrundabfrage in JavaScript: HintergrundFetchRecord

## Synopsis
Der `BackgroundFetchRecord` ist ein Teil der Background Fetch API in JavaScript, die es Entwicklern ermöglicht, große Dateien im Hintergrund herunterzuladen, ohne dass die Benutzeroberfläche blockiert wird. Diese API ist besonders nützlich für Progressive Web Apps (PWAs).

## Dokumentation
### Zweck
`BackgroundFetchRecord` dient dazu, Informationen über den Status von Hintergrund-Downloads zu verwalten. Es ermöglicht Entwicklern, den Fortschritt, den Status und die Metadaten von Downloads zu überwachen, während der Benutzer weiterhin mit der Anwendung interagieren kann.

### Verwendung
Um `BackgroundFetchRecord` zu verwenden, muss zunächst eine Background Fetch-Anfrage initiiert werden. Diese wird durch den Aufruf der `register`-Methode der `BackgroundFetch`-Schnittstelle gestartet.

### Details
- **Eigenschaften**:
  - `id`: Eine eindeutige Kennung für den Hintergrund-Download.
  - `status`: Der aktuelle Status des Downloads (z. B. "in-progress", "completed", "failed").
  - `uploadedBytes`: Die Anzahl der bereits hochgeladenen Bytes.
  - `downloadedBytes`: Die Anzahl der bereits heruntergeladenen Bytes.
  
- **Methoden**:
  - `abort()`: Beendet den Download.
  - `getFile()`: Gibt eine Referenz auf die heruntergeladenen Dateien zurück.

## Beispiele
### Beispiel 1: Hintergrund-Download initiieren
```javascript
const registration = await navigator.serviceWorker.ready;
const fetchRecord = await registration.backgroundFetch.fetch('example-fetch', [
  new Request('https://example.com/large-file.zip')
]);

console.log(fetchRecord.id); // Gibt die ID des Downloads aus
```

### Beispiel 2: Fortschritt eines Downloads überwachen
```javascript
fetchRecord.addEventListener('progress', () => {
  console.log(`Fortschritt: ${fetchRecord.downloadedBytes} von ${fetchRecord.totalBytes}`);
});
```

## Erklärung
Ein häufiges Problem beim Arbeiten mit `BackgroundFetchRecord` ist, dass Entwickler möglicherweise nicht alle Statusänderungen korrekt überwachen. Es ist wichtig, sich bewusst zu sein, dass Downloads abgebrochen werden können, und die Anwendung entsprechend zu gestalten. Zudem sollte man sicherstellen, dass die Service Worker korrekt registriert sind, da `BackgroundFetch` nur mit aktivierten Service Workern funktioniert.

Ein weiterer wichtiger Punkt ist, dass die Unterstützung für die Background Fetch API in verschiedenen Browsern variieren kann. Es ist ratsam, vor der Implementierung die Kompatibilität zu überprüfen.

## Ein-Satz-Zusammenfassung
Der `BackgroundFetchRecord` ermöglicht es Entwicklern, den Status und Fortschritt von Hintergrund-Downloads in JavaScript zu verwalten, wodurch eine nahtlose Benutzererfahrung in Webanwendungen gewährleistet wird.