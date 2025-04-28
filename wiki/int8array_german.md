<!--
Meta Description: # Int8Array in JavaScript: Eine umfassende Anleitung ## Synopsis Int8Array ist ein Typed Array in JavaScript, das eine Sammlung von 8-Bit ganzzahligen...
Meta Keywords: int8array, ein, die, javascript, const
-->

# Int8Array in JavaScript: Eine umfassende Anleitung

## Synopsis
Int8Array ist ein Typed Array in JavaScript, das eine Sammlung von 8-Bit ganzzahligen Werten speichert. Es ermöglicht die effiziente Handhabung von binären Daten, ideal für Anwendungen, die niedrigere Speicheranforderungen und schnelle Verarbeitung benötigen.

## Dokumentation
Int8Array ist eine Klasse, die Teil der ECMAScript 2015 (ES6) Spezifikation ist. Sie ermöglicht das Erstellen und Verwalten von Arrays, die 8-Bit signierte Ganzzahlen (von -128 bis 127) speichern. Dies ist besonders nützlich für Anwendungen, die mit binären Daten arbeiten, wie z.B. Bildverarbeitung oder Netzwerkprotokolle.

### Verwendung
Um ein Int8Array zu erstellen, können Sie einen ArrayBuffer oder eine Länge übergeben. Hier sind einige Möglichkeiten, wie Sie Int8Array verwenden können:

1. **Erstellen eines Int8Array mit einer bestimmten Länge:**
   ```javascript
   const arr = new Int8Array(5); // Erstellt ein Int8Array mit 5 Elementen
   ```

2. **Erstellen eines Int8Array aus einem Array:**
   ```javascript
   const arrFromArray = new Int8Array([10, 20, 30]); // Erstellt ein Int8Array mit den Werten 10, 20 und 30
   ```

3. **Erstellen eines Int8Array aus einem ArrayBuffer:**
   ```javascript
   const buffer = new ArrayBuffer(8);
   const int8 = new Int8Array(buffer); // Erstellt ein Int8Array, das den ArrayBuffer nutzt
   ```

### Eigenschaften und Methoden
- **length**: Gibt die Anzahl der Elemente im Int8Array zurück.
- **set(array)**: Setzt die Werte des Int8Arrays auf die Werte eines anderen Arrays.
- **subarray(start, end)**: Gibt ein neues Int8Array zurück, das einen Teil des aktuellen Arrays darstellt.

## Beispiele
### Beispiel 1: Grundlegende Erstellung
```javascript
const int8Array = new Int8Array(3);
int8Array[0] = 127;
int8Array[1] = -128;
int8Array[2] = 0;

console.log(int8Array); // Ausgabe: Int8Array(3) [127, -128, 0]
```

### Beispiel 2: Verwendung der `set` Methode
```javascript
const int8Array = new Int8Array(3);
int8Array.set([10, 20, 30]);

console.log(int8Array); // Ausgabe: Int8Array(3) [10, 20, 30]
```

### Beispiel 3: Erstellen eines Subarrays
```javascript
const int8Array = new Int8Array([1, 2, 3, 4, 5]);
const subArray = int8Array.subarray(1, 4);

console.log(subArray); // Ausgabe: Int8Array(3) [2, 3, 4]
```

## Erklärung
Ein häufiges Missverständnis bei der Verwendung von Int8Array ist, dass es nur mit Werten zwischen -128 und 127 funktioniert. Werte außerhalb dieses Bereichs werden automatisch umgewandelt, was zu unerwarteten Ergebnissen führen kann. Zum Beispiel wird der Wert 128 auf -128 umgewandelt. 

Ein weiterer Punkt ist, dass Typed Arrays nicht die gleichen Methoden wie reguläre Arrays haben, wie z.B. `push` oder `pop`. Stattdessen sollte man die `set`-Methode verwenden, um Werte hinzuzufügen oder zu ändern.

## Ein-Satz-Zusammenfassung
Int8Array in JavaScript ist ein leistungsfähiges Werkzeug zum Speichern und Verarbeiten von 8-Bit signierten Ganzzahlen in einer effizienten Datenstruktur.