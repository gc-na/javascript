<!--
Meta Description: # Int16Array in JavaScript: Eine umfassende Anleitung ## Synopsis `Int16Array` ist ein Typed Array in JavaScript, das eine Sammlung von 16-Bit vorzeic...
Meta Keywords: int16array, von, intarray, die, und
-->

# Int16Array in JavaScript: Eine umfassende Anleitung

## Synopsis
`Int16Array` ist ein Typed Array in JavaScript, das eine Sammlung von 16-Bit vorzeichenbehafteten Ganzzahlen speichert und ermöglicht effiziente numerische Berechnungen und Speicheroptimierungen.

## Dokumentation
`Int16Array` ist Teil der Typed Arrays, die es Entwicklern ermöglichen, auf binäre Daten direkt zuzugreifen. `Int16Array` speichert 16-Bit vorzeichenbehaftete Ganzzahlen und eignet sich besonders für Anwendungen, die mit großen Datenmengen arbeiten oder die Leistung optimieren müssen.

### Zweck
Der Hauptzweck von `Int16Array` besteht darin, eine effiziente Möglichkeit zu bieten, mit Ganzzahlen im Bereich von -32.768 bis 32.767 zu arbeiten. Diese Arrays sind nützlich in Bereichen wie Grafikprogrammierung, Audioverarbeitung und anderen Anwendungen, die mit binären Daten umgehen.

### Verwendung
`Int16Array` kann auf verschiedene Arten initialisiert werden:
- **Leeres Array**: `const arr = new Int16Array(10);` - Erstellt ein leeres `Int16Array` mit einer Länge von 10.
- **Array von Werten**: `const arr = new Int16Array([1, 2, 3]);` - Erstellt ein `Int16Array` mit den Werten 1, 2 und 3.
- **ArrayBuffer**: `const buffer = new ArrayBuffer(16); const arr = new Int16Array(buffer);` - Erstellt ein `Int16Array` aus einem vorhandenen `ArrayBuffer`.

### Eigenschaften
- **Länge**: `Int16Array.length` gibt die Anzahl der Elemente im Array zurück.
- **Byte-Länge**: `Int16Array.BYTES_PER_ELEMENT` gibt die Anzahl der Bytes zurück, die ein Element benötigt (in diesem Fall 2).

## Beispiele

### Beispiel 1: Initialisierung und Zugriff
```javascript
const intArray = new Int16Array([1000, 2000, -3000]);
console.log(intArray[0]); // Ausgabe: 1000
console.log(intArray[1]); // Ausgabe: 2000
```

### Beispiel 2: Bearbeitung von Werten
```javascript
const intArray = new Int16Array(5);
intArray[0] = 10;
intArray[1] = 20;
console.log(intArray); // Ausgabe: Int16Array(5) [10, 20, 0, 0, 0]
```

### Beispiel 3: Verwendung von ArrayBuffer
```javascript
const buffer = new ArrayBuffer(8);
const intArray = new Int16Array(buffer);
intArray[0] = 30000;
intArray[1] = -30000;
console.log(intArray); // Ausgabe: Int16Array(4) [30000, -30000]
```

## Erklärung
Ein häufiges Problem bei der Verwendung von `Int16Array` ist die Überlaufgefahr. Da `Int16Array` nur Werte im Bereich von -32.768 bis 32.767 speichern kann, werden Werte außerhalb dieses Bereichs zu unerwarteten Ergebnissen führen. Beispielsweise wird der Wert 40000 als -25536 gespeichert, da er über den maximalen Wert hinausgeht.

Ein weiterer Punkt ist, dass beim Arbeiten mit `Int16Array` und `ArrayBuffer` die Größe des Buffer korrekt dimensioniert werden muss, um sicherzustellen, dass genügend Speicher für alle benötigten Elemente vorhanden ist.

## Einzeilenzusammenfassung
`Int16Array` ermöglicht die Speicherung und Verarbeitung von 16-Bit vorzeichenbehafteten Ganzzahlen in JavaScript, was eine effiziente Handhabung von numerischen Daten gewährleistet.