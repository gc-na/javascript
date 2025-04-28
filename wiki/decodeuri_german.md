<!--
Meta Description: # decodeURI in JavaScript: Eine umfassende Anleitung zur URL-Dekodierung ## Synopsis Die Funktion `decodeURI` in JavaScript wird verwendet, um eine ko...
Meta Keywords: decodeuri, die, uri, javascript, zeichen
-->

# decodeURI in JavaScript: Eine umfassende Anleitung zur URL-Dekodierung

## Synopsis
Die Funktion `decodeURI` in JavaScript wird verwendet, um eine kodierte URI (Uniform Resource Identifier) zu dekodieren. Sie wandelt spezielle Zeichen, die in einer URI kodiert sind, in ihre ursprüngliche lesbare Form um.

## Documentation
Die `decodeURI`-Funktion ist ein integrierter Bestandteil von JavaScript und ermöglicht Entwicklern das Decodieren von URIs, die mit der Funktion `encodeURI` oder anderen URI-Kodierungsmechanismen erstellt wurden. Diese Funktion ist besonders nützlich, wenn URIs in einer Webanwendung verarbeitet werden müssen.

### Zweck
Der Hauptzweck von `decodeURI` ist es, kodierte Zeichen wie `%20` (für Leerzeichen), `%3A` (für `:`) und andere spezielle Zeichen zurück in ihre ursprünglichen Darstellung zu konvertieren.

### Usage
Die Syntax von `decodeURI` ist wie folgt:

```javascript
decodeURI(encodedURI)
```

**Parameter:**
- `encodedURI`: Eine kodierte URI als String, die dekodiert werden soll.

**Rückgabewert:**
Die Funktion gibt die dekodierte URI als String zurück.

### Details
`decodeURI` dekodiert alle kodierten Teile der URI, die durch `%` gefolgt von zwei hexadezimalen Ziffern dargestellt sind. Allerdings ignoriert `decodeURI` bestimmte Zeichen, die in URIs eine besondere Bedeutung haben, wie `#`, `?`, `&` usw. Diese Zeichen bleiben unverändert, um die Struktur der URI nicht zu beeinträchtigen.

## Examples
Hier sind einige einfache Beispiele zur Veranschaulichung der Verwendung von `decodeURI`:

### Beispiel 1: Einfache Dekodierung
```javascript
const encodedURI = "https%3A%2F%2Fwww.example.com%2Ftest%3Fname%3DJohn%20Doe";
const decodedURI = decodeURI(encodedURI);
console.log(decodedURI); // Ausgabe: https://www.example.com/test?name=John Doe
```

### Beispiel 2: Dekodierung mit Sonderzeichen
```javascript
const encodedURI = "https%3A%2F%2Fwww.example.com%2Fsearch%3Fquery%3DJavaScript%20Kurs";
const decodedURI = decodeURI(encodedURI);
console.log(decodedURI); // Ausgabe: https://www.example.com/search?query=JavaScript Kurs
```

## Explanation
Ein häufiges Missverständnis bei der Verwendung von `decodeURI` ist, dass es auch die dekodierten Zeichen wie `#`, `?` und `&` dekodiert. Tatsächlich ignoriert `decodeURI` diese Zeichen, da sie für die Struktur der URI wichtig sind. Wenn Sie jedoch alle kodierten Zeichen, einschließlich der Strukturzeichen, dekodieren möchten, sollten Sie `decodeURIComponent` verwenden.

Ein weiterer Punkt ist, dass die Eingabe von `decodeURI` korrekt kodiert sein muss. Andernfalls kann ein Fehler auftreten oder das Ergebnis kann unerwartet sein.

## One Line Summary
Die `decodeURI`-Funktion in JavaScript dekodiert eine kodierte URI und gibt sie in ihrer ursprünglichen Form zurück.