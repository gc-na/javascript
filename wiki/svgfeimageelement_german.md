<!--
Meta Description: # SVGFEImageElement in JavaScript: Verwendung und Funktionen ## Zusammenfassung Das `SVGFEImageElement` ist ein Bestandteil der SVG (Scalable Vector G...
Meta Keywords: svg, feimage, das, die, setattribute
-->

# SVGFEImageElement in JavaScript: Verwendung und Funktionen

## Zusammenfassung
Das `SVGFEImageElement` ist ein Bestandteil der SVG (Scalable Vector Graphics) Spezifikation, der es ermöglicht, rasterisierte Bilder innerhalb von SVG-Dokumenten zu integrieren. In JavaScript wird es verwendet, um die Manipulation und das Management von Bildinhalten in SVG-Grafiken zu erleichtern.

## Dokumentation
### Zweck
Das `SVGFEImageElement` repräsentiert das <feImage> Element in SVG, das dazu dient, Bilder in SVG-Filteranwendungen zu laden und darzustellen. Es ist besonders nützlich für die Anwendung von Bildfiltern und für die Erstellung komplexer Grafiken.

### Verwendung
Um ein `SVGFEImageElement` zu verwenden, muss es innerhalb eines SVG-Dokuments platziert werden. Es kann durch JavaScript erstellt und manipuliert werden, um Bilder dynamisch zu laden, die innerhalb von SVG-Filtereffekten verwendet werden.

### Details
- **Eigenschaften**:
  - `href`: Die URL des Bildes, das geladen werden soll.
  - `width` und `height`: Bestimmen die Dimensionen des Bildes.
  - `preserveAspectRatio`: Gibt an, wie das Bild in Bezug auf die ursprünglichen Dimensionen skaliert wird.

- **Methoden**:
  - `setAttribute(name, value)`: Setzt ein Attribut auf dem Element.
  - `getAttribute(name)`: Ruft den Wert eines Attributs ab.

## Beispiele
### Beispiel 1: Einfaches SVG mit feImage
```javascript
const svgNS = "http://www.w3.org/2000/svg";
const feImage = document.createElementNS(svgNS, "feImage");
feImage.setAttribute("href", "bild.jpg");
feImage.setAttribute("width", "100");
feImage.setAttribute("height", "100");

const filter = document.createElementNS(svgNS, "filter");
filter.appendChild(feImage);

const svg = document.createElementNS(svgNS, "svg");
svg.appendChild(filter);
document.body.appendChild(svg);
```

### Beispiel 2: Bild mit preserveAspectRatio
```javascript
const feImage = document.createElementNS(svgNS, "feImage");
feImage.setAttribute("href", "bild.jpg");
feImage.setAttribute("width", "200");
feImage.setAttribute("height", "200");
feImage.setAttribute("preserveAspectRatio", "xMidYMid meet");

const filter = document.createElementNS(svgNS, "filter");
filter.appendChild(feImage);
```

## Erklärung
Ein häufiges Problem beim Arbeiten mit `SVGFEImageElement` ist das Laden von Bildern aus unterschiedlichen Domänen, was zu CORS-Problemen führen kann. Stellen Sie sicher, dass die Bilder, die Sie laden möchten, die entsprechenden CORS-Header setzen, um diese Probleme zu vermeiden. Außerdem sollten Sie darauf achten, dass das Bildformat unterstützt wird, da nicht alle Formate in allen Browsern gleich gut unterstützt werden.

## Zusammenfassung in einem Satz
Das `SVGFEImageElement` ist ein wichtiges Element in SVG, das es ermöglicht, rasterisierte Bilder innerhalb von SVG-Grafiken zu integrieren und mit JavaScript zu steuern.