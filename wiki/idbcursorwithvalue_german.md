<!--
Meta Description: # IDBCursorWithValue in JavaScript: Ein umfassender Leitfaden ## Synopsis Der `IDBCursorWithValue` ist ein essentielles Interface in der IndexedDB API...
Meta Keywords: cursor, let, idbcursorwithvalue, event, value
-->

# IDBCursorWithValue in JavaScript: Ein umfassender Leitfaden

## Synopsis
Der `IDBCursorWithValue` ist ein essentielles Interface in der IndexedDB API von JavaScript, das es Entwicklern ermöglicht, über Datensätze in einer Datenbank zu iterieren und gleichzeitig den Wert jedes Datensatzes zu erhalten.

## Dokumentation

### Zweck
`IDBCursorWithValue` wird verwendet, um durch Datensätze einer IndexedDB zu navigieren. Im Gegensatz zu einem regulären `IDBCursor` gibt `IDBCursorWithValue` den Wert des aktuellen Datensatzes direkt zurück, was die Arbeit mit den Daten erheblich vereinfacht.

### Verwendung
Um einen `IDBCursorWithValue` zu erstellen, müssen Sie zunächst eine IndexedDB-Datenbank öffnen und einen Transaktionskontext erstellen. Anschließend können Sie einen Cursor auf ein Object Store oder einen Index setzen, um über die Datensätze zu iterieren.

### Details
- **Methoden**: `continue()`, `delete()`, `update()`
- **Eigenschaften**: `direction`, `key`, `value`
- **Richtungen**: `next`, `prev`, `nextunique`, `prevunique`

## Beispiele

### Beispiel 1: Einfacher Cursor mit Wert
```javascript
let request = indexedDB.open("MyDatabase");

request.onsuccess = function(event) {
    let db = event.target.result;
    let transaction = db.transaction("MyObjectStore", "readonly");
    let objectStore = transaction.objectStore("MyObjectStore");
    
    let cursorRequest = objectStore.openCursor();
    
    cursorRequest.onsuccess = function(event) {
        let cursor = event.target.result;
        if (cursor) {
            console.log("Key: " + cursor.key + ", Value: ", cursor.value);
            cursor.continue();
        }
    };
};
```

### Beispiel 2: Verwenden von IDBCursorWithValue
```javascript
let request = indexedDB.open("MyDatabase");

request.onsuccess = function(event) {
    let db = event.target.result;
    let transaction = db.transaction("MyObjectStore", "readonly");
    let objectStore = transaction.objectStore("MyObjectStore");
    
    let cursorRequest = objectStore.openCursor();
    
    cursorRequest.onsuccess = function(event) {
        let cursor = event.target.result;
        if (cursor) {
            let value = cursor.value; // Zugriff auf den Wert
            console.log("Key: " + cursor.key + ", Value: ", value);
            cursor.continue();
        }
    };
};
```

## Erklärung
Ein häufiger Stolperstein bei der Verwendung von `IDBCursorWithValue` ist das Missverständnis bezüglich der Transaktionssicherheit. Alle Lese- und Schreiboperationen müssen innerhalb einer aktiven Transaktion stattfinden. Ein weiterer Hinweis ist, dass der Cursor nur dann Daten zurückgibt, wenn die Datenbank erfolgreich geöffnet wurde. Überprüfen Sie immer die `onsuccess` und `onerror` Ereignisse, um sicherzustellen, dass Ihre Datenbankoperationen erfolgreich sind.

## Ein-Satz-Zusammenfassung
`IDBCursorWithValue` ermöglicht eine einfache Iteration über Datensätze in einer IndexedDB und gibt gleichzeitig die Werte der Datensätze zurück.