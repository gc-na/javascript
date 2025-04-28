<!--
Meta Description: # Int32Array in JavaScript: Ein umfassender Leitfaden ## Synopsis `Int32Array` ist ein typed Array in JavaScript, das eine Liste von 32-Bit-Ganzzahlen...
Meta Keywords: int32array, array, javascript, ein, von
-->

# Int32Array in JavaScript: Ein umfassender Leitfaden

## Synopsis
`Int32Array` ist ein typed Array in JavaScript, das eine Liste von 32-Bit-Ganzzahlen speichert. Es ermöglicht effiziente Speicherung und Manipulation von binären Daten, insbesondere in Webanwendungen, die Leistung und Speicheroptimierung erfordern.

## Dokumentation
`Int32Array` ist Teil der JavaScript Typed Arrays und wird verwendet, um eine Array-ähnliche Ansicht auf eine Sequenz von 32-Bit-Ganzzahlen zu erstellen. Es ist besonders nützlich, wenn Sie mit binären Daten oder leistungsintensiven Berechnungen arbeiten.

### Zweck
`Int32Array` ermöglicht die Manipulation von 32-Bit-Ganzzahlen in einem Array-Format, das direkt mit den meisten Web-APIs interagiert, die binäre Daten verwenden.

### Verwendung
Sie können ein `Int32Array` auf verschiedene Arten erstellen:

1. **Leeres Int32Array**:
   ```javascript
   const array = new Int32Array(5); // Erstellt ein Int32Array mit einer Länge von 5
   ```

2. **Int32Array aus einem Array**:
   ```javascript
   const array = new Int32Array([1, 2, 3, 4, 5]); // Erstellt ein Int32Array aus einem normalen Array
   ```

3. **Int32Array aus einem ArrayBuffer**:
   ```javascript
   const buffer = new ArrayBuffer(16); // Erstellt einen ArrayBuffer mit 16 Bytes
   const intArray = new Int32Array(buffer); // Erstellt ein Int32Array, das diesen Buffer nutzt
   ```

### Methoden
- `set()`: Kopiert Werte in das Int32Array.
- `subarray()`: Gibt eine neue Ansicht auf einen Teil des Int32Array zurück.
- `fill()`: Füllt alle Elemente mit einem bestimmten Wert.

## Beispiele
### Beispiel 1: Erstellen eines Int32Array
```javascript
const myArray = new Int32Array(3);
myArray[0] = 10;
myArray[1] = 20;
myArray[2] = 30;
console.log(myArray); // Int32Array(3) [10, 20, 30]
```

### Beispiel 2: Verwendung von set()
```javascript
const array = new Int32Array(3);
array.set([1, 2, 3]);
console.log(array); // Int32Array(3) [1, 2, 3]
```

### Beispiel 3: Teilansicht mit subarray()
```javascript
const array = new Int32Array([1, 2, 3, 4, 5]);
const subArray = array.subarray(1, 4);
console.log(subArray); // Int32Array(3) [2, 3, 4]
```

## Erklärung
Ein häufiges Missverständnis bei der Verwendung von `Int32Array` ist, dass Sie erwarten, dass es wie ein normales JavaScript-Array funktioniert. Beachten Sie, dass `Int32Array` nur 32-Bit-Ganzzahlen speichert, und alle Werte außerhalb des Bereichs von -2.147.483.648 bis 2.147.483.647 werden nicht korrekt behandelt. Zudem können Sie keine nicht-integer Werte speichern; diese werden auf den nächsten Integer gerundet.

Ein weiteres wichtiges Detail ist, dass die Größe des `Int32Array` statisch ist, was bedeutet, dass Sie die Länge nach der Erstellung nicht mehr ändern können.

## Zusammenfassung in einem Satz
`Int32Array` ist ein leistungsstarkes Werkzeug in JavaScript für die effiziente Handhabung von 32-Bit-Ganzzahlen in binären Datenstrukturen.