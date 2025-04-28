<!--
Meta Description: # SVGImageElement in JavaScript: Eine umfassende Anleitung ## Synopsis Der `SVGImageElement` ist ein DOM-Element, das es ermöglicht, SVG-Grafiken in H...
Meta Keywords: svg, image, das, ein, die
-->

# SVGImageElement in JavaScript: Eine umfassende Anleitung

## Synopsis
Der `SVGImageElement` ist ein DOM-Element, das es ermöglicht, SVG-Grafiken in HTML-Dokumente einzufügen und zu manipulieren. Es ist besonders nützlich für die Darstellung von Vektorgrafiken und bietet verschiedene Eigenschaften zur Anpassung.

## Dokumentation
`SVGImageElement` ist ein Teil der SVG (Scalable Vector Graphics)-Spezifikation und wird verwendet, um Rasterbilder in SVG-Dokumenten darzustellen. Dieses Element ist ein spezifischer Typ von `SVGElement` und ermöglicht das Einfügen von Bildern in ein SVG-Element. Es wird häufig verwendet, um Bitmap-Bilder wie JPEG, PNG oder GIF in eine SVG-Grafik zu integrieren.

### Eigenschaften
- **href**: Ein Attribut, das die URL des Bildes angibt, das eingebettet werden soll.
- **width**: Bestimmt die Breite des Bildes in Benutzerkoordinaten.
- **height**: Bestimmt die Höhe des Bildes in Benutzerkoordinaten.
- **preserveAspectRatio**: Gibt an, wie das Bild in Bezug auf seine ursprünglichen Dimensionen skaliert werden soll.

### Methoden
- **setAttribute()**: Ermöglicht das Setzen von Attributen des SVG-Bildes.
- **getAttribute()**: Ermöglicht das Abrufen von Attributen des SVG-Bildes.

### Verwendung
Um ein `SVGImageElement` zu erstellen, kann man entweder direkt im SVG-Code angeben oder über JavaScript dynamisch hinzufügen. Hier ist ein einfaches Beispiel:

```javascript
const svgNamespace = "http://www.w3.org/2000/svg";
const image = document.createElementNS(svgNamespace, "image");

image.setAttribute("href", "path/to/image.png");
image.setAttribute("width", "100");
image.setAttribute("height", "100");
document.querySelector("svg").appendChild(image);
```

## Beispiele
### Beispiel 1: Einfaches SVG-Bild einfügen
```html
<svg width="200" height="200">
  <image href="path/to/image.png" width="100" height="100" />
</svg>
```

### Beispiel 2: Dynamisches Hinzufügen eines SVG-Bildes mit JavaScript
```javascript
const svg = document.querySelector("svg");
const image = document.createElementNS("http://www.w3.org/2000/svg", "image");
image.setAttribute("href", "path/to/image.png");
image.setAttribute("width", "150");
image.setAttribute("height", "150");
svg.appendChild(image);
```

## Erklärung
Bei der Verwendung von `SVGImageElement` können einige häufige Fehler auftreten:
- **Falsche URL**: Wenn der `href`-Pfad falsch ist oder das Bild nicht gefunden werden kann, wird nichts angezeigt.
- **Größenverhältnisse**: Achten Sie darauf, dass die Attribute `width` und `height` korrekt gesetzt sind. Andernfalls kann das Bild verzerrt angezeigt werden.
- **Cross-Origin-Richtlinien**: Wenn Bilder von einer anderen Domain geladen werden, stellen Sie sicher, dass die CORS-Richtlinien die Verwendung erlauben.

## Ein-Satz-Zusammenfassung
`SVGImageElement` ist ein leistungsfähiges DOM-Element in JavaScript, das die Integration und Manipulation von Rasterbildern in SVG-Dokumenten ermöglicht.