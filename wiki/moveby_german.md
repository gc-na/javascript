<!--
Meta Description: # moveBy: Ein Überblick über die JavaScript-Methode zur Positionsänderung von Fenstern ## Synopsis Die `moveBy`-Methode in JavaScript ermöglicht es En...
Meta Keywords: die, moveby, methode, fenster, das
-->

# moveBy: Ein Überblick über die JavaScript-Methode zur Positionsänderung von Fenstern

## Synopsis
Die `moveBy`-Methode in JavaScript ermöglicht es Entwicklern, die Position eines Browserfensters relativ zu seiner aktuellen Position zu ändern. Diese Funktion ist besonders nützlich in Anwendungen, die mehrere Fenster verwenden.

## Documentation
### Zweck
Die `moveBy`-Methode wird verwendet, um ein geöffnetes Fenster um eine bestimmte Anzahl von Pixeln in horizontaler und vertikaler Richtung zu verschieben. Diese Methode gehört zum `window`-Objekt und ist in der Regel nur in Pop-up-Fenstern anwendbar, die durch Skripting geöffnet wurden.

### Verwendung
Die Syntax der `moveBy`-Methode ist wie folgt:

```javascript
window.moveBy(x, y);
```

- `x`: Ein Integer-Wert, der die Anzahl der Pixel angibt, um die das Fenster in horizontaler Richtung verschoben werden soll. Positive Werte verschieben das Fenster nach rechts, negative Werte nach links.
- `y`: Ein Integer-Wert, der die Anzahl der Pixel angibt, um die das Fenster in vertikaler Richtung verschoben werden soll. Positive Werte verschieben das Fenster nach unten, negative Werte nach oben.

### Details
- Die Methode funktioniert nur, wenn das Fenster ohne Einschränkungen geöffnet wurde (z.B. mit `window.open()` und den richtigen Parametern).
- Browser, die Pop-up-Blocker implementieren, können die Funktionalität von `moveBy` einschränken oder ganz blockieren.
- Die `moveBy`-Methode wird von modernen Browsern unterstützt, jedoch kann die Benutzererfahrung variieren.

## Examples
### Beispiel 1: Ein einfaches Verschieben des Fensters
```javascript
// Öffnen eines neuen Fensters
let newWindow = window.open("", "myWindow", "width=400,height=400");

// Warten, bis das Fenster geladen ist, und dann verschieben
newWindow.onload = function() {
    newWindow.moveBy(100, 50); // Verschiebt das Fenster um 100 Pixel nach rechts und 50 Pixel nach unten
};
```

### Beispiel 2: Verschieben mit negativen Werten
```javascript
// Verschiebt das Fenster um 50 Pixel nach links und 30 Pixel nach oben
newWindow.onload = function() {
    newWindow.moveBy(-50, -30);
};
```

## Explanation
Bei der Verwendung von `moveBy` gibt es einige häufige Stolpersteine und Hinweise:

- **Pop-up-Blocker:** Die Methode könnte aufgrund von Sicherheitseinstellungen oder Blockern nicht funktionieren, wenn das Fenster nicht als Pop-up geöffnet wurde.
- **Benutzererfahrung:** Übermäßiges oder unerwartetes Verschieben von Fenstern kann als störend empfunden werden; verwenden Sie diese Methode daher mit Bedacht.
- **Kompatibilität:** Obwohl die Methode in den meisten modernen Browsern unterstützt wird, kann die Implementierung variieren. Testen Sie Ihre Anwendung in verschiedenen Browsern.

## One Line Summary
Die `moveBy`-Methode in JavaScript ermöglicht das Verschieben eines Browserfensters relativ zur aktuellen Position.