<!--
Meta Description: # IDBDatabase in JavaScript: Eine umfassende Anleitung ## Synopsis `IDBDatabase` ist eine Schnittstelle der IndexedDB-API in JavaScript, die es Entwic...
Meta Keywords: eine, const, die, idbdatabase, event
-->

# IDBDatabase in JavaScript: Eine umfassende Anleitung

## Synopsis
`IDBDatabase` ist eine Schnittstelle der IndexedDB-API in JavaScript, die es Entwicklern ermöglicht, Datenbanken im Browser zu erstellen, zu lesen, zu aktualisieren und zu löschen.

## Dokumentation

### Zweck
`IDBDatabase` repräsentiert eine Datenbank, die durch die IndexedDB-API verwaltet wird. Sie ermöglicht es Webanwendungen, strukturierte Daten lokal im Browser zu speichern, was eine effiziente Verwaltung großer Datenmengen ermöglicht.

### Verwendung
Um eine `IDBDatabase`-Instanz zu erstellen, muss der Entwickler eine Verbindung zu einer IndexedDB-Datenbank herstellen, indem er die `indexedDB.open()` Methode verwendet. Diese Methode akzeptiert den Namen der Datenbank und optional eine Versionsnummer. 

### Details
- **Methoden**: `IDBDatabase` bietet verschiedene Methoden zur Interaktion mit der Datenbank, darunter:
  - `transaction()`: Erzeugt eine Transaktion für Lese- oder Schreiboperationen.
  - `close()`: Schließt die Datenbankverbindung.
  - `deleteObjectStore()`: Löscht einen Objektspeicher.
  
- **Ereignisse**: `IDBDatabase` unterstützt verschiedene Ereignisse, wie `onversionchange`, das ausgelöst wird, wenn eine andere Verbindung die Datenbankversion ändert.

## Beispiele

### Grundlegende Verwendung
```javascript
const request = indexedDB.open("MeineDatenbank", 1);

request.onupgradeneeded = function(event) {
    const db = event.target.result;
    const objectStore = db.createObjectStore("MeineObjekte", { keyPath: "id" });
};

request.onsuccess = function(event) {
    const db = event.target.result;
    console.log("Datenbank erfolgreich geöffnet:", db.name);
};

request.onerror = function(event) {
    console.error("Fehler beim Öffnen der Datenbank:", event.target.error);
};
```

### Transaktionen nutzen
```javascript
const request = indexedDB.open("MeineDatenbank", 1);

request.onsuccess = function(event) {
    const db = event.target.result;
    const transaction = db.transaction("MeineObjekte", "readwrite");
    const objectStore = transaction.objectStore("MeineObjekte");
    
    const data = { id: 1, name: "Beispielobjekt" };
    const addRequest = objectStore.add(data);
    
    addRequest.onsuccess = function() {
        console.log("Daten erfolgreich hinzugefügt.");
    };
    
    transaction.oncomplete = function() {
        console.log("Transaktion erfolgreich abgeschlossen.");
    };
};
```

## Erklärung
Bei der Verwendung von `IDBDatabase` müssen Entwickler vorsichtig sein, um sicherzustellen, dass Transaktionen korrekt verwaltet werden. Ein häufiger Fehler ist das Vergessen, eine Transaktion zu schließen, was zu unerwarteten Ergebnissen führen kann. Außerdem sollte beachtet werden, dass die `onupgradeneeded`-Ereignisbehandlung für die Erstellung oder Aktualisierung von Objektspeichern zuständig ist, was bei jeder Änderung der Versionsnummer ausgeführt wird.

## Einzeilige Zusammenfassung
`IDBDatabase` ist eine zentrale API in JavaScript zur Verwaltung von IndexedDB-Datenbanken, die Entwicklern ermöglicht, strukturierte Daten effizient im Browser zu speichern.