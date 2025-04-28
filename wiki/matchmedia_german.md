<!--
Meta Description: # matchMedia in JavaScript: Responsive Design und Media Queries ## Synopsis `matchMedia` ist eine JavaScript-Funktion, die es Entwicklern ermöglicht, ...
Meta Keywords: die, der, media, matchmedia, ist
-->

# matchMedia in JavaScript: Responsive Design und Media Queries

## Synopsis
`matchMedia` ist eine JavaScript-Funktion, die es Entwicklern ermöglicht, Media Queries zu überprüfen und auf Änderungen in der Bildschirmgröße oder anderen Eigenschaften des Viewports zu reagieren. Dies ist besonders nützlich für die Implementierung responsiver Designs.

## Dokumentation
Die Methode `window.matchMedia()` wird verwendet, um eine Media Query zu evaluieren. Sie gibt ein `MediaQueryList`-Objekt zurück, das Informationen über den Status der Media Query bereitstellt, einschließlich ob die Query zutrifft oder nicht.

### Zweck
Mit `matchMedia` können Entwickler:
- Media Queries programmgesteuert abfragen.
- Auf Änderungen in der Übereinstimmung der Media Queries hören.
- Dynamisch CSS-Stile oder JavaScript-Funktionen basierend auf dem Viewport anpassen.

### Verwendung
Die Syntax von `matchMedia` ist wie folgt:

```javascript
const mediaQueryList = window.matchMedia(mediaQueryString);
```

- `mediaQueryString`: Ein String, der die Media Query beschreibt (z.B. `"(max-width: 600px)"`).

### Eigenschaften des MediaQueryList-Objekts
- `matches`: Ein Boolean, der angibt, ob die Media Query zutrifft.
- `media`: Ein String, der die Media Query zurückgibt.
- `addListener(callback)`: Fügt einen Listener hinzu, der auf Änderungen in der Übereinstimmung reagiert (veraltet).
- `removeListener(callback)`: Entfernt einen Listener (veraltet).
- `addEventListener(type, listener)`: Fügt einen Event-Listener hinzu, der auf Änderungen reagiert.
- `removeEventListener(type, listener)`: Entfernt einen Event-Listener.

## Beispiele
### Beispiel 1: Einfache Abfrage
```javascript
const mediaQueryList = window.matchMedia("(max-width: 600px)");

if (mediaQueryList.matches) {
    console.log("Das Viewport ist 600px oder kleiner.");
} else {
    console.log("Das Viewport ist größer als 600px.");
}
```

### Beispiel 2: Auf Änderungen reagieren
```javascript
const mediaQueryList = window.matchMedia("(max-width: 600px)");

function handleMediaChange(e) {
    if (e.matches) {
        console.log("Viewport ist 600px oder kleiner.");
    } else {
        console.log("Viewport ist größer als 600px.");
    }
}

mediaQueryList.addEventListener('change', handleMediaChange);
```

## Erklärung
Ein häufiger Fehler bei der Verwendung von `matchMedia` ist das Vergessen, die `change`-Ereignisse zu behandeln. Entwickler sollten sicherstellen, dass sie Listener hinzufügen, um auf Änderungen in der Übereinstimmung zu reagieren, insbesondere bei dynamischen Layouts.

Es ist auch wichtig zu beachten, dass die Methoden `addListener` und `removeListener` veraltet sind. Stattdessen sollten die Methoden `addEventListener` und `removeEventListener` verwendet werden, um die Kompatibilität mit modernen Browsern zu gewährleisten.

## Ein-Zeilen-Zusammenfassung
`matchMedia` ist eine leistungsstarke JavaScript-Funktion, die Entwicklern hilft, Media Queries zu überprüfen und auf Änderungen im Viewport dynamisch zu reagieren.