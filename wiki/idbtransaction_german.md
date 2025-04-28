<!--
Meta Description: # IDBTransaction in JavaScript: Eine umfassende Anleitung ## Synopsis Der `IDBTransaction` ist ein zentraler Bestandteil der IndexedDB-API in JavaScri...
Meta Keywords: transaktion, transaction, der, eine, die
-->

# IDBTransaction in JavaScript: Eine umfassende Anleitung

## Synopsis
Der `IDBTransaction` ist ein zentraler Bestandteil der IndexedDB-API in JavaScript, der es ermöglicht, Datenbankoperationen in Transaktionen zu gruppieren und sicherzustellen, dass diese atomar ausgeführt werden.

## Dokumentation
### Zweck
`IDBTransaction` wird verwendet, um eine Gruppe von Operationen auf einer IndexedDB-Datenbank durchzuführen. Es stellt sicher, dass alle Operationen innerhalb der Transaktion entweder erfolgreich abgeschlossen werden oder bei einem Fehler vollständig zurückgerollt werden. Dies ist besonders wichtig für die Datensicherheit und Konsistenz.

### Verwendung
Um eine `IDBTransaction` zu erstellen, müssen Sie zunächst eine Verbindung zu einer IndexedDB-Datenbank herstellen und dann eine Transaktion über eine oder mehrere Objekte (Stores) initiieren. Hierbei müssen Sie den Modus der Transaktion angeben: `readonly` für nur Leseoperationen oder `readwrite` für Lese- und Schreiboperationen.

#### Syntax
```javascript
let transaction = db.transaction(storeNames, mode);
```

- **db**: Eine Instanz von `IDBDatabase`.
- **storeNames**: Ein oder mehrere Namen von Object Stores, auf die die Transaktion zugreifen soll.
- **mode**: Der Modus der Transaktion (`"readonly"` oder `"readwrite"`).

### Details
- Transaktionen sind nur für die Dauer ihrer Ausführung aktiv. Nach Abschluss oder bei einem Fehler wird die Transaktion automatisch geschlossen.
- Es können mehrere Transaktionen gleichzeitig bestehen, jedoch kann nur eine Transaktion eines bestimmten Object Stores zur gleichen Zeit aktiv sein.
- Die Transaktion bietet Methoden, um auf die Object Stores zuzugreifen, wie `objectStore()`.

## Beispiele
### Beispiel 1: Eine einfache `IDBTransaction` erstellen
```javascript
let request = indexedDB.open("MeineDatenbank", 1);

request.onsuccess = function(event) {
    let db = event.target.result;
    let transaction = db.transaction("MeineObjekte", "readwrite");
    
    let objectStore = transaction.objectStore("MeineObjekte");
    let addRequest = objectStore.add({ id: 1, name: "Beispiel" });

    addRequest.onsuccess = function() {
        console.log("Daten erfolgreich hinzugefügt!");
    };

    transaction.oncomplete = function() {
        console.log("Transaktion abgeschlossen.");
    };

    transaction.onerror = function(event) {
        console.log("Fehler in der Transaktion: ", event.target.error);
    };
};
```

### Beispiel 2: Mehrere Operationen in einer Transaktion
```javascript
let transaction = db.transaction(["Objekt1", "Objekt2"], "readwrite");

let store1 = transaction.objectStore("Objekt1");
let store2 = transaction.objectStore("Objekt2");

store1.add({ id: 1, value: "Wert1" });
store2.add({ id: 2, value: "Wert2" });

transaction.oncomplete = function() {
    console.log("Alle Operationen wurden erfolgreich abgeschlossen.");
};
```

## Erklärung
Ein häufiger Fehler bei der Verwendung von `IDBTransaction` ist das Missverständnis über die Lebensdauer der Transaktion. Es ist wichtig zu beachten, dass alle Operationen innerhalb der Transaktion synchronisiert und abgeschlossen sein müssen, bevor die Transaktion als abgeschlossen gilt. Ein weiterer Punkt ist, dass Transaktionen nicht überschneidend sind; dies bedeutet, dass Sie auf ein Object Store nicht gleichzeitig in mehreren Transaktionen zugreifen können. Planen Sie Ihre Datenoperationen entsprechend, um Konflikte zu vermeiden.

## Einzeiler Zusammenfassung
`IDBTransaction` ermöglicht atomare Datenbankoperationen in IndexedDB, indem es eine Gruppe von Lese- und Schreiboperationen in einer Transaktion zusammenfasst.