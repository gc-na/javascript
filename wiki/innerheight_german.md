<!--
Meta Description: # innerHeight in JavaScript: Höhe des Ansichtsfensters Abrufen ## Synopsis Die `innerHeight`-Eigenschaft in JavaScript ermöglicht es Entwicklern, die ...
Meta Keywords: die, höhe, innerheight, des, ansichtsfensters
-->

# innerHeight in JavaScript: Höhe des Ansichtsfensters Abrufen

## Synopsis
Die `innerHeight`-Eigenschaft in JavaScript ermöglicht es Entwicklern, die Höhe des Ansichtsfensters (Viewport) eines Fensters in Pixeln zu ermitteln. Diese Eigenschaft ist nützlich, um responsive Designs zu erstellen und das Layout dynamisch an verschiedene Bildschirmgrößen anzupassen.

## Documentation
Die `innerHeight`-Eigenschaft gehört zum `window`-Objekt und gibt die Höhe des Ansichtsfensters in Pixeln zurück, einschließlich der sichtbaren Scrollleisten, jedoch ohne die Höhe der Browser-Schnittstelle (wie z.B. Adressleiste oder Menüleiste). 

### Verwendung
Um die aktuelle Höhe des Ansichtsfensters abzurufen, kann folgende Syntax verwendet werden:

```javascript
let viewportHeight = window.innerHeight;
```

### Details
- **Typ:** Zahl (Integer)
- **Wertebereich:** Von 0 bis der maximalen Höhe des Bildschirms.
- **Änderungen:** Die `innerHeight`-Eigenschaft ändert sich dynamisch, wenn das Fenster skaliert oder die Größe ändert.

## Examples
Hier sind einige grundlegende Beispiele zur Verwendung von `innerHeight`:

### Beispiel 1: Höhe des Ansichtsfensters abrufen
```javascript
console.log("Die Höhe des Ansichtsfensters beträgt: " + window.innerHeight + " Pixel.");
```

### Beispiel 2: Dynamische Anpassung bei Fenstergröße
```javascript
window.addEventListener('resize', function() {
    console.log("Neue Höhe des Ansichtsfensters: " + window.innerHeight + " Pixel.");
});
```

### Beispiel 3: Verwendung in einer Bedingung
```javascript
if (window.innerHeight < 600) {
    console.log("Das Fenster ist zu klein für die optimale Anzeige.");
}
```

## Explanation
Ein häufiger Stolperstein beim Arbeiten mit `innerHeight` ist, dass die Höhe des Ansichtsfensters nicht immer die gleiche Höhe wie die gesamte Höhe der Webseite ist. Wenn der Inhalt der Seite größer ist als das Ansichtsfenster, wird `innerHeight` nur die Höhe des sichtbaren Bereichs zurückgeben. 

Ein weiterer Punkt, den Entwickler beachten sollten, ist, dass bei der Verwendung von `innerHeight` in Kombination mit anderen Layout-Techniken (z.B. Flexbox oder Grid) unerwartete Layout-Probleme auftreten können. Es ist ratsam, `innerHeight` nur dann zu verwenden, wenn die genaue Höhe des Ansichtsfensters erforderlich ist.

## One Line Summary
Die `innerHeight`-Eigenschaft in JavaScript gibt die Höhe des aktuellen Ansichtsfensters in Pixeln zurück und ist entscheidend für die Erstellung responsiver Designs.