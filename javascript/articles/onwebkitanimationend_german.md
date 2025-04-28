<!--
Meta Description: # onwebkitanimationend: Ereignis für den Abschluss von CSS-Animationen in JavaScript ## Synopsis Das `onwebkitanimationend`-Ereignis in JavaScript erm...
Meta Keywords: das, ist, onwebkitanimationend, ereignis, event
-->

# onwebkitanimationend: Ereignis für den Abschluss von CSS-Animationen in JavaScript

## Synopsis
Das `onwebkitanimationend`-Ereignis in JavaScript ermöglicht Entwicklern, auf das Ende einer CSS-Animation zu reagieren, die mit der `@keyframes`-Regel definiert wurde. Es wird häufig verwendet, um Animationen dynamisch zu steuern und Benutzerinteraktionen zu verbessern.

## Dokumentation
### Zweck
Das `onwebkitanimationend`-Ereignis wird ausgelöst, wenn eine CSS-Animation, die mit dem `-webkit-` Präfix definiert ist, vollständig abgeschlossen ist. Es ist insbesondere relevant für Webkit-basierte Browser, wie Safari und frühe Versionen von Chrome.

### Verwendung
Um das `onwebkitanimationend`-Ereignis zu verwenden, müssen Sie einen Event-Listener für das Ziel-Element hinzufügen. Dies geschieht typischerweise in JavaScript, nachdem das Element im DOM geladen ist.

### Details
- **Syntax:** `element.onwebkitanimationend = function(event) { /* Ihre Logik hier */ };`
- **Parameter:** Das `event`-Objekt enthält Informationen über das ausgelöste Ereignis, einschließlich der Animation, die beendet wurde.
- **Kompatibilität:** Das `onwebkitanimationend`-Ereignis ist spezifisch für WebKit-basierte Browser und sollte mit anderen events wie `animationend` kombiniert werden, um die Kompatibilität mit anderen Browsern zu gewährleisten.

## Beispiele
### Beispiel 1: Einfaches Animation End Event
```javascript
const element = document.getElementById('myElement');

element.onwebkitanimationend = function(event) {
    console.log('Die Animation ist beendet:', event.animationName);
};
```

### Beispiel 2: Kombination mit `animationend`
```javascript
const element = document.getElementById('myElement');

element.onanimationend = function(event) {
    console.log('Die Animation ist beendet:', event.animationName);
};

element.onwebkitanimationend = function(event) {
    console.log('Die WebKit Animation ist beendet:', event.animationName);
};
```

## Erklärung
Ein häufiges Problem bei der Verwendung von `onwebkitanimationend` ist die Browserkompatibilität. Da dieses Ereignis nur in WebKit-Browsern unterstützt wird, sollten Entwickler sicherstellen, dass sie auch das standardisierte `animationend`-Ereignis für andere Browser verwenden. Ein weiteres Problem kann auftreten, wenn die Animation nicht korrekt definiert ist oder nicht im richtigen Zustand ist, um das Ereignis auszulösen.

## One Line Summary
Das `onwebkitanimationend`-Ereignis in JavaScript ermöglicht es Entwicklern, auf das Ende einer CSS-Animation in WebKit-Browsern zu reagieren.