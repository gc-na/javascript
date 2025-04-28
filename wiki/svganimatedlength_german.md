<!--
Meta Description: # SVGAnimatedLength in JavaScript: Ein umfassender Leitfaden ## Synopsis SVGAnimatedLength ist ein Teil der SVG-Spezifikation, der es ermöglicht, Läng...
Meta Keywords: der, svg, die, svganimatedlength, ist
-->

# SVGAnimatedLength in JavaScript: Ein umfassender Leitfaden

## Synopsis
SVGAnimatedLength ist ein Teil der SVG-Spezifikation, der es ermöglicht, Längenwerte (wie Breite und Höhe) animierbar zu machen. In JavaScript wird es verwendet, um dynamische SVG-Grafiken zu erstellen, die auf Benutzerinteraktionen oder zeitbasierte Animationen reagieren.

## Dokumentation
### Zweck
SVGAnimatedLength wird verwendet, um Längenwerte innerhalb von SVG-Elementen zu definieren, die animiert werden können. Es ermöglicht Entwicklern, sowohl statische als auch dynamische Änderungen an den Längenwerten vorzunehmen, was für die Erstellung von komplexen Animationen und interaktiven Grafiken unerlässlich ist.

### Verwendung
SVGAnimatedLength ist eine Schnittstelle, die zwei Eigenschaften enthält:
- `baseVal`: Der Basiswert der Länge, der nicht animiert werden kann.
- `animVal`: Der aktuelle animierte Wert der Länge, der sich während der Animation ändern kann.

Um SVGAnimatedLength in JavaScript zu verwenden, müssen Sie ein SVG-Element in Ihrem Dokument haben, das eine animierbare Länge unterstützt. Typische Anwendung findet man bei Elementen wie `<line>`, `<rect>`, `<circle>` und `<ellipse>`.

### Details
Die Eigenschaften `baseVal` und `animVal` sind in der Regel vom Typ `SVGLength`. Sie können mit diesen Werten arbeiten, um die Darstellung von SVG-Elementen dynamisch zu ändern. Es ist wichtig zu beachten, dass Änderungen an `baseVal` den animierten Wert (`animVal`) beeinflussen können, jedoch nicht umgekehrt.

## Beispiele
### Beispiel 1: Einfache Verwendung von SVGAnimatedLength
```html
<svg width="200" height="200">
  <rect id="myRect" width="100" height="100" fill="blue" />
</svg>

<script>
  const rect = document.getElementById('myRect');
  rect.width.baseVal.value = 150; // Setzt die Breite auf 150
</script>
```

### Beispiel 2: Animierte Länge
```html
<svg width="200" height="200">
  <line id="myLine" x1="0" y1="0" x2="100" y2="100" stroke="red" />
</svg>

<script>
  const line = document.getElementById('myLine');
  line.x2.baseVal.value = 150; // Ändert die Endkoordinate der Linie
</script>
```

## Erklärung
Eine häufige Falle bei der Verwendung von SVGAnimatedLength ist, dass Entwickler den Wert von `animVal` direkt ändern wollen, was nicht möglich ist. Stattdessen sollte immer `baseVal` verwendet werden, um den gewünschten Effekt zu erzielen. Eine weitere Schwierigkeit kann auftreten, wenn SVG-Elemente nicht korrekt im DOM platziert sind oder wenn sie nicht die erwarteten Eigenschaften haben.

Es ist auch wichtig, die Synchronisation zwischen `baseVal` und `animVal` zu verstehen. Wenn eine Animation aktiv ist, kann `animVal` sich unabhängig von `baseVal` ändern, was dazu führen kann, dass der Entwickler nicht den erwarteten Wert erhält, wenn er auf `animVal` zugreift.

## Ein-Satz-Zusammenfassung
SVGAnimatedLength ermöglicht es Entwicklern, Längenwerte in SVG-Elementen zu animieren und bietet eine flexible Möglichkeit zur Erstellung dynamischer Grafiken in JavaScript.