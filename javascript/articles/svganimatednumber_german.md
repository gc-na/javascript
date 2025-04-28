<!--
Meta Description: # SVGAnimatedNumber in JavaScript: Eine umfassende Anleitung ## Synopsis SVGAnimatedNumber ist ein Datentyp in der SVG (Scalable Vector Graphics) API,...
Meta Keywords: circle, svg, baseval, ist, der
-->

# SVGAnimatedNumber in JavaScript: Eine umfassende Anleitung 

## Synopsis
SVGAnimatedNumber ist ein Datentyp in der SVG (Scalable Vector Graphics) API, der es ermöglicht, animierte numerische Werte in SVG-Elementen zu verarbeiten. Dieser Typ ist besonders nützlich für Animationen und Interaktivität in Webanwendungen.

## Dokumentation

### Zweck
SVGAnimatedNumber wird verwendet, um numerische Werte zu speichern, die sich im Laufe der Zeit ändern können, insbesondere im Rahmen von SVG-Animationen. Es ist ein Bestandteil der SVG DOM und ermöglicht es Entwicklern, auf animierte Werte zuzugreifen und diese zu steuern.

### Verwendung
In JavaScript kann SVGAnimatedNumber über verschiedene SVG-Elemente, wie etwa `<circle>`, `<rect>` oder `<line>`, erstellt werden. Um auf den aktuellen Wert zuzugreifen, können Sie die Eigenschaften `baseVal` und `animVal` verwenden:

- `baseVal`: Der Basiswert, der den aktuellen Zustand des Attributs darstellt.
- `animVal`: Der aktuelle animierte Wert des Attributs.

### Details 
SVGAnimatedNumber ist eine Schnittstelle, die von anderen SVG-Elementen genutzt wird, um numerische Attribute zu animieren. Die Werte können sowohl direkt im SVG-Code als auch über JavaScript manipulierbar sein. 

## Beispiele

### Beispiel 1: Zugriff auf `baseVal` und `animVal`
```javascript
// Erstellen eines SVG-Elements
let svgNS = "http://www.w3.org/2000/svg";
let circle = document.createElementNS(svgNS, "circle");
circle.setAttribute("cx", "50");
circle.setAttribute("cy", "50");
circle.setAttribute("r", "40");
circle.setAttribute("fill", "red");

// Hinzufügen des Kreises zum DOM
document.getElementById("svgContainer").appendChild(circle);

// Zugriff auf die animierten Werte
let radius = circle.r.baseVal; // Zugriff auf baseVal
console.log("Basiswert: ", radius.value); // Ausgabe: Basiswert: 40

// Simulieren einer Animation
setTimeout(() => {
    circle.r.baseVal.value = 60; // Ändern des Basiswerts
    console.log("Aktualisierter Basiswert: ", circle.r.baseVal.value); // Ausgabe: Aktualisierter Basiswert: 60
}, 2000);
```

### Beispiel 2: Animation eines Kreises
```javascript
let circle = document.querySelector("circle");

// Animation des Radius über setInterval
let radius = 40;
setInterval(() => {
    radius += 5;
    if (radius > 100) radius = 40; // Zurücksetzen
    circle.setAttribute("r", radius);
}, 1000);
```

## Erklärung
Ein häufiger Fehler beim Arbeiten mit SVGAnimatedNumber ist das Missverständnis über die `baseVal` und `animVal` Eigenschaften. `baseVal` wird verwendet, um den aktuellen Wert des Attributs zu setzen, während `animVal` den Wert repräsentiert, der durch Animationen erreicht wird. Es ist wichtig zu beachten, dass `animVal` nicht direkt verändert werden kann, da es nur den aktuellen animierten Zustand widerspiegelt.

Ein weiterer Punkt ist, dass SVG-Animationen nicht immer in allen Browsern gleich gut unterstützt werden. Es empfiehlt sich, die Kompatibilität zu überprüfen, bevor Sie umfangreiche Animationen implementieren.

## Ein-Satz-Zusammenfassung
SVGAnimatedNumber ist ein wichtiger Datentyp in JavaScript für die Handhabung und Animation von numerischen Werten in SVG-Elementen.