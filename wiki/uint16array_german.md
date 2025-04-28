<!--
Meta Description: # Uint16Array in JavaScript: Eine umfassende Anleitung ## Zusammenfassung `Uint16Array` ist eine Typed Array-Klasse in JavaScript, die eine Sammlung v...
Meta Keywords: uint16array, die, von, javascript, myarray
-->

# Uint16Array in JavaScript: Eine umfassende Anleitung

## Zusammenfassung
`Uint16Array` ist eine Typed Array-Klasse in JavaScript, die eine Sammlung von 16-Bit-ungezeichneten Ganzzahlen speichert und eine effiziente Möglichkeit bietet, mit binären Daten zu arbeiten.

## Dokumentation
`Uint16Array` ist Teil der ECMAScript-Spezifikation und ermöglicht die Erstellung von Arrays, die ausschließlich 16-Bit-ungezeichnete Ganzzahlen speichern. Diese Datenstruktur eignet sich hervorragend für die Verarbeitung von binären Daten, insbesondere in Anwendungen wie Grafikprogrammierung, WebGL und Audioverarbeitung.

### Zweck
Der Hauptzweck von `Uint16Array` ist die Speicherung und Manipulation von Ganzzahlen im Bereich von 0 bis 65535 (2^16 - 1). Dies ist besonders nützlich in Szenarien, in denen die Speichereffizienz und die Geschwindigkeit eine Rolle spielen.

### Verwendung
Um ein `Uint16Array` zu erstellen, können Sie einen ArrayBuffer oder eine Länge als Argument übergeben. Die Syntax lautet:

```javascript
let array = new Uint16Array(length);
let arrayFromBuffer = new Uint16Array(buffer, byteOffset, length);
```

- **length**: Die Anzahl der 16-Bit-Werte im Array.
- **buffer**: Ein ArrayBuffer, von dem das `Uint16Array` abgeleitet wird.
- **byteOffset**: Der Offset in Bytes im ArrayBuffer, wo die Daten beginnen.

## Beispiele
### Beispiel 1: Erstellen eines `Uint16Array`
```javascript
let myArray = new Uint16Array(5); // Erstellt ein Uint16Array mit 5 Elementen
console.log(myArray); // Ausgabe: Uint16Array(5) [0, 0, 0, 0, 0]
```

### Beispiel 2: Initialisieren mit Werten
```javascript
let initializedArray = new Uint16Array([10, 20, 30, 40, 50]);
console.log(initializedArray); // Ausgabe: Uint16Array(5) [10, 20, 30, 40, 50]
```

### Beispiel 3: Zugriff auf Werte
```javascript
let myArray = new Uint16Array([100, 200, 300]);
console.log(myArray[1]); // Ausgabe: 200
```

### Beispiel 4: Manipulation von Werten
```javascript
let myArray = new Uint16Array(3);
myArray[0] = 500;
myArray[1] = 1000;
myArray[2] = 1500;
console.log(myArray); // Ausgabe: Uint16Array(3) [500, 1000, 1500]
```

## Erklärung
Ein häufiges Problem bei der Verwendung von `Uint16Array` ist das Verständnis des Unterschieds zwischen Typed Arrays und regulären JavaScript-Arrays. Typed Arrays haben eine feste Länge und sind in ihrer Typisierung strikt, was bedeutet, dass sie nur 16-Bit-ungezeichnete Ganzzahlen speichern können. Wenn Sie versuchen, einen Wert außerhalb des gültigen Bereichs (0 bis 65535) zu speichern, wird er automatisch auf 0 zurückgesetzt.

Ein weiteres häufiges Missverständnis betrifft die Byte-Offsets. Wenn Sie einen `Uint16Array` aus einem `ArrayBuffer` erstellen, müssen Sie sicherstellen, dass der `byteOffset` auf das richtige Byte zeigt, da dies die Datenintegrität beeinflussen kann.

## Kurze Zusammenfassung
`Uint16Array` ist ein leistungsstarkes Tool in JavaScript zur Speicherung und Manipulation von 16-Bit-ungezeichneten Ganzzahlen, das besonders in der Verarbeitung von binären Daten nützlich ist.