<!--
Meta Description: # SVGLinearGradientElement in JavaScript: Verwendung und Beispiele ## Synopsis `SVGLinearGradientElement` ist ein wichtiges Interface im SVG (Scalable...
Meta Keywords: svg, setattribute, lineargradient, ein, die
-->

# SVGLinearGradientElement in JavaScript: Verwendung und Beispiele

## Synopsis
`SVGLinearGradientElement` ist ein wichtiges Interface im SVG (Scalable Vector Graphics), das in JavaScript verwendet wird, um lineare Farbverläufe zu definieren und anzuwenden. Es ermöglicht Entwicklern, dynamisch Farbverläufe in SVG-Grafiken zu erstellen und zu manipulieren.

## Dokumentation
`SVGLinearGradientElement` ist ein Teil der SVG-Spezifikation und stellt ein lineares Farbverlaufselement dar. Dieses Element wird häufig verwendet, um den visuellen Effekt von Tiefe oder Dimension in Grafiken zu erzeugen. Ein linearer Farbverlauf wird durch zwei oder mehr Farbstopps definiert, die entlang einer geraden Linie angeordnet sind.

### Zweck
Der Hauptzweck von `SVGLinearGradientElement` ist es, Farbverläufe in SVG-Grafiken zu erstellen, die dann auf verschiedene SVG-Elemente angewendet werden können, wie z.B. Rechtecke, Kreise und Pfade.

### Verwendung
Um `SVGLinearGradientElement` zu verwenden, müssen Sie zunächst ein SVG-Element erstellen und dann ein `linearGradient`-Element hinzufügen. Dies geschieht typischerweise mit JavaScript, um die Eigenschaften des Farbverlaufs dynamisch zu ändern.

Hier ist ein typisches Beispiel, wie man einen linearen Farbverlauf in JavaScript erstellt:

```javascript
// Erstellen des SVG-Elements
const svgNS = "http://www.w3.org/2000/svg";
const svg = document.createElementNS(svgNS, "svg");
svg.setAttribute("width", "200");
svg.setAttribute("height", "200");

// Erstellen des linearen Farbverlaufs
const linearGradient = document.createElementNS(svgNS, "linearGradient");
linearGradient.setAttribute("id", "gradient1");
linearGradient.setAttribute("x1", "0%");
linearGradient.setAttribute("y1", "0%");
linearGradient.setAttribute("x2", "100%");
linearGradient.setAttribute("y2", "100%");

// Hinzufügen von Farbstopps
const stop1 = document.createElementNS(svgNS, "stop");
stop1.setAttribute("offset", "0%");
stop1.setAttribute("stop-color", "red");
linearGradient.appendChild(stop1);

const stop2 = document.createElementNS(svgNS, "stop");
stop2.setAttribute("offset", "100%");
stop2.setAttribute("stop-color", "blue");
linearGradient.appendChild(stop2);

// Hinzufügen des Farbverlaufs zum SVG
svg.appendChild(linearGradient);

// Erstellen eines Rechtecks mit dem Farbverlauf
const rect = document.createElementNS(svgNS, "rect");
rect.setAttribute("width", "200");
rect.setAttribute("height", "200");
rect.setAttribute("fill", "url(#gradient1)");
svg.appendChild(rect);

// Hinzufügen des SVG zum Dokument
document.body.appendChild(svg);
```

## Erklärung
Ein häufiges Problem bei der Verwendung von `SVGLinearGradientElement` ist, dass der Farbverlauf möglicherweise nicht korrekt angezeigt wird, wenn die `id` des Farbverlaufs nicht richtig referenziert wird. Stellen Sie sicher, dass der `fill`-Wert des SVG-Elements mit der `id` des `linearGradient` übereinstimmt.

Ein weiterer Punkt ist, dass die Koordinaten für `x1`, `y1`, `x2` und `y2` die Richtung des Farbverlaufs bestimmen. Ein falsches Setzen dieser Werte kann zu unerwarteten Ergebnissen führen.

Es ist auch wichtig zu beachten, dass die `stop-color`-Eigenschaft die Farbe der Farbstopps definiert, während die `offset`-Eigenschaft angibt, an welcher Stelle im Verlauf dieser Stopp angewendet wird.

## Ein-Satz-Zusammenfassung
`SVGLinearGradientElement` ermöglicht die dynamische Erstellung und Manipulation von linearen Farbverläufen in SVG-Grafiken mittels JavaScript.