<!--
Meta Description: # IDBIndex in JavaScript: Indizes in IndexedDB ## Synopsis IDBIndex ist ein wichtiges Interface in IndexedDB, das es Entwicklern ermöglicht, Indizes a...
Meta Keywords: index, der, die, idbindex, ist
-->

# IDBIndex in JavaScript: Indizes in IndexedDB

## Synopsis
IDBIndex ist ein wichtiges Interface in IndexedDB, das es Entwicklern ermöglicht, Indizes auf Datenbanken zu erstellen, um die Suche nach bestimmten Daten zu optimieren.

## Dokumentation
Das `IDBIndex`-Objekt ist Teil der IndexedDB API, die es Webanwendungen ermöglicht, große Mengen strukturierter Daten zu speichern. Mit `IDBIndex` können Entwickler Indizes auf Objektspeicher erstellen, um die Effizienz von Abfragen zu steigern.

### Zweck
Der Hauptzweck von IDBIndex ist die Verbesserung der Abfragegeschwindigkeit, indem schnelle Zugriffe auf Daten durch vorgefertigte Indizes ermöglicht werden. Anstatt alle Daten zu durchsuchen, können Entwickler gezielt auf indizierte Felder zugreifen.

### Verwendung
Um einen IDBIndex zu nutzen, müssen Sie zunächst einen Objektspeicher in einer IndexedDB-Datenbank erstellen. Anschließend können Sie einen Index über die Methode `createIndex()` des `IDBObjectStore`-Objekts anlegen.

#### Syntax
```javascript
let index = objectStore.createIndex(name, keyPath, optionalParameters);
```

- `name`: Der Name des Index.
- `keyPath`: Der Pfad zu den zu indizierenden Werten.
- `optionalParameters`: Ein optionales Objekt, das zusätzliche Einstellungen wie `unique` oder `multiEntry` enthält.

### Eigenschaften und Methoden
- **Eigenschaften**:
  - `name`: Der Name des Index.
  - `keyPath`: Der Pfad, auf den der Index zeigt.
  - `multiEntry`: Gibt an, ob der Index mehrere Werte pro Eintrag unterstützen kann.
  - `unique`: Gibt an, ob der Index eindeutige Werte erfordert.

- **Methoden**:
  - `get(key)`: Ruft den Wert für den angegebenen Schlüssel ab.
  - `getAll()`: Gibt alle Werte im Index zurück.
  - `count()`: Zählt die Anzahl der Einträge im Index.

## Beispiele
### Beispiel 1: Erstellen eines Index
```javascript
const request = indexedDB.open("MeineDatenbank", 1);

request.onupgradeneeded = function(event) {
    const db = event.target.result;
    const objectStore = db.createObjectStore("Benutzer", { keyPath: "id" });
    objectStore.createIndex("nachname", "nachname", { unique: false });
};
```

### Beispiel 2: Abfragen eines Index
```javascript
const transaction = db.transaction("Benutzer", "readonly");
const objectStore = transaction.objectStore("Benutzer");
const index = objectStore.index("nachname");

const request = index.get("Müller");

request.onsuccess = function(event) {
    console.log(event.target.result);
};
```

## Erklärung
Eine häufige Falle beim Arbeiten mit `IDBIndex` ist das Missverständnis bezüglich der `keyPath`. Wenn die `keyPath` nicht korrekt definiert ist oder die Datenstruktur nicht den Erwartungen entspricht, wird der Index möglicherweise nicht wie erwartet funktionieren. Ein weiteres häufiges Problem ist die Verwendung von `unique`-Indizes. Wenn Sie versuchen, doppelte Werte in einem einzigartigen Index zu speichern, wird ein Fehler ausgelöst.

## Einzeilige Zusammenfassung
IDBIndex ist ein Interface in IndexedDB, das es Entwicklern ermöglicht, Indizes zu erstellen, um die Suche nach Daten effizienter zu gestalten.