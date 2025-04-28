<!--
Meta Description: # Promises in JavaScript: Ein umfassender Leitfaden ## Synopsis Ein Promise in JavaScript ist ein Objekt, das einen asynchronen Vorgang repräsentiert ...
Meta Keywords: promise, promises, und, ein, javascript
-->

# Promises in JavaScript: Ein umfassender Leitfaden

## Synopsis
Ein Promise in JavaScript ist ein Objekt, das einen asynchronen Vorgang repräsentiert und einen Wert zurückgibt, der möglicherweise jetzt oder in der Zukunft verfügbar ist, oder nie. Es ermöglicht eine saubere Handhabung von asynchronem Code und ist ein fundamental wichtiges Konzept in modernen JavaScript-Anwendungen.

## Dokumentation
### Zweck
Promises bieten eine bessere Struktur für die Handhabung von asynchronem Code im Vergleich zu Callback-Funktionen. Sie helfen, "Callback-Hölle" zu vermeiden und ermöglichen eine klarere und wartbare Codebasis.

### Verwendung
Ein Promise kann in drei Zuständen sein:
- **Pending (Ausstehend)**: Der anfängliche Zustand, das Promise ist weder erfüllt noch abgelehnt.
- **Fulfilled (Erfüllt)**: Der Zustand, der angibt, dass das Promise erfolgreich abgeschlossen wurde und einen Wert zurückgibt.
- **Rejected (Abgelehnt)**: Der Zustand, der angibt, dass das Promise fehlgeschlagen ist und einen Fehler zurückgibt.

#### Erstellen eines Promises
Ein Promise wird mit dem `Promise`-Konstruktor erstellt, der eine Funktion als Argument akzeptiert. Diese Funktion hat zwei Parameter: `resolve` und `reject`.

```javascript
const myPromise = new Promise((resolve, reject) => {
    // Asynchrone Operation
    if (/* Erfolg */) {
        resolve("Erfolg!");
    } else {
        reject("Fehler!");
    }
});
```

#### Verbrauch eines Promises
Um den Wert eines Promises zu konsumieren, verwendet man die Methoden `.then()` und `.catch()`:

```javascript
myPromise
    .then((result) => {
        console.log(result); // Gibt "Erfolg!" aus
    })
    .catch((error) => {
        console.error(error); // Gibt "Fehler!" aus
    });
```

### Details
Promises unterstützen auch die Methode `.finally()`, die ausgeführt wird, nachdem das Promise erfüllt oder abgelehnt wurde, unabhängig vom Ergebnis:

```javascript
myPromise
    .finally(() => {
        console.log("Operation abgeschlossen.");
    });
```

### Chaining von Promises
Man kann mehrere Promises miteinander verketten, was die Handhabung komplexer asynchroner Abläufe erleichtert:

```javascript
myPromise
    .then((result) => {
        console.log(result);
        return anotherAsyncOperation();
    })
    .then((secondResult) => {
        console.log(secondResult);
    })
    .catch((error) => {
        console.error(error);
    });
```

## Beispiele
### Einfaches Beispiel eines Promises
```javascript
const delay = (ms) => {
    return new Promise((resolve) => {
        setTimeout(() => {
            resolve("Fertig nach " + ms + "ms");
        }, ms);
    });
};

delay(1000).then(console.log); // Gibt "Fertig nach 1000ms" nach 1 Sekunde aus
```

### Promise.all
`Promise.all` ermöglicht es, mehrere Promises gleichzeitig zu verarbeiten. Es erfüllt ein Promise, wenn alle enthaltenen Promises erfüllt sind.

```javascript
const promise1 = Promise.resolve(3);
const promise2 = 42;
const promise3 = new Promise((resolve) => setTimeout(resolve, 100, "Hallo"));

Promise.all([promise1, promise2, promise3]).then((values) => {
    console.log(values); // Gibt [3, 42, "Hallo"] aus
});
```

## Erklärung
### Häufige Fallen
- **Nicht behandelte Fehler**: Wenn ein Promise abgelehnt wird und kein `.catch()` vorhanden ist, wird der Fehler nicht behandelt.
- **Asynchrone Fehler**: Fehler innerhalb der `.then()`-Funktionen müssen ebenfalls behandelt werden, da sie sonst nicht korrekt gefangen werden.

### Zusätzliche Hinweise
- Promises sind nicht gleichbedeutend mit "async/await". Letzteres ist eine syntaktische Verbesserung zur Handhabung von Promises und macht den Code lesbarer.
- Promises können nicht erneut erfüllt oder abgelehnt werden, einmal abgeschlossen, bleiben sie im jeweiligen Zustand.

## Ein Satz Zusammenfassung
Ein Promise in JavaScript ist ein Objekt, das die zukünftige Fertigstellung oder den Misserfolg einer asynchronen Operation repräsentiert und es ermöglicht, asynchronen Code strukturiert und verständlich zu handhaben.