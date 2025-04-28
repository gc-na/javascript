<!--
Meta Description: # AggregateError in JavaScript: Fehleraggregation leicht gemacht ## Synopsis `AggregateError` ist eine eingebaute Fehlerklasse in JavaScript, die es e...
Meta Keywords: aggregateerror, fehler, promise, ist, die
-->

# AggregateError in JavaScript: Fehleraggregation leicht gemacht

## Synopsis
`AggregateError` ist eine eingebaute Fehlerklasse in JavaScript, die es ermöglicht, mehrere Fehler in einem einzigen Fehlerobjekt zu aggregieren. Dies ist besonders nützlich bei der Arbeit mit Promises, wo mehrere asynchrone Operationen gleichzeitig durchgeführt werden.

## Dokumentation
`AggregateError` ist eine spezielle Fehlerklasse, die in ECMAScript 2021 (ES12) eingeführt wurde. Sie wird verwendet, um mehrere Fehler zu sammeln, die während der Ausführung von asynchronen Operationen aufgetreten sind. Diese Fehler können dann zusammen behandelt oder protokolliert werden, was die Fehlersuche und das Debugging erheblich erleichtert.

### Verwendung
Die Verwendung von `AggregateError` erfolgt normalerweise in Verbindung mit der Methode `Promise.any()`, die mehrere Promises akzeptiert und nur den ersten erfolgreichen Promise zurückgibt. Wenn alle Promises fehlschlagen, wird ein `AggregateError`-Objekt zurückgegeben, das alle aufgetretenen Fehler enthält.

#### Syntax
```javascript
new AggregateError(errors: Iterable<Error>, message?: string);
```

- **errors**: Ein iterierbares Objekt (z.B. ein Array) von Fehlerobjekten, die aggregiert werden sollen.
- **message**: (optional) Eine benutzerdefinierte Fehlermeldung.

### Eigenschaften
- `name`: Der Name des Fehlers, der standardmäßig auf "AggregateError" gesetzt ist.
- `errors`: Ein Array, das die einzelnen Fehlerobjekte enthält.

## Beispiele
### Beispiel 1: Grundlegende Verwendung
```javascript
const promise1 = Promise.reject(new Error("Fehler 1"));
const promise2 = Promise.reject(new Error("Fehler 2"));
const promise3 = Promise.resolve("Erfolg");

Promise.any([promise1, promise2, promise3])
    .then(result => {
        console.log(result); // "Erfolg"
    })
    .catch(err => {
        console.error(err instanceof AggregateError); // true
        console.error(err.errors); // [Error: Fehler 1, Error: Fehler 2]
    });
```

### Beispiel 2: Aggregation mehrerer Fehler
```javascript
const promises = [
    Promise.reject(new Error("Erster Fehler")),
    Promise.reject(new Error("Zweiter Fehler")),
];

Promise.any(promises)
    .catch(err => {
        console.log(err.name); // "AggregateError"
        console.log(err.errors.length); // 2
    });
```

## Erklärung
Ein häufiges Problem bei der Verwendung von `AggregateError` ist, dass Entwickler möglicherweise nicht verstehen, dass `AggregateError` nur dann auftritt, wenn alle Promises fehlschlagen. Wenn mindestens ein Promise erfolgreich ist, wird der Erfolg zurückgegeben und der `AggregateError` wird nicht ausgelöst. 

Ein weiterer Punkt ist, dass `AggregateError` nicht in älteren JavaScript-Umgebungen unterstützt wird. Es ist ratsam, Polyfills oder Transpiler wie Babel zu verwenden, um die Kompatibilität zu gewährleisten.

## Einzeiler Zusammenfassung
`AggregateError` in JavaScript aggregiert mehrere Fehler in einem einzigen Objekt, das bei der Verarbeitung von fehlerhaften Promises hilfreich ist.