<!--
Meta Description: # IDBRequest in JavaScript: Alles, was Sie wissen müssen ## Synopsis `IDBRequest` ist ein zentraler Bestandteil der IndexedDB-API in JavaScript, der e...
Meta Keywords: der, die, anfrage, idbrequest, ein
-->

# IDBRequest in JavaScript: Alles, was Sie wissen müssen

## Synopsis
`IDBRequest` ist ein zentraler Bestandteil der IndexedDB-API in JavaScript, der es Entwicklern ermöglicht, asynchrone Datenbankanfragen zu stellen und deren Ergebnisse zu verwalten.

## Dokumentation
`IDBRequest` ist ein Objekt, das das Ergebnis einer Anfrage an eine IndexedDB-Datenbank darstellt. Es wird verwendet, um Datenoperationen wie das Hinzufügen, Aktualisieren, Löschen oder Abrufen von Daten durchzuführen. `IDBRequest` bietet Ereignisse, die es ermöglichen, auf den erfolgreichen Abschluss oder auf Fehler bei einer Anfrage zu reagieren.

### Zweck
Der Hauptzweck von `IDBRequest` besteht darin, eine Schnittstelle für asynchrone Datenbankoperationen zu bieten. Es ermöglicht Entwicklern, auf die Ergebnisse von Datenbankoperationen zuzugreifen, während die Benutzeroberfläche reaktionsfähig bleibt.

### Verwendung
Ein `IDBRequest`-Objekt wird in der Regel von Methoden wie `add()`, `put()`, `delete()`, oder `get()` aufgerufen. Nach dem Ausführen einer dieser Methoden können Sie die Eigenschaften und Ereignisse des `IDBRequest`-Objekts verwenden, um den Status der Anfrage zu überwachen.

#### Eigenschaften
- `result`: Enthält das Ergebnis der Anfrage, wenn diese erfolgreich war.
- `error`: Enthält den Fehler, falls die Anfrage fehlgeschlagen ist.
- `readyState`: Gibt den aktuellen Status der Anfrage zurück, der entweder `pending`, `done`, oder `blocked` sein kann.

#### Ereignisse
- `onsuccess`: Wird aufgerufen, wenn die Anfrage erfolgreich abgeschlossen wurde.
- `onerror`: Wird aufgerufen, wenn ein Fehler bei der Anfrage aufgetreten ist.

## Beispiele
### Beispiel 1: Einfügen eines Datensatzes
```javascript
let request = db.transaction(['myObjectStore'], 'readwrite')
                .objectStore('myObjectStore')
                .add({ id: 1, name: 'Beispiel' });

request.onsuccess = function(event) {
    console.log('Datensatz erfolgreich hinzugefügt:', event.target.result);
};

request.onerror = function(event) {
    console.error('Fehler beim Hinzufügen des Datensatzes:', event.target.error);
};
```

### Beispiel 2: Abrufen eines Datensatzes
```javascript
let request = db.transaction(['myObjectStore'])
                .objectStore('myObjectStore')
                .get(1);

request.onsuccess = function(event) {
    console.log('Datensatz abgerufen:', event.target.result);
};

request.onerror = function(event) {
    console.error('Fehler beim Abrufen des Datensatzes:', event.target.error);
};
```

## Erklärung
Ein häufiger Fehler beim Arbeiten mit `IDBRequest` ist die Annahme, dass die Anfrage sofort ein Ergebnis liefert. Da IndexedDB asynchron arbeitet, sollte man immer die `onsuccess`- und `onerror`-Ereignisse verwenden, um den Abschluss der Anfrage zu behandeln. Außerdem ist es wichtig, die Transaktionen ordnungsgemäß zu verwalten, um Datenintegrität und -konsistenz zu gewährleisten.

## Ein-Satz-Zusammenfassung
`IDBRequest` ist ein JavaScript-Objekt, das asynchrone Datenbankanfragen an IndexedDB verwaltet und es Entwicklern ermöglicht, auf die Ergebnisse der Operationen zu reagieren.