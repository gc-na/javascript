<!--
Meta Description: # SVGFEDiffuseLightingElement in JavaScript: Eine umfassende Anleitung ## Synopsis Der `SVGFEDiffuseLightingElement` ist ein SVG-Element, das in JavaS...
Meta Keywords: die, svg, filter, svgfediffuselightingelement, das
-->

# SVGFEDiffuseLightingElement in JavaScript: Eine umfassende Anleitung

## Synopsis
Der `SVGFEDiffuseLightingElement` ist ein SVG-Element, das in JavaScript verwendet wird, um diffuse Lichtquellen in SVG-Grafiken zu erzeugen. Es ermöglicht Entwicklern, Licht- und Schatteneffekte zu simulieren, um visuelle Tiefe zu schaffen.

## Dokumentation
### Zweck
`SVGFEDiffuseLightingElement` wird verwendet, um diffuse Beleuchtungseffekte in SVG-Bildern zu erzeugen. Es ist Teil des SVG-Filter-Systems, das es ermöglicht, verschiedene visuelle Effekte auf grafische Elemente anzuwenden.

### Verwendung
Um ein `SVGFEDiffuseLightingElement` zu verwenden, müssen Sie es innerhalb eines `filter`-Elements in Ihrer SVG-Grafik definieren. Es ist wichtig, die Attribute korrekt zu setzen, um den gewünschten Beleuchtungseffekt zu erzielen.

### Details
- **Attribute:**
  - `in`: Gibt den Eingang des Filters an (z.B. das Element, auf das der Filter angewendet wird).
  - `surfaceScale`: Skaliert die Oberfläche, die beleuchtet wird.
  - `diffuseConstant`: Bestimmt die Stärke des diffusen Lichts.
  - `kernelUnitLength`: Definiert die Maßeinheit für den Kernel.
  - `lightingColor`: Bestimmt die Farbe des diffusen Lichts.

### Beispiel
Hier ist ein einfaches Beispiel eines `SVGFEDiffuseLightingElement` in einer SVG-Grafik:

```xml
<svg width="200" height="200">
  <defs>
    <filter id="diffuse-lighting-filter">
      <feDiffuseLighting in="SourceGraphic" surfaceScale="1" diffuseConstant="1">
        <light x="100" y="100" z="200" />
      </feDiffuseLighting>
    </filter>
  </defs>
  
  <rect x="10" y="10" width="100" height="100" fill="blue" filter="url(#diffuse-lighting-filter)" />
</svg>
```

## Erklärung
Ein häufiger Fehler bei der Verwendung von `SVGFEDiffuseLightingElement` ist, die Lichtquelle (`<light>`) außerhalb des Licht-Elements zu platzieren oder nicht die richtigen Werte für `surfaceScale` und `diffuseConstant` zu verwenden. Diese Werte beeinflussen stark, wie das Licht auf die Objekte wirkt. Ein zu hoher `surfaceScale`-Wert kann dazu führen, dass das Licht nicht richtig auf die Oberfläche auftrifft und die gewünschte Grafik nicht wie gewünscht aussieht.

## Zusammenfassung in einem Satz
`SVGFEDiffuseLightingElement` ermöglicht die Anwendung von diffusen Beleuchtungseffekten in SVG-Grafiken über JavaScript, um visuelle Tiefe und realistische Lichtverhältnisse zu schaffen.