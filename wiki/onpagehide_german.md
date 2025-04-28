<!--
Meta Description: # onpagehide: Ereignis in JavaScript zur Überwachung von Seitenverlassen ## Synopsis Das `onpagehide`-Ereignis in JavaScript wird verwendet, um eine F...
Meta Keywords: ereignis, das, onpagehide, wird, die
-->

# onpagehide: Ereignis in JavaScript zur Überwachung von Seitenverlassen

## Synopsis
Das `onpagehide`-Ereignis in JavaScript wird verwendet, um eine Funktion auszuführen, wenn eine Seite verlassen wird, sei es durch Navigieren zu einer anderen Seite oder durch Schließen des Browser-Tabs. Es ist besonders nützlich, um den Zustand der Anwendung zu speichern oder um Cleanup-Aufgaben durchzuführen.

## Dokumentation
Das `onpagehide`-Ereignis gehört zur Window-Schnittstelle und wird ausgelöst, wenn die aktuelle Seite ausgeblendet wird. Dies kann durch einen Seitenwechsel oder das Schließen des Fensters geschehen. Das Ereignis ist Teil der Page Lifecycle Events und wird in der Regel in Verbindung mit dem `onpageshow`-Ereignis verwendet.

### Verwendung
Um das `onpagehide`-Ereignis zu verwenden, müssen Sie einen Event-Listener hinzufügen, der auf dieses Ereignis reagiert. Hier ist ein allgemeines Beispiel für die Verwendung:

```javascript
window.onpagehide = function(event) {
    console.log("Die Seite wird ausgeblendet.");
    // Hier können Sie Ihre Logik zum Speichern des Zustands implementieren
};
```

### Details
- **Ereignisobjekt**: Das übergebene `event`-Objekt enthält Informationen über das Ereignis. Es hat eine `persisted`-Eigenschaft, die angibt, ob die Seite im Cache gespeichert wurde.
- **Kompatibilität**: `onpagehide` ist in den meisten modernen Browsern verfügbar, jedoch sollten Sie die Browserkompatibilität prüfen, wenn Sie diese Funktion verwenden möchten.
- **Verhalten**: Wenn der Benutzer die Seite zurückkehrt, wird das `onpageshow`-Ereignis ausgelöst, was eine gute Möglichkeit ist, um den vorherigen Zustand wiederherzustellen.

## Beispiele
### Einfaches Beispiel

```javascript
window.onpagehide = function(event) {
    console.log("Die Seite wird ausgeblendet.");
};
```

### Beispiel mit Zustandsspeicherung

```javascript
let userData = {};

window.onpagehide = function(event) {
    userData.someKey = "someValue"; // Speichern von Daten vor dem Verlassen
    localStorage.setItem('userData', JSON.stringify(userData));
};
```

## Erklärung
Ein häufiger Stolperstein beim Umgang mit dem `onpagehide`-Ereignis ist, dass Entwickler möglicherweise erwarten, dass das Ereignis auch ausgelöst wird, wenn der Benutzer einfach zwischen Tabs wechselt. Das `onpagehide`-Ereignis wird jedoch nur ausgelöst, wenn die Seite vollständig ausgeblendet wird, nicht nur bei einem Tab-Wechsel. Achten Sie darauf, dass Sie den Code im richtigen Kontext verwenden und dass Sie bei der Implementierung von Logik zur Datenpersistenz sicherstellen, dass die Daten ordnungsgemäß gespeichert werden.

## Ein-Satz-Zusammenfassung
Das `onpagehide`-Ereignis ermöglicht es Entwicklern, Aktionen beim Verlassen einer Seite auszuführen, was ideal für das Speichern von Zustand oder das Durchführen von Cleanup-Aufgaben ist.