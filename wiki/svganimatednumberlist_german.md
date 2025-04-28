<!--
Meta Description: # SVGAnimatedNumberList in JavaScript: Verwendung und Beispiele ## Synopsis SVGAnimatedNumberList ist ein JavaScript-Objekt, das verwendet wird, um ei...
Meta Keywords: die, und, svg, baseval, svganimatednumberlist
-->

# SVGAnimatedNumberList in JavaScript: Verwendung und Beispiele

## Synopsis
SVGAnimatedNumberList ist ein JavaScript-Objekt, das verwendet wird, um eine Liste von animierten Zahlen in SVG (Scalable Vector Graphics) darzustellen. Es ermöglicht die Definition und Animation von numerischen Werten in SVG-Elementen.

## Documentation
### Zweck
SVGAnimatedNumberList ist Teil der SVG-Spezifikation und ermöglicht die Animation von numerischen Werten, die in SVG-Elementen verwendet werden. Diese Werte können beispielsweise für Attribute wie `stroke-dasharray` oder `points` in Polyline- und Polygon-Elementen verwendet werden.

### Verwendung
SVGAnimatedNumberList wird typischerweise in Verbindung mit dem DOM (Document Object Model) von SVG verwendet. Es besteht aus zwei Hauptbestandteilen: einer `baseVal` und einer `animVal`. Die `baseVal` repräsentiert den statischen Wert der Liste, während `animVal` den aktuellen animierten Wert darstellt.

### Eigenschaften
- **baseVal**: Ein `SVGNumberList`, das die zugrunde liegenden Werte der Liste enthält.
- **animVal**: Ein `SVGNumberList`, das die aktuell animierten Werte enthält, die von SVG-Animationen verändert werden.

Diese Eigenschaften ermöglichen es Entwicklern, auf die Werte zuzugreifen und sie zu manipulieren, um dynamische und interaktive SVG-Grafiken zu erstellen.

## Examples
### Beispiel 1: Erstellen einer SVGAnimatedNumberList
```javascript
// Annahme: Wir haben ein SVG-Element mit einer animierten Linie
let line = document.querySelector('line');

// Zugriff auf die animierten Werte
let strokeDasharray = line.getAttribute('stroke-dasharray');

// Erstellen einer SVGAnimatedNumberList
let animatedNumberList = new SVGAnimatedNumberList();
animatedNumberList.baseVal = new SVGNumberList();
animatedNumberList.animVal = new SVGNumberList();

// Hinzufügen von Werten zur baseVal
animatedNumberList.baseVal.appendItem(10);
animatedNumberList.baseVal.appendItem(20);
```

### Beispiel 2: Zugriff auf die Werte
```javascript
// Zugriff auf die Basis- und Animationswerte
console.log(animatedNumberList.baseVal); // Gibt die Basiswerte aus
console.log(animatedNumberList.animVal);  // Gibt die animierten Werte aus
```

## Explanation
Ein häufiger Fallstrick bei der Arbeit mit SVGAnimatedNumberList ist das Missverständnis zwischen `baseVal` und `animVal`. Während `baseVal` die statischen Werte repräsentiert, ändern sich die `animVal`-Werte basierend auf der Animation. Wenn keine Animation auf das SVG-Element angewendet wird, sind `baseVal` und `animVal` identisch. 

Ein weiteres wichtiges Detail ist, dass nicht alle SVG-Attribute automatisch animierbar sind. Entwickler sollten sicherstellen, dass sie nur Attribute verwenden, die die Animation unterstützen.

## One Line Summary
SVGAnimatedNumberList ist ein JavaScript-Objekt zur Verwaltung und Animation von numerischen Werten in SVG-Grafiken.