<!--
Meta Description: # DOMRectList in JavaScript: Eine umfassende Anleitung ## Synopsis DOMRectList ist eine Sammlung von DOMRect-Objekten, die die geometrischen Eigenscha...
Meta Keywords: die, von, domrectlist, eigenschaften, ist
-->

# DOMRectList in JavaScript: Eine umfassende Anleitung

## Synopsis
DOMRectList ist eine Sammlung von DOMRect-Objekten, die die geometrischen Eigenschaften von Rechtecken im Dokument beschreibt. Diese Funktionalität ist besonders nützlich für die Arbeit mit DOM-Elementen und deren Positionen auf der Webseite.

## Documentation
### Zweck
DOMRectList wird verwendet, um eine Liste von DOMRect-Objekten zu repräsentieren, die typischerweise von Methoden wie `getClientRects()` oder `getBoundingClientRect()` zurückgegeben werden. Diese Objekte bieten Informationen zu den Dimensionen und Positionen von Elementen im Dokumentenlayout.

### Verwendung
Die DOMRectList wird in der Regel in den folgenden Szenarien verwendet:
- Zur Bestimmung der Position und Größe eines Elements auf der Webseite.
- Um geometrische Berechnungen durchzuführen, z.B. für Kollisionserkennung oder Layout-Anpassungen.

### Details
- **Eigenschaften**: DOMRectList hat keine eigenen Eigenschaften, sondern besteht aus DOMRect-Objekten, die jeweils die Eigenschaften `width`, `height`, `top`, `right`, `bottom`, und `left` besitzen.
- **Methoden**: Die DOMRectList ist eine iterable, das heißt, Sie können über die enthaltenen DOMRect-Objekte iterieren.

## Beispiele
### Beispiel 1: Verwendung von getClientRects()
```javascript
let element = document.getElementById('meinElement');
let rects = element.getClientRects();

for (let rect of rects) {
    console.log(`Breite: ${rect.width}, Höhe: ${rect.height}`);
}
```

### Beispiel 2: Verwendung von getBoundingClientRect()
```javascript
let element = document.getElementById('meinElement');
let boundingRect = element.getBoundingClientRect();

console.log(`Position: (${boundingRect.left}, ${boundingRect.top})`);
console.log(`Größe: ${boundingRect.width} x ${boundingRect.height}`);
```

## Erklärung
**Häufige Stolpersteine**:
- **Leere DOMRectList**: Wenn das Element, von dem Sie die Rechtecke abrufen, nicht im Dokument sichtbar ist oder keine Bereiche hat, kann die DOMRectList leer sein.
- **Zugriff auf Eigenschaften**: Stellen Sie sicher, dass Sie die Eigenschaften von DOMRect-Objekten korrekt verwenden, da ein falscher Zugriff zu `undefined` führen kann.
- **Browser-Kompatibilität**: Überprüfen Sie die Unterstützung in älteren Browsern, da nicht alle Methoden in allen Browsern gleich implementiert sein können.

## One Line Summary
DOMRectList ist eine Sammlung von DOMRect-Objekten, die die geometrischen Eigenschaften von Elementen im Dokument beschreibt und nützlich für Layout- und Positionsabfragen ist.