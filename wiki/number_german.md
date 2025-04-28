<!--
Meta Description: # JavaScript Number: Grundlagen, Verwendung und Beispiele ## Synopsis Die `Number`-Objekt in JavaScript ermöglicht die Darstellung und Manipulation vo...
Meta Keywords: number, von, javascript, und, ist
-->

# JavaScript Number: Grundlagen, Verwendung und Beispiele

## Synopsis
Die `Number`-Objekt in JavaScript ermöglicht die Darstellung und Manipulation von numerischen Werten. Es bietet verschiedene Funktionen zur Umwandlung, Berechnung und Überprüfung von Zahlen.

## Dokumentation
Das `Number`-Objekt in JavaScript ist ein eingebautes globales Objekt, das eine Reihe von Eigenschaften und Methoden zur Verfügung stellt, um mit numerischen Werten zu arbeiten. Es unterstützt sowohl Ganzzahlen als auch Fließkommazahlen und ist unveränderlich.

### Eigenschaften
- **`Number.MAX_VALUE`**: Der größte mögliche Wert, den eine Zahl darstellen kann.
- **`Number.MIN_VALUE`**: Der kleinste positive Wert, der von einer Zahl dargestellt werden kann.
- **`Number.NEGATIVE_INFINITY`**: Repräsentiert negative Unendlichkeit.
- **`Number.POSITIVE_INFINITY`**: Repräsentiert positive Unendlichkeit.
- **`Number.NaN`**: Steht für "Not-a-Number" und wird verwendet, wenn eine mathematische Berechnung fehlschlägt.

### Methoden
- **`Number.isNaN(value)`**: Überprüft, ob der übergebene Wert `NaN` ist.
- **`Number.isFinite(value)`**: Prüft, ob der Wert ein endlicher Zahl ist.
- **`Number.parseInt(string, radix)`**: Wandelt einen String in eine Ganzzahl um.
- **`Number.parseFloat(string)`**: Wandelt einen String in eine Fließkommazahl um.
- **`Number.toFixed(digits)`**: Formatiert eine Zahl mit einer bestimmten Anzahl von Dezimalstellen.

## Beispiele
### Beispiel 1: Verwendung von `Number.parseInt`
```javascript
let ganzzahl = Number.parseInt("42");
console.log(ganzzahl); // Ausgabe: 42
```

### Beispiel 2: Verwendung von `Number.isNaN`
```javascript
let wert = "Hallo";
console.log(Number.isNaN(wert)); // Ausgabe: false
```

### Beispiel 3: Verwendung von `Number.toFixed`
```javascript
let zahl = 5.6789;
console.log(zahl.toFixed(2)); // Ausgabe: "5.68"
```

## Erklärung
Bei der Arbeit mit dem `Number`-Objekt gibt es einige häufige Stolpersteine:

- **NaN-Vergleiche**: `NaN` ist nicht gleich `NaN`. Um zu überprüfen, ob ein Wert `NaN` ist, sollte die Methode `Number.isNaN()` verwendet werden.
- **Fließkomma-Präzision**: Fließkommazahlen können aufgrund von Rundungsfehlern unerwartete Ergebnisse liefern. Zum Beispiel ist `0.1 + 0.2 !== 0.3`.
- **Typumwandlung**: JavaScript führt beim Rechnen oft implizite Typumwandlungen durch, was zu unerwarteten Ergebnissen führen kann. Es ist ratsam, Werte mit `Number()` oder ähnlichen Methoden explizit in Zahlen umzuwandeln.

## Ein Satz Zusammenfassung
Das `Number`-Objekt in JavaScript bietet essentielle Funktionen zur Verarbeitung und Handhabung numerischer Werte, einschließlich Umwandlungen und mathematischer Operationen.