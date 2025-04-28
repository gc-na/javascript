<!--
Meta Description: # requestAnimationFrame in JavaScript: Effiziente Animationen mit minimalem Ressourcenverbrauch ## Synopsis `requestAnimationFrame` ist eine JavaScrip...
Meta Keywords: die, requestanimationframe, animationen, ist, eine
-->

# requestAnimationFrame in JavaScript: Effiziente Animationen mit minimalem Ressourcenverbrauch

## Synopsis
`requestAnimationFrame` ist eine JavaScript-Funktion, die Entwicklern ermöglicht, Animationen effizient und flüssig zu gestalten, indem sie die Rendering-Performance des Browsers optimal nutzt. Sie synchronisiert Animationen mit dem Bildschirm-Refresh und verbessert die Benutzererfahrung.

## Dokumentation
`requestAnimationFrame` ist eine Methode des `window`-Objekts, die es Entwicklern ermöglicht, eine Callback-Funktion zu registrieren, die vor dem nächsten Neuzeichnen des Browsers ausgeführt wird. Das Hauptziel ist die Optimierung von Animationen und der damit verbundenen Performance.

### Zweck
Die Funktion ermöglicht es, Animationen zeitlich zu steuern und den Ressourcenverbrauch zu minimieren, indem sie die Anzahl der Frames, die pro Sekunde gerendert werden, an die Bildwiederholfrequenz des Displays anpasst.

### Verwendung
Die Syntax für `requestAnimationFrame` lautet:

```javascript
let requestId = window.requestAnimationFrame(callback);
```

- **callback**: Eine Funktion, die vor dem nächsten Neuzeichnen des Browsers aufgerufen wird.

Um eine Animation zu stoppen, kann die ID, die von `requestAnimationFrame` zurückgegeben wird, mit `cancelAnimationFrame` verwendet werden:

```javascript
window.cancelAnimationFrame(requestId);
```

### Details
- `requestAnimationFrame` gibt eine fortlaufende ID zurück, die zur Stornierung der Animation verwendet werden kann.
- Die Callback-Funktion erhält einen Parameter, der die aktuelle Zeit in Millisekunden angibt.
- Die Methode ist nützlich für Animationen, die auf CSS-Transitionen oder -Animationen basieren, und kann den CPU- und GPU-Verbrauch reduzieren.

## Beispiele

### Einfaches Beispiel
Hier ist ein einfaches Beispiel, das zeigt, wie `requestAnimationFrame` verwendet wird, um eine sich bewegende Box zu animieren:

```javascript
let box = document.getElementById('box');
let position = 0;

function animate() {
    position += 1; // Erhöhe die Position
    box.style.transform = `translateX(${position}px)`;
    
    if (position < window.innerWidth) {
        requestAnimationFrame(animate); // Nächster Frame
    }
}

requestAnimationFrame(animate); // Starte die Animation
```

### Verwendung mit Zeitstempel
In diesem Beispiel wird der Zeitstempel verwendet, um die Animationsgeschwindigkeit zu steuern:

```javascript
let start = null;

function step(timestamp) {
    if (!start) start = timestamp; // Startzeit merken
    const progress = timestamp - start;
    
    // Bewege das Element basierend auf der Zeit
    box.style.transform = `translateX(${Math.min(progress / 10, 200)}px)`;
    
    if (progress < 2000) { // Stoppe nach 2 Sekunden
        requestAnimationFrame(step);
    }
}

requestAnimationFrame(step); // Starte die Animation
```

## Erklärung
Ein häufiges Problem bei der Verwendung von `requestAnimationFrame` ist, dass einige Entwickler möglicherweise vergessen, die Callback-Funktion wiederholt aufzurufen, was zu ruckelnden Animationen führen kann. Es ist wichtig, sicherzustellen, dass die nächste Animation innerhalb der Callback-Funktion erneut registriert wird.

Ein weiterer Punkt ist, dass `requestAnimationFrame` nicht sofort aufgerufen wird. Es wird nur vor dem nächsten Neuzeichnen des Browsers aufgerufen, was bedeutet, dass es einen gewissen Verzögerungseffekt geben kann. Das ist jedoch vorteilhaft, da es die Framerate des Browsers berücksichtigt, was zu flüssigeren Animationen führt.

## Ein Satz Zusammenfassung
`requestAnimationFrame` ist eine effiziente Methode in JavaScript zur Erstellung von flüssigen Animationen, die die Leistung des Browsers optimal nutzt.