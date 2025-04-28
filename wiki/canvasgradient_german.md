<!--
Meta Description: # CanvasGradient in JavaScript: Eine umfassende Anleitung ## Synopsis CanvasGradient ist ein wichtiges Objekt in der HTML5-Canvas-API, das es Entwickl...
Meta Keywords: canvas, die, ein, canvasgradient, ist
-->

# CanvasGradient in JavaScript: Eine umfassende Anleitung

## Synopsis
CanvasGradient ist ein wichtiges Objekt in der HTML5-Canvas-API, das es Entwicklern ermöglicht, Farbverläufe in 2D-Grafiken zu erstellen. Es wird häufig verwendet, um visuell ansprechende Hintergründe und Formen zu gestalten.

## Documentation
CanvasGradient ist ein Teil des 2D-Kontextes des HTML5-Canvas-Elements. Es bietet eine Möglichkeit, Farbverläufe zu definieren, die dann auf Formen und Text angewendet werden können. Es gibt zwei Haupttypen von Farbverläufen, die mit CanvasGradient erstellt werden können: lineare und radiale Farbverläufe.

### Verwendung
Um ein CanvasGradient-Objekt zu erstellen, müssen Sie zuerst den 2D-Kontext eines Canvas-Elements abrufen. Danach können Sie die Methoden `createLinearGradient` oder `createRadialGradient` verwenden, um einen Farbverlauf zu erstellen.

#### Methoden:
- **createLinearGradient(x0, y0, x1, y1)**: Erstellt einen linearen Farbverlauf zwischen zwei Punkten.
- **createRadialGradient(x0, y0, r0, x1, y1, r1)**: Erstellt einen radialen Farbverlauf zwischen zwei Kreisen.

#### Farbdefinition
Sobald ein Farbverlauf erstellt ist, können Sie Farben hinzufügen, indem Sie die Methode `addColorStop(offset, color)` verwenden, wobei `offset` ein Wert zwischen 0 und 1 ist, der angibt, wo die Farbe im Verlauf angewendet wird.

### Beispiel
Hier ist ein einfaches Beispiel, wie man ein CanvasGradient in einem HTML-Canvas verwendet:

```html
<canvas id="myCanvas" width="400" height="400"></canvas>
<script>
  var canvas = document.getElementById("myCanvas");
  var ctx = canvas.getContext("2d");

  // Erstellen eines linearen Farbverlaufs
  var gradient = ctx.createLinearGradient(0, 0, 200, 0);
  gradient.addColorStop(0, "red");
  gradient.addColorStop(1, "blue");

  // Anwenden des Farbverlaufs
  ctx.fillStyle = gradient;
  ctx.fillRect(10, 10, 200, 100);
</script>
```

## Explanation
Ein häufiger Fehler beim Arbeiten mit CanvasGradient ist die falsche Verwendung der `addColorStop`-Methode. Stellen Sie sicher, dass die `offset`-Werte zwischen 0 und 1 liegen. Ein weiterer Punkt zur Beachtung ist die Reihenfolge der Farben; die erste Farbe wird an der Position 0 angezeigt, während die letzte Farbe an der Position 1 angezeigt wird.

Zusätzlich ist es wichtig zu beachten, dass Farbverläufe nur innerhalb des Canvas-Elements sichtbar sind. Wenn Sie den Canvas in eine andere Dimension ändern, kann dies die Darstellung des Farbverlaufs beeinflussen.

## One Line Summary
CanvasGradient in JavaScript ermöglicht das Erstellen von ansprechenden Farbverläufen für 2D-Grafiken im HTML5-Canvas.