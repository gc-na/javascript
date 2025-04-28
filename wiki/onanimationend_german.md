<!--
Meta Description: # onanimationend in JavaScript: Ein umfassender Leitfaden ## Synopsis Das `onanimationend`-Event in JavaScript ermöglicht Entwicklern, eine Funktion a...
Meta Keywords: das, event, animation, onanimationend, die
-->

# onanimationend in JavaScript: Ein umfassender Leitfaden

## Synopsis
Das `onanimationend`-Event in JavaScript ermöglicht Entwicklern, eine Funktion auszuführen, wenn eine CSS-Animation auf einem Element abgeschlossen ist. Dieses Event ist besonders nützlich, um auf die Beendigung von Animationen zu reagieren und interaktive Benutzererlebnisse zu schaffen.

## Dokumentation
Das `onanimationend`-Event gehört zur Gruppe der Animationsevents in JavaScript. Es wird ausgelöst, wenn eine CSS-Animation auf ein Element endet. Mit diesem Event können Entwickler wichtige Aktionen durchführen, wie das Entfernen von Klassen, das Starten neuer Animationen oder das Aktualisieren von Benutzeroberflächen.

### Verwendung
Um das `onanimationend`-Event zu verwenden, müssen Sie einen Event-Listener an ein DOM-Element anhängen. Die Syntax sieht folgendermaßen aus:

```javascript
element.onanimationend = function(event) {
    // Code, der ausgeführt werden soll, wenn die Animation endet
};
```

### Details
- **Event-Objekt**: Das Event-Objekt enthält Informationen über die Animation, einschließlich des Namens der Animation und des Ziel-Elements.
- **Browser-Unterstützung**: `onanimationend` wird von modernen Browsern unterstützt. Für ältere Browser können Polyfills erforderlich sein.
- **Animationen**: Stellen Sie sicher, dass die Animation korrekt im CSS definiert ist, um das Event auszulösen.

## Beispiele

### Beispiel 1: Einfaches onanimationend-Event

```html
<div id="myElement" class="animated"></div>

<style>
.animated {
    animation: fadeOut 2s;
}

@keyframes fadeOut {
    from { opacity: 1; }
    to { opacity: 0; }
}
</style>

<script>
const element = document.getElementById('myElement');
element.onanimationend = function() {
    console.log('Animation beendet!');
};
</script>
```

### Beispiel 2: Verwendung mit mehreren Animationen

```html
<div id="box" class="box"></div>

<style>
.box {
    width: 100px;
    height: 100px;
    background-color: red;
    animation: move 2s forwards;
}

@keyframes move {
    from { transform: translateX(0); }
    to { transform: translateX(200px); }
}
</style>

<script>
const box = document.getElementById('box');
box.onanimationend = function() {
    box.style.backgroundColor = 'green';
    console.log('Die Bewegung ist abgeschlossen.');
};
</script>
```

## Erklärung
Ein häufiger Fehler beim Arbeiten mit `onanimationend` ist, dass die Animation möglicherweise nicht richtig definiert ist. Stellen Sie sicher, dass:
- Die CSS-Animation korrekt in den Stylesheets definiert ist.
- Das Element, auf das Sie das Event anwenden, tatsächlich animiert wird.
- Sie das Event nicht vorzeitig entfernen oder überschreiben, bevor die Animation beendet ist.

Ein weiterer Punkt ist die Browserkompatibilität. Während die meisten modernen Browser `onanimationend` unterstützen, sollten Sie sicherstellen, dass Ihre Anwendung auch in älteren Browsern funktioniert, falls dies erforderlich ist.

## Einzeiler Zusammenfassung
Das `onanimationend`-Event in JavaScript ermöglicht es Entwicklern, auf das Ende einer CSS-Animation zu reagieren und entsprechende Aktionen durchzuführen.