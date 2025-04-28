<!--
Meta Description: # Uint8Array in JavaScript: Ein umfassender Leitfaden ## Synopsis `Uint8Array` ist eine Typed Array-Klasse in JavaScript, die es ermöglicht, eine Samm...
Meta Keywords: uint8array, array, und, javascript, die
-->

# Uint8Array in JavaScript: Ein umfassender Leitfaden

## Synopsis
`Uint8Array` ist eine Typed Array-Klasse in JavaScript, die es ermöglicht, eine Sammlung von 8-Bit-unsigned Ganzzahlen effizient zu speichern und zu manipulieren. Diese Datenstruktur wird häufig in der Webentwicklung für die Verarbeitung von Binärdaten verwendet, z. B. in WebSockets, WebRTC und beim Arbeiten mit Blob-Daten.

## Dokumentation

### Zweck
`Uint8Array` ist Teil der `TypedArray`-Familie in JavaScript, die speziell für die Arbeit mit binären Daten optimiert sind. Sie bieten eine Möglichkeit, eine feste Anzahl von Elementen in einem Array zu speichern, wobei jedes Element einen Wert zwischen 0 und 255 annehmen kann. 

### Verwendung
Um ein `Uint8Array` zu erstellen, können Sie den Konstruktor auf verschiedene Arten verwenden:

1. **Leeres Array**: 
   ```javascript
   const array = new Uint8Array(10); // Ein Array mit 10 Elementen, initialisiert mit 0
   ```

2. **Array von Werten**:
   ```javascript
   const array = new Uint8Array([1, 2, 3, 255]); // Ein Array mit den Werten 1, 2, 3 und 255
   ```

3. **ArrayBuffer**:
   ```javascript
   const buffer = new ArrayBuffer(4); // Erstellen eines ArrayBuffers mit 4 Bytes
   const array = new Uint8Array(buffer); // Erstellen eines Uint8Array aus dem Buffer
   ```

### Details
- `Uint8Array` hat eine feste Länge, die zur Erstellungszeit festgelegt wird.
- Die Werte sind 8-Bit unsigned Integers, was bedeutet, dass sie nur positive Werte zwischen 0 und 255 annehmen können.
- Die Methoden, die für `Uint8Array` verfügbar sind, umfassen unter anderem `set()`, `subarray()`, `slice()`, und viele Array-Methoden wie `forEach()`, `map()`, und `filter()`.

## Beispiele

### Beispiel 1: Grundlegende Array-Initialisierung
```javascript
const myArray = new Uint8Array(5);
console.log(myArray); // Uint8Array(5) [0, 0, 0, 0, 0]
```

### Beispiel 2: Mit Werten initialisieren
```javascript
const myArray = new Uint8Array([10, 20, 30]);
console.log(myArray); // Uint8Array(3) [10, 20, 30]
```

### Beispiel 3: Werte setzen und lesen
```javascript
const myArray = new Uint8Array(3);
myArray.set([100, 200, 255]);
console.log(myArray[1]); // 200
```

## Erklärung
Ein häufiges Missverständnis bei der Verwendung von `Uint8Array` ist die Annahme, dass es negatives Zahlen speichern kann. Da es sich um ein "unsigned" Array handelt, können nur Werte zwischen 0 und 255 gespeichert werden. Wenn Sie versuchen, einen Wert außerhalb dieses Bereichs zu setzen, wird der Wert modulo 256 genommen. Zum Beispiel wird der Wert 256 zu 0, und der Wert 300 wird zu 44.

Darüber hinaus ist es wichtig, sich bewusst zu sein, dass `Uint8Array` eine flache Struktur hat, was bedeutet, dass Sie keine mehrdimensionalen Arrays direkt speichern können. Für mehrdimensionale Datenstrukturen müssen Sie mehrere `Uint8Array`-Instanzen verwenden.

## Ein-Satz-Zusammenfassung
`Uint8Array` ist eine leistungsfähige Typisierte Array-Klasse in JavaScript, die effiziente Manipulation und Speicherung von 8-Bit-unsigned Ganzzahlen ermöglicht.