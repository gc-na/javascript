<!--
Meta Description: # queueMicrotask in JavaScript: Ein umfassender Leitfaden ## Synopsis `queueMicrotask` ist eine wichtige Funktion in JavaScript, die es ermöglicht, Au...
Meta Keywords: die, queuemicrotask, ist, microtask, der
-->

# queueMicrotask in JavaScript: Ein umfassender Leitfaden

## Synopsis
`queueMicrotask` ist eine wichtige Funktion in JavaScript, die es ermöglicht, Aufgaben im Microtask-Queue zu planen, um sie nach dem aktuellen Call Stack auszuführen. Dies trägt zur Verbesserung der Performance und zur Vermeidung von Blockierungen bei.

## Dokumentation
### Zweck
Die Funktion `queueMicrotask` wurde eingeführt, um Entwicklern die Möglichkeit zu geben, kleine Aufgaben (Microtasks) zu planen, die nach dem aktuellen JavaScript-Task, aber vor dem nächsten Rendering-Zyklus ausgeführt werden. Dies ist besonders nützlich, um sicherzustellen, dass wichtige Funktionen, wie Promise-Handler, in der richtigen Reihenfolge ausgeführt werden.

### Verwendung
Die Syntax von `queueMicrotask` ist einfach:

```javascript
queueMicrotask(callback);
```

- **callback**: Eine Funktion, die aufgerufen wird, wenn die aktuelle Ausführung des Scripts abgeschlossen ist.

### Details
- `queueMicrotask` ist eine Teilmenge des Task-Queues und wird nach der Ausführung des aktuellen Scripts, aber vor der nächsten Rendering-Phase ausgeführt.
- Es ist nützlich für asynchrone Programmierung, insbesondere in Kombination mit Promises.
- Microtasks haben eine höhere Priorität als Tasks, die in der Task-Queue (z. B. `setTimeout`) geplant werden.

## Beispiele
### Einfaches Beispiel

```javascript
console.log("Start");

queueMicrotask(() => {
    console.log("Microtask 1");
});

queueMicrotask(() => {
    console.log("Microtask 2");
});

console.log("Ende");
```
**Ausgabe:**
```
Start
Ende
Microtask 1
Microtask 2
```

### Verwendung mit Promises

```javascript
Promise.resolve().then(() => {
    console.log("Promise 1");
});

queueMicrotask(() => {
    console.log("Microtask 3");
});

Promise.resolve().then(() => {
    console.log("Promise 2");
});
```

**Ausgabe:**
```
Microtask 3
Promise 1
Promise 2
```

## Erklärung
Ein häufiges Missverständnis bei der Verwendung von `queueMicrotask` ist die Annahme, dass es die gleiche Funktionalität wie `setTimeout` hat. Im Gegensatz zu `setTimeout`, das eine Verzögerung im Task-Queue erzeugt, wird `queueMicrotask` sofort nach dem aktuellen Task ausgeführt, was zu einer schnelleren Reaktionszeit führt.

Ein weiterer Punkt ist, dass Microtasks nicht blockiert werden können. Wenn eine Microtask einen Fehler wirft, wird der gesamte Event Loop unterbrochen, was zu unerwartetem Verhalten führen kann.

## Zusammenfassung in einem Satz
`queueMicrotask` ist eine JavaScript-Funktion, die es ermöglicht, Microtasks zu planen, die sofort nach dem aktuellen Task ausgeführt werden, wodurch die Effizienz und die Reihenfolge der Aufrufe verbessert werden.