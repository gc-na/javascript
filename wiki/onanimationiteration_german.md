<!--
Meta Description: # onanimationiteration in JavaScript: Ereignisse für CSS-Animationen ## Synopsis Das `onanimationiteration`-Ereignis in JavaScript ermöglicht es Entwi...
Meta Keywords: element, die, animation, onanimationiteration, das
-->

# onanimationiteration in JavaScript: Ereignisse für CSS-Animationen

## Synopsis
Das `onanimationiteration`-Ereignis in JavaScript ermöglicht es Entwicklern, auf jedes Mal zu reagieren, wenn eine CSS-Animation eine Iteration abgeschlossen hat. Es ist ein nützliches Werkzeug für die Interaktivität und das Feedback von Animationen in Webanwendungen.

## Dokumentation
Das `onanimationiteration`-Ereignis gehört zu den Ereignissen, die durch CSS-Animationen ausgelöst werden. Es wird ausgelöst, wenn eine Animation, die auf ein Element angewendet wird, eine ihrer Iterationen abgeschlossen hat. Dies geschieht, nachdem die Animation vollständig durchlaufen wurde, und bietet Entwicklern die Möglichkeit, Aktionen auszuführen oder Änderungen vorzunehmen, während die Animation fortschreitet.

### Verwendung
Um das `onanimationiteration`-Ereignis zu verwenden, müssen Sie einen Event-Listener für ein DOM-Element hinzufügen, das eine CSS-Animation hat. Hier ist die grundlegende Syntax:

```javascript
element.onanimationiteration = function() {
    // Ihr Code hier
};
```

### Details
- **Element**: Das DOM-Element, das die CSS-Animation enthält.
- **Funktion**: Die Funktion, die ausgeführt wird, wenn die Animation eine Iteration abschließt. Diese Funktion kann beliebige JavaScript-Aktionen umfassen, wie das Aktualisieren von UI-Elementen oder das Protokollieren von Informationen.

## Beispiele
Hier sind einige grundlegende Beispiele zur Verwendung von `onanimationiteration`:

### Beispiel 1: Einfaches Logging

```html
<div class="animiertes-element"></div>

<script>
const element = document.querySelector('.animiertes-element');

element.onanimationiteration = function() {
    console.log('Die Animation hat eine Iteration abgeschlossen!');
};
</script>
```

### Beispiel 2: Ändern der Hintergrundfarbe bei jeder Iteration

```html
<style>
.animiertes-element {
    width: 100px;
    height: 100px;
    background-color: red;
    animation: pulsieren 1s infinite;
}

@keyframes pulsieren {
    0% { transform: scale(1); }
    50% { transform: scale(1.2); }
    100% { transform: scale(1); }
}
</style>

<div class="animiertes-element"></div>

<script>
const element = document.querySelector('.animiertes-element');

element.onanimationiteration = function() {
    element.style.backgroundColor = element.style.backgroundColor === 'red' ? 'blue' : 'red';
};
</script>
```

## Erklärung
Ein gängiger Fehler beim Arbeiten mit `onanimationiteration` ist es, zu erwarten, dass das Ereignis nur einmal pro Animation ausgelöst wird. In Wirklichkeit wird es bei jeder Iteration der Animation ausgesprochen, was bedeutet, dass Sie sicherstellen müssen, dass Ihr Code entsprechend gestaltet ist, um unerwartete Ergebnisse zu vermeiden.

Außerdem sollten Sie beachten, dass `onanimationiteration` nur für CSS-Animationen funktioniert, die im CSS definiert sind. Inline-Animationen oder JavaScript-basierte Animationen können dieses Ereignis nicht auslösen.

## Einzeiler Zusammenfassung
Das `onanimationiteration`-Ereignis in JavaScript ermöglicht Entwicklern, auf jede abgeschlossene Iteration einer CSS-Animation zu reagieren und bietet so eine dynamische Interaktivität in Webanwendungen.