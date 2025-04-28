<!--
Meta Description: # oncontextrestored: Ein Überblick über das Kontextwiederherstellungsereignis in JavaScript ## Synopsis Das `oncontextrestored` Ereignis in JavaScript...
Meta Keywords: canvas, das, des, context, oncontextrestored
-->

# oncontextrestored: Ein Überblick über das Kontextwiederherstellungsereignis in JavaScript

## Synopsis
Das `oncontextrestored` Ereignis in JavaScript wird verwendet, um zu erkennen, wenn der Kontext eines Canvas-Elements nach einer Unterbrechung wiederhergestellt wurde. Dies ist besonders nützlich in Anwendungen, die Grafiken oder Animationen rendern, da es Entwicklern ermöglicht, ihre Zeichnungen effizient zu verwalten.

## Dokumentation
Das `oncontextrestored` Ereignis ist Teil der HTML5 Canvas API und wird ausgelöst, wenn der Kontext eines Canvas-Elements wiederhergestellt wird, nachdem er durch einen Verlust oder eine Unterbrechung (z.B. durch das Minimieren des Fensters oder das Wechseln des Tabs) vorübergehend verloren ging. Dies geschieht in der Regel, wenn die Zeichengrafik neu gerendert werden muss, um die aktuelle Ansicht des Canvas wiederherzustellen.

### Verwendung
Um das `oncontextrestored` Ereignis zu verwenden, müssen Sie zunächst einen Canvas-Kontext erstellen und dann einen Event-Listener für das Ereignis hinzufügen. Hier ist ein einfaches Beispiel:

```javascript
const canvas = document.getElementById('myCanvas');
const context = canvas.getContext('2d');

canvas.addEventListener('contextrestored', function() {
    // Code zur Wiederherstellung des Canvas-Inhalts
    draw(); // Funktion, die die Zeichnung auf dem Canvas aktualisiert
});
```

### Details
- **Ereignisname**: `contextrestored`
- **Ereignisobjekt**: Das Ereignisobjekt enthält Informationen über das Ereignis, jedoch keine spezifischen Eigenschaften für dieses Ereignis.
- **Kompatibilität**: `oncontextrestored` ist in modernen Browsern gut unterstützt, sollte jedoch in älteren Versionen getestet werden.

## Beispiele
Hier sind einige einfache Beispiele zur Veranschaulichung der Verwendung des `oncontextrestored` Ereignisses:

### Beispiel 1: Grundlegende Verwendung
```javascript
const canvas = document.getElementById('myCanvas');
const context = canvas.getContext('2d');

function draw() {
    context.clearRect(0, 0, canvas.width, canvas.height);
    context.fillStyle = 'blue';
    context.fillRect(10, 10, 100, 100);
}

canvas.addEventListener('contextrestored', draw);

// Initiale Zeichnung
draw();
```

### Beispiel 2: Animation
```javascript
const canvas = document.getElementById('myCanvas');
const context = canvas.getContext('2d');
let x = 0;

function animate() {
    context.clearRect(0, 0, canvas.width, canvas.height);
    context.fillStyle = 'red';
    context.fillRect(x, 50, 50, 50);
    x += 1;
    requestAnimationFrame(animate);
}

canvas.addEventListener('contextrestored', animate);

// Start der Animation
animate();
```

## Erklärung
Ein häufiges Problem, das Entwickler erleben, ist das Vergessen, den Canvas-Inhalt nach einem Verlust des Kontextes zu aktualisieren. Es ist wichtig, sicherzustellen, dass alle notwendigen Grafiken neu gezeichnet werden, wenn das `oncontextrestored` Ereignis ausgelöst wird, da der vorherige Zustand des Canvas möglicherweise verloren geht. Es ist ratsam, alle Zeichenoperationen in einer separaten Funktion (z.B. `draw()`) zu kapseln, die sowohl beim Initialisieren des Canvas als auch beim Wiederherstellen des Kontexts aufgerufen wird.

## Ein Satz Zusammenfassung
Das `oncontextrestored` Ereignis in JavaScript ermöglicht die Wiederherstellung und Aktualisierung von Canvas-Inhalten, wenn der Kontext verloren geht und dann wiederhergestellt wird.