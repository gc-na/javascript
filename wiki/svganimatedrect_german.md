<!--
Meta Description: # SVGAnimatedRect in JavaScript: Eine umfassende Anleitung ## Synopsis SVGAnimatedRect ist eine Web-Schnittstelle, die es ermöglicht, animierte Rechte...
Meta Keywords: svganimatedrect, die, svg, und, eine
-->

# SVGAnimatedRect in JavaScript: Eine umfassende Anleitung

## Synopsis
SVGAnimatedRect ist eine Web-Schnittstelle, die es ermöglicht, animierte Rechtecke in SVG-Grafiken zu erstellen. Sie bietet eine einfache Möglichkeit, die Attribute eines Rechtecks über Zeit zu ändern.

## Dokumentation
### Zweck
SVGAnimatedRect wird verwendet, um die Position und Größe von Rechtecken in Scalable Vector Graphics (SVG) zu animieren. Es ist besonders nützlich in interaktiven Anwendungen und Grafiken, wo dynamische Änderungen visuelle Effekte erzeugen.

### Verwendung
SVGAnimatedRect ist Teil der SVG-Spezifikation und wird typischerweise in Verbindung mit dem `<rect>`-Element verwendet. Diese Schnittstelle bietet animierte Attribute für die Position (x, y) und Dimensionen (width, height) eines Rechtecks.

### Details
Ein SVGAnimatedRect-Objekt hat folgende Eigenschaften:
- **baseVal**: Ein SVGRect, das den Basiswert des Rechtecks repräsentiert.
- **animVal**: Ein SVGRect, das den aktuellen animierten Wert des Rechtecks darstellt.

### Beispiel
Hier ist ein einfaches Beispiel, das zeigt, wie man ein SVGAnimatedRect in JavaScript verwenden kann:

```html
<svg width="200" height="200">
  <rect id="myRect" x="10" y="10" width="50" height="50" fill="blue">
    <animate attributeName="x" from="10" to="100" dur="2s" fill="freeze" />
  </rect>
</svg>

<script>
  const rect = document.getElementById('myRect');
  const animatedRect = rect.getCTM();

  console.log(animatedRect); // Gibt die transformierten Eigenschaften des Rechtecks aus.
</script>
```

## Erklärung
Eine häufige Falle bei der Verwendung von SVGAnimatedRect ist das Missverständnis bezüglich der animVal und baseVal Eigenschaften. Viele Entwickler erwarten, dass animVal sofort aktualisiert wird, wenn eine Animation gestartet wird. In Wirklichkeit wird animVal erst aktualisiert, nachdem die Animation tatsächlich beginnt. Außerdem sollten Sie sicherstellen, dass die Animationseinstellungen wie `dur` (Dauer) und `fill` (Fülltyp) korrekt definiert sind, um unerwartete Ergebnisse zu vermeiden.

## Einzeilensummary
SVGAnimatedRect ermöglicht die Animation von Rechtecken in SVG-Grafiken, was dynamische visuelle Effekte fördert.