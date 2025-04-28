<!--
Meta Description: # Atomics in JavaScript: Ein umfassender Leitfaden ## Synopsis Atomics ist ein globales Objekt in JavaScript, das eine API für die atomare Manipulatio...
Meta Keywords: atomics, einem, view, und, der
-->

# Atomics in JavaScript: Ein umfassender Leitfaden

## Synopsis
Atomics ist ein globales Objekt in JavaScript, das eine API für die atomare Manipulation von Shared Array Buffers bereitstellt und es ermöglicht, sicher mit gemeinsam genutztem Speicher in Multithreading-Umgebungen zu arbeiten.

## Dokumentation
### Zweck
Atomics ermöglicht die atomare Durchführung von Operationen auf Werten in einem Shared Array Buffer, was in Umgebungen mit mehreren Threads unerlässlich ist, um Datenrennen und Inkonsistenzen zu vermeiden.

### Verwendung
Die Atomics API ist Teil der Web-Worker-Umgebung und wird verwendet, um Operationen wie Lesen, Schreiben und Synchronisieren von Daten durchzuführen. Es wird hauptsächlich zusammen mit `SharedArrayBuffer` verwendet.

#### Methoden
- **Atomics.add()**: Addiert einen Wert zu einem Element in einem Shared Array.
- **Atomics.sub()**: Subtrahiert einen Wert von einem Element in einem Shared Array.
- **Atomics.and()**: Führt eine bitweise AND-Operation auf einem Element durch.
- **Atomics.or()**: Führt eine bitweise OR-Operation auf einem Element durch.
- **Atomics.xor()**: Führt eine bitweise XOR-Operation auf einem Element durch.
- **Atomics.exchange()**: Setzt einen neuen Wert in einem Element und gibt den alten Wert zurück.
- **Atomics.compareExchange()**: Vergleicht einen aktuellen Wert mit einem erwarteten und ersetzt ihn, wenn sie übereinstimmen.
- **Atomics.wait()**: Wartet auf eine Änderung an einem bestimmten Element in einem Shared Array.
- **Atomics.wake()**: Weckt einen oder mehrere wartende Threads.

### Details
Um Atomics zu verwenden, muss ein `SharedArrayBuffer` erstellt werden, der dann mit einem `TypedArray` verknüpft wird. Atomics-Operationen sind in der Regel schnell und ermöglichen die Synchronisation zwischen Web-Worker-Threads.

## Beispiele
### Beispiel 1: Atomics.add()
```javascript
const sab = new SharedArrayBuffer(4);
const view = new Int32Array(sab);
Atomics.add(view, 0, 1);
console.log(Atomics.load(view, 0)); // Ausgabe: 1
```

### Beispiel 2: Atomics.wait() und Atomics.wake()
```javascript
const sab = new SharedArrayBuffer(4);
const view = new Int32Array(sab);
const worker = new Worker('worker.js');

Atomics.wait(view, 0, 0); // Wartet, bis der Wert an Index 0 nicht mehr 0 ist
// In worker.js
// Atomics.store(view, 0, 1);
// Atomics.wake(view, 0);
```

### Beispiel 3: Atomics.compareExchange()
```javascript
const sab = new SharedArrayBuffer(4);
const view = new Int32Array(sab);
const oldValue = Atomics.compareExchange(view, 0, 0, 42);
console.log(oldValue); // Ausgabe: 0
console.log(Atomics.load(view, 0)); // Ausgabe: 42
```

## Erklärung
Ein häufiger Stolperstein bei der Verwendung von Atomics ist das Verständnis der Synchronisation zwischen Threads. Die Methoden `wait` und `wake` sind besonders wichtig, um Threads zu steuern. Bei der Verwendung von `compareExchange` sollte darauf geachtet werden, dass der erwartete Wert genau dem aktuellen Wert entspricht, um den Austausch erfolgreich durchzuführen.

## Ein Satz Zusammenfassung
Atomics in JavaScript ermöglicht atomare Operationen auf gemeinsam genutztem Speicher, um sichere Multithreading-Anwendungen zu erstellen.