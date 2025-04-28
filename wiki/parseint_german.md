<!--
Meta Description: # parseInt in JavaScript: Eine umfassende Anleitung ## Synopsis Die `parseInt`-Funktion in JavaScript ist ein leistungsfähiges Werkzeug zum Konvertier...
Meta Keywords: die, parseint, eine, wird, zeichenfolge
-->

# parseInt in JavaScript: Eine umfassende Anleitung

## Synopsis
Die `parseInt`-Funktion in JavaScript ist ein leistungsfähiges Werkzeug zum Konvertieren von Zeichenfolgen in Ganzzahlen. Sie spielt eine wichtige Rolle bei der Verarbeitung von Benutzereingaben und der Sicherstellung, dass numerische Werte korrekt interpretiert werden.

## Dokumentation
Die `parseInt`-Funktion wird verwendet, um eine Zeichenfolge in eine Ganzzahl zu konvertieren. Sie hat die folgende Syntax:

```javascript
parseInt(string, radix);
```

### Parameter
- **string**: Die Zeichenfolge, die in eine Ganzzahl umgewandelt werden soll. Wenn der Parameter `string` nicht angegeben ist oder nicht konvertierbar ist, gibt `parseInt` `NaN` zurück.
- **radix**: (optional) Eine Ganzzahl zwischen 2 und 36, die die Basis der Zahl angibt. Wenn dieser Parameter weggelassen wird, wird die Basis je nach Format der Zeichenfolge bestimmt:
  - Wenn die Zeichenfolge mit "0x" oder "0X" beginnt, wird die Basis auf 16 (hexadezimal) gesetzt.
  - Wenn die Zeichenfolge mit "0" beginnt, wird die Basis auf 8 (oktal) oder 10 (dezimal) gesetzt (dies hängt von der Implementierung ab).
  - Andernfalls wird die Basis auf 10 (dezimal) gesetzt.

### Rückgabewert
`parseInt` gibt die konvertierte Ganzzahl zurück oder `NaN`, wenn die Zeichenfolge nicht in eine Zahl umgewandelt werden kann.

## Beispiele
Hier sind einige grundlegende Beispiele zur Verwendung von `parseInt`:

```javascript
console.log(parseInt("42"));          // Ausgabe: 42
console.log(parseInt("1010", 2));     // Ausgabe: 10 (binär)
console.log(parseInt("0xF", 16));     // Ausgabe: 15 (hexadezimal)
console.log(parseInt("   20abc "));   // Ausgabe: 20 (Whitespace wird ignoriert)
console.log(parseInt("abc20"));       // Ausgabe: NaN (kann nicht konvertiert werden)
console.log(parseInt("12.34"));       // Ausgabe: 12 (nur der Ganzzahlteil wird berücksichtigt)
```

## Erklärung
Ein häufiges Missverständnis bei `parseInt` ist die Handhabung von nicht-numerischen Zeichen. Wenn die Zeichenfolge mit einer Zahl beginnt, wird diese Zahl bis zum ersten nicht-numerischen Zeichen gelesen. Beispielsweise gibt `parseInt("123abc")` den Wert `123` zurück. Wenn die Zeichenfolge jedoch mit einem nicht-numerischen Zeichen beginnt, wird `parseInt` `NaN` zurückgeben.

Ein weiteres häufiges Problem ist die Verwendung des `radix`-Parameters. Es ist eine bewährte Praxis, immer einen `radix`-Wert anzugeben, um unerwartete Ergebnisse zu vermeiden, insbesondere bei Zahlen, die mit "0" beginnen.

## Zusammenfassung in einem Satz
`parseInt` in JavaScript konvertiert eine Zeichenfolge in eine Ganzzahl und ermöglicht die Angabe der Basis für die Konvertierung.