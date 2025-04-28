<!--
Meta Description: # SVGFESpotLightElement: Der Schlüssel zur Lichtsteuerung in SVG mit JavaScript ## Synopsis Das `SVGFESpotLightElement` ist ein DOM-Element in SVG (Sc...
Meta Keywords: svg, die, filter, 200, das
-->

# SVGFESpotLightElement: Der Schlüssel zur Lichtsteuerung in SVG mit JavaScript

## Synopsis
Das `SVGFESpotLightElement` ist ein DOM-Element in SVG (Scalable Vector Graphics), das verwendet wird, um Lichtquellen mit spezifischen Eigenschaften zu definieren. Dieses Element ist entscheidend für die Erstellung von beleuchteten Effekten und Schatten in SVG-Grafiken und wird häufig in Kombination mit JavaScript verwendet, um dynamische und interaktive Grafiken zu erstellen.

## Documentation
Das `SVGFESpotLightElement` ist Teil der SVG-Spezifikation und ermöglicht die Definition von Spot-Lichtern innerhalb von SVG-Grafiken. Ein Spot-Licht hat eine spezifische Position, Richtung, und kann durch verschiedene Parameter wie Blendenwinkel und Intensität gesteuert werden. 

### Eigenschaften
- **x**: Definiert die X-Position des Lichtpunkts.
- **y**: Definiert die Y-Position des Lichtpunkts.
- **z**: Definiert die Z-Position des Lichtpunkts (Tiefe).
- **pointsAtX**: Gibt die X-Position des Punktes an, auf den das Licht gerichtet ist.
- **pointsAtY**: Gibt die Y-Position des Punktes an, auf den das Licht gerichtet ist.
- **pointsAtZ**: Gibt die Z-Position des Punktes an, auf den das Licht gerichtet ist.
- **specularExponent**: Steuert den Glanz des Lichtes.
- **limitingConeAngle**: Bestimmt den Winkel des Lichtkegels.

### Verwendung
Um `SVGFESpotLightElement` zu verwenden, muss es innerhalb eines `filter`-Elements in SVG platziert werden. Der Filter kann dann auf andere SVG-Elemente angewendet werden, um den gewünschten Lichteffekt zu erzielen.

```html
<svg width="200" height="200">
    <defs>
        <filter id="spotlight">
            <feSpotLight x="50" y="50" z="30" pointsAtX="50" pointsAtY="50" specularExponent="20" limitingConeAngle="30" />
        </filter>
    </defs>
    <circle cx="100" cy="100" r="40" fill="red" filter="url(#spotlight)" />
</svg>
```

## Examples
Hier sind einige grundlegende Beispielanwendungen für `SVGFESpotLightElement`:

### Beispiel 1: Einfaches Spotlicht
```html
<svg width="300" height="300">
    <defs>
        <filter id="lightEffect">
            <feSpotLight x="150" y="100" z="50" pointsAtX="150" pointsAtY="150" specularExponent="10" limitingConeAngle="15" />
        </filter>
    </defs>
    <rect x="50" y="50" width="200" height="200" fill="blue" filter="url(#lightEffect)" />
</svg>
```

### Beispiel 2: Dynamisches Spotlicht mit JavaScript
```html
<svg id="svgCanvas" width="400" height="400">
    <defs>
        <filter id="dynamicLight">
            <feSpotLight id="spotLight" x="200" y="200" z="100" pointsAtX="200" pointsAtY="200" specularExponent="5" limitingConeAngle="20" />
        </filter>
    </defs>
    <circle cx="200" cy="200" r="50" fill="green" filter="url(#dynamicLight)" />
</svg>

<script>
    const spotLight = document.getElementById('spotLight');
    document.addEventListener('mousemove', (event) => {
        spotLight.setAttribute('pointsAtX', event.clientX);
        spotLight.setAttribute('pointsAtY', event.clientY);
    });
</script>
```

## Explanation
Ein häufiges Problem bei der Verwendung von `SVGFESpotLightElement` ist die falsche Positionierung der Lichter, was zu unerwarteten Effekten führen kann. Stellen Sie sicher, dass Sie die `x`, `y` und `z`-Werte korrekt setzen, um das Licht richtig zu positionieren. Auch die Verwendung von zu hohen Werten für `specularExponent` kann zu einem sehr harten Licht führen, das möglicherweise nicht den gewünschten Effekt erzielt.

Ein weiterer wichtiger Punkt ist die Unterstützung in verschiedenen Browsern. Überprüfen Sie die Kompatibilität, da einige ältere Browser möglicherweise nicht alle SVG-Filterfunktionen unterstützen.

## One Line Summary
`SVGFESpotLightElement` ermöglicht die Definition von Spot-Lichtern in SVG, um beeindruckende Licht- und Schatteneffekte in JavaScript-gesteuerten Grafiken zu erzeugen.