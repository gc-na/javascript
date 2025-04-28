<!--
Meta Description: # IDBObjectStore: Ein umfassender Leitfaden zur Verwendung in JavaScript ## Synopsis IDBObjectStore ist eine zentrale Komponente der IndexedDB API in ...
Meta Keywords: const, objectstore, meineobjekte, transaction, die
-->

# IDBObjectStore: Ein umfassender Leitfaden zur Verwendung in JavaScript

## Synopsis
IDBObjectStore ist eine zentrale Komponente der IndexedDB API in JavaScript, die es Entwicklern ermöglicht, strukturierte Daten in einem Client-seitigen Speicher zu speichern, abzurufen und zu verwalten.

## Dokumentation
### Zweck
IDBObjectStore ist ein Speicherort innerhalb einer IndexedDB-Datenbank, der es ermöglicht, Objekte zu speichern, die durch Schlüssel identifiziert werden. Es ermöglicht das Speichern von Daten in Form von JavaScript-Objekten und deren effizientem Abrufen.

### Verwendung
Um IDBObjectStore zu verwenden, müssen Sie zunächst eine IndexedDB-Datenbank erstellen oder öffnen. Danach können Sie ein ObjectStore anlegen, in dem Sie Objekte speichern. Hier sind die Schritte zur Verwendung:

1. **Datenbank öffnen oder erstellen**:
   ```javascript
   const request = indexedDB.open("meineDatenbank", 1);
   request.onupgradeneeded = function(event) {
       const db = event.target.result;
       const objectStore = db.createObjectStore("meineObjekte", { keyPath: "id" });
   };
   ```

2. **Daten hinzufügen**:
   ```javascript
   request.onsuccess = function(event) {
       const db = event.target.result;
       const transaction = db.transaction("meineObjekte", "readwrite");
       const objectStore = transaction.objectStore("meineObjekte");
       
       const meinObjekt = { id: 1, name: "Beispiel" };
       const addRequest = objectStore.add(meinObjekt);

       addRequest.onsuccess = function() {
           console.log("Objekt erfolgreich hinzugefügt");
       };
   };
   ```

3. **Daten abrufen**:
   ```javascript
   const transaction = db.transaction("meineObjekte", "readonly");
   const objectStore = transaction.objectStore("meineObjekte");
   const getRequest = objectStore.get(1);
   
   getRequest.onsuccess = function() {
       console.log("Abgerufenes Objekt:", getRequest.result);
   };
   ```

### Details
- **Methoden**: IDBObjectStore bietet verschiedene Methoden wie `.add()`, `.put()`, `.delete()`, `.get()`, und `.getAll()`, um die Interaktion mit den gespeicherten Objekten zu ermöglichen.
- **Transaktionen**: Alle Aktionen auf einem ObjectStore müssen innerhalb einer Transaktion ausgeführt werden, die die Konsistenz der Daten gewährleistet.
- **Indexierung**: Sie können Indizes auf einem ObjectStore erstellen, um die Suche und den Zugriff auf Daten zu optimieren.

## Beispiele
### Einfaches Objekt speichern und abrufen
```javascript
// Datenbank und ObjectStore erstellen
const request = indexedDB.open("meineDatenbank", 1);
request.onupgradeneeded = function(event) {
    const db = event.target.result;
    db.createObjectStore("meineObjekte", { keyPath: "id" });
};

// Daten hinzufügen
request.onsuccess = function(event) {
    const db = event.target.result;
    const transaction = db.transaction("meineObjekte", "readwrite");
    const objectStore = transaction.objectStore("meineObjekte");
    
    objectStore.add({ id: 1, name: "Beispiel" });
};

// Daten abrufen
const getTransaction = db.transaction("meineObjekte", "readonly");
const getObjectStore = getTransaction.objectStore("meineObjekte");
const getRequest = getObjectStore.get(1);
getRequest.onsuccess = function() {
    console.log(getRequest.result);  // { id: 1, name: "Beispiel" }
};
```

## Erklärung
### Häufige Stolpersteine
- **Transaktionsreichweite**: Stellen Sie sicher, dass alle Operationen innerhalb einer Transaktion durchgeführt werden, da dies die Konsistenz gewährleistet.
- **Objekte mit Schlüsselpfad**: Wenn Sie Objekte ohne den definierten Schlüsselpfad hinzufügen, kann es zu Fehlern kommen.
- **Browser-Kompatibilität**: Überprüfen Sie die Kompatibilität des Browsers mit der IndexedDB API, da nicht alle mobilen und älteren Browser diese unterstützen.

## Ein Satz Zusammenfassung
IDBObjectStore ermöglicht das Speichern und Abrufen strukturierter Daten in einer IndexedDB-Datenbank in JavaScript.