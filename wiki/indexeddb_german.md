<!--
Meta Description: # IndexedDB in JavaScript: Eine umfassende Anleitung zur Nutzung von Client-seitiger Datenbanktechnologie ## Synopsis IndexedDB ist eine leistungsstar...
Meta Keywords: const, die, transaction, indexeddb, daten
-->

# IndexedDB in JavaScript: Eine umfassende Anleitung zur Nutzung von Client-seitiger Datenbanktechnologie

## Synopsis
IndexedDB ist eine leistungsstarke API, die es Webentwicklern ermöglicht, strukturierte Daten im Browser zu speichern und abzurufen. Sie bietet eine transaktionale Datenbank, die ideal für die Offline-Nutzung und die Speicherung umfangreicher Datenmengen geeignet ist.

## Dokumentation
### Zweck
IndexedDB ist eine client-seitige Datenbanktechnologie, die es ermöglicht, große Mengen an strukturierten Daten zu speichern. Sie ist besonders nützlich für Webanwendungen, die offline funktionieren müssen oder große Datenmengen verwalten, wie z. B. Spiele oder Datenvisualisierungen.

### Verwendung
Um IndexedDB zu nutzen, müssen Entwickler zunächst eine Datenbank erstellen oder öffnen. Anschließend können sie Objektspeicher (äquivalent zu Tabellen in relationalen Datenbanken) anlegen, Daten speichern, abfragen und löschen. Die API ist asynchron, was bedeutet, dass sie die Benutzeroberfläche nicht blockiert.

### Grundlegende Schritte
1. **Datenbank erstellen oder öffnen**
   ```javascript
   const request = indexedDB.open("MeineDatenbank", 1);
   ```

2. **Datenbankstruktur definieren**
   ```javascript
   request.onupgradeneeded = (event) => {
       const db = event.target.result;
       const objectStore = db.createObjectStore("MeineObjekte", { keyPath: "id" });
   };
   ```

3. **Daten hinzufügen**
   ```javascript
   request.onsuccess = (event) => {
       const db = event.target.result;
       const transaction = db.transaction("MeineObjekte", "readwrite");
       const objectStore = transaction.objectStore("MeineObjekte");
       objectStore.add({ id: 1, name: "Beispiel" });
   };
   ```

4. **Daten abfragen**
   ```javascript
   const transaction = db.transaction("MeineObjekte", "readonly");
   const objectStore = transaction.objectStore("MeineObjekte");
   const getRequest = objectStore.get(1);
   
   getRequest.onsuccess = (event) => {
       console.log(event.target.result);
   };
   ```

5. **Daten löschen**
   ```javascript
   const deleteRequest = objectStore.delete(1);
   deleteRequest.onsuccess = () => {
       console.log("Daten gelöscht");
   };
   ```

## Beispiele
### Beispiel 1: Grundlegende IndexedDB-Nutzung
```javascript
const request = indexedDB.open("TestDB", 1);

request.onupgradeneeded = (event) => {
    const db = event.target.result;
    db.createObjectStore("TestStore", { keyPath: "id" });
};

request.onsuccess = (event) => {
    const db = event.target.result;
    const transaction = db.transaction("TestStore", "readwrite");
    const store = transaction.objectStore("TestStore");
    store.add({ id: 1, name: "Test" });
};
```

### Beispiel 2: Daten abfragen und anzeigen
```javascript
const transaction = db.transaction("TestStore", "readonly");
const store = transaction.objectStore("TestStore");
const getRequest = store.get(1);

getRequest.onsuccess = () => {
    if (getRequest.result) {
        console.log("Name:", getRequest.result.name);
    } else {
        console.log("Kein Datensatz gefunden.");
    }
};
```

## Erklärung
### Häufige Stolpersteine
- **Asynchrone Natur:** Die meisten Operationen in IndexedDB sind asynchron. Es ist wichtig, die Callback-Funktionen korrekt zu verwalten, um sicherzustellen, dass die Datenbankoperationen abgeschlossen sind, bevor auf die Daten zugegriffen wird.
- **Versionierung:** Wenn Sie die Struktur der Datenbank ändern (z. B. neue Objektstores hinzufügen), müssen Sie die Version der Datenbank erhöhen, um den `onupgradeneeded`-Ereignislistener auszulösen.
- **Browser-Kompatibilität:** Nicht alle Browser unterstützen IndexedDB gleich gut. Stellen Sie sicher, dass Sie die Kompatibilität prüfen, bevor Sie die API in Ihrer Anwendung verwenden.

## Ein-Satz-Zusammenfassung
IndexedDB ist eine leistungsstarke JavaScript-API zur Speicherung und Verwaltung strukturierter Daten im Browser, die Offline-Funktionalität und eine hohe Speicherkapazität bietet.