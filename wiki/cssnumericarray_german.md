<!--
Meta Description: # CSSNumericArray in JavaScript: Eine umfassende Anleitung ## Synopsis CSSNumericArray ist eine JavaScript-Schnittstelle, die es Entwicklern ermöglich...
Meta Keywords: cssnumericarray, css, die, mit, werten
-->

# CSSNumericArray in JavaScript: Eine umfassende Anleitung

## Synopsis
CSSNumericArray ist eine JavaScript-Schnittstelle, die es Entwicklern ermöglicht, numerische Werte in CSS-Variablen zu verwalten und zu manipulieren. Diese Schnittstelle ist besonders nützlich für die Arbeit mit CSS-Funktionen, die mehrere numerische Werte erfordern, wie z.B. `translate`, `scale` oder `rotate`.

## Dokumentation
### Zweck
CSSNumericArray wird verwendet, um eine Sammlung von CSS-numerischen Werten darzustellen. Diese Schnittstelle ermöglicht es Entwicklern, mit diesen Werten zu rechnen, sie zu konvertieren und sie in CSS-Anweisungen zu verwenden.

### Verwendung
Um mit CSSNumericArray zu arbeiten, müssen Sie sicherstellen, dass Sie eine CSS-Funktion verwenden, die mehrere numerische Werte akzeptiert. Die Werte werden in einer Array-ähnlichen Struktur gespeichert, die mathematische Operationen und die Umwandlung zwischen verschiedenen Einheiten ermöglicht.

### Details
- **Erstellung**: CSSNumericArray-Instanzen können durch die Verwendung von CSS-Funktionen, wie `CSSNumericValue`, erstellt werden.
- **Methoden**: CSSNumericArray bietet verschiedene Methoden zur Manipulation der Zahlen, darunter `add`, `subtract`, `multiply`, und `divide`.
- **Einheiten**: Die Werte können in verschiedenen CSS-Einheiten wie `px`, `em`, `rem` und anderen angegeben werden.

## Beispiele
```javascript
// Erstellen eines CSSNumericArray mit zwei Werten
const numericArray = new CSSNumericArray([CSS.px(10), CSS.px(20)]);

// Addition von Werten
const result = numericArray.add(CSS.px(5)); // Ergebnis: CSSNumericArray mit Werten [15px, 20px]

// Multiplikation eines Wertes
const scaled = numericArray.multiply(2); // Ergebnis: CSSNumericArray mit Werten [20px, 40px]
```

## Erklärung
Ein häufiges Missverständnis ist, dass CSSNumericArray wie ein reguläres JavaScript-Array behandelt werden kann. Beachten Sie, dass CSSNumericArray spezifische Methoden und Eigenschaften hat, die für die Manipulation von CSS-Werten optimiert sind. Außerdem können nicht alle mathematischen Operationen direkt auf CSSNumericArray angewendet werden, was zu Fehlern führen kann, wenn diese nicht berücksichtigt werden.

Ein weiterer Punkt ist, dass die Verwendung von CSSNumericArray in Kombination mit CSS-in-JS-Bibliotheken möglicherweise nicht immer unterstützt wird, da diese Bibliotheken oft eigene Mechanismen zur Handhabung von CSS-Variablen verwenden.

## Eine-Satz-Zusammenfassung
CSSNumericArray in JavaScript ermöglicht die effiziente Handhabung und Manipulation von numerischen Werten in CSS-Funktionen mit einer Vielzahl nützlicher Methoden.