<!--
Meta Description: # StorageManager in JavaScript: Verwaltung des Speichers im Web ## Synopsis Der `StorageManager` ist eine JavaScript-Schnittstelle, die Entwicklern er...
Meta Keywords: die, der, ist, storagemanager, des
-->

# StorageManager in JavaScript: Verwaltung des Speichers im Web

## Synopsis
Der `StorageManager` ist eine JavaScript-Schnittstelle, die Entwicklern ermöglicht, den Speicherstatus und die Speicherkapazität von Webanwendungen zu überwachen und zu steuern. Damit können Anwendungen effizienter mit lokalem Speicher umgehen, insbesondere in Bezug auf die Persistenz von Daten.

## Dokumentation
Der `StorageManager` ist Teil der Web Storage API und bietet Methoden zur Verwaltung des Speichers. Er ermöglicht es Entwicklern, Informationen über den verfügbaren Speicherplatz sowie die Möglichkeit, den Speicherstatus zu ändern, zu erhalten. Die wichtigsten Methoden sind:

- **`StorageManager.estimate()`**: Diese Methode gibt eine Schätzung des verfügbaren Speichers und des insgesamt genutzten Speichers zurück. Sie hilft Entwicklern zu verstehen, wie viel Speicherplatz für ihre Anwendung noch verfügbar ist.

- **`StorageManager.persist()`**: Mit dieser Methode können Anwendungen den Antrag stellen, persistente Speicherung zu verwenden, was bedeutet, dass die Daten auch nach dem Schließen des Browsers erhalten bleiben. Dies ist besonders wichtig für Anwendungen, die auf Datenanhalten angewiesen sind.

- **`StorageManager.persisted()`**: Diese Methode gibt zurück, ob der Speicher für die Anwendung persistent ist oder nicht. Dies ist nützlich, um zu entscheiden, wie mit temporären Daten umgegangen werden soll.

### Verwendung
Um auf den `StorageManager` zuzugreifen, verwenden Sie den globalen `navigator`-Objekt:

```javascript
if ('storage' in navigator) {
    const storageManager = navigator.storage;
}
```

## Beispiele
### Beispiel für die Schätzung des Speichers

```javascript
async function checkStorageEstimate() {
    const estimate = await navigator.storage.estimate();
    console.log(`Verfügbarer Speicher: ${estimate.quota}`);
    console.log(`Genutzter Speicher: ${estimate.usage}`);
}

checkStorageEstimate();
```

### Beispiel für persistente Speicherung

```javascript
async function requestPersistentStorage() {
    const persisted = await navigator.storage.persist();
    if (persisted) {
        console.log("Die Daten werden dauerhaft gespeichert.");
    } else {
        console.log("Die Daten sind nicht persistent.");
    }
}

requestPersistentStorage();
```

### Beispiel zur Überprüfung, ob der Speicher persistent ist

```javascript
async function checkIfPersistent() {
    const persisted = await navigator.storage.persisted();
    console.log(persisted ? "Der Speicher ist persistent." : "Der Speicher ist nicht persistent.");
}

checkIfPersistent();
```

## Erklärung
Ein häufiger Stolperstein bei der Verwendung des `StorageManager` kann sein, dass nicht alle Browser die persistente Speicherung unterstützen. Es ist wichtig, vor der Verwendung der Methoden eine Überprüfung auf die Verfügbarkeit des `StorageManager` durchzuführen. Auch sollte bedacht werden, dass Benutzer in ihren Browsereinstellungen die Speicherung von Daten einschränken können, was die Funktionsweise der Anwendung beeinflussen könnte.

Ein weiterer wichtiger Punkt ist, dass die Nutzung von Speicherplatz durch die Anwendung nicht unbegrenzt ist. Die Schätzung des Speichers kann variieren, und es kann zu Speicherüberläufen kommen, wenn die Grenzen überschritten werden.

## Zusammenfassung in einem Satz
Der `StorageManager` ermöglicht es JavaScript-Anwendungen, den Speicherstatus zu überwachen und die Speicherkapazität effizient zu verwalten, indem er Methoden zur Schätzung und Beantragung persistenter Speicherung bereitstellt.