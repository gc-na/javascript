<!--
Meta Description: # PromiseRejectionEvent in JavaScript: Eine umfassende Anleitung ## Synopsis Der `PromiseRejectionEvent` in JavaScript ist ein Ereignis, das ausgelöst...
Meta Keywords: ein, promise, promiserejectionevent, ist, der
-->

# PromiseRejectionEvent in JavaScript: Eine umfassende Anleitung

## Synopsis
Der `PromiseRejectionEvent` in JavaScript ist ein Ereignis, das ausgelöst wird, wenn ein Promise abgelehnt wird und kein entsprechender Handler für die Ablehnung registriert ist. Es bietet Entwicklern die Möglichkeit, auf unhandled Rejections zu reagieren und diese zu protokollieren oder zu behandeln.

## Dokumentation
Der `PromiseRejectionEvent` ist ein Teil der Promise-Spezifikation in JavaScript und wird verwendet, um Fehlerbehandlungen für Promises zu implementieren. Es tritt auf, wenn ein Promise abgelehnt wird und die Ablehnung nicht durch einen `.catch()`-Handler oder ein `try...catch`-Block behandelt wird. Dieses Ereignis ermöglicht es Entwicklern, global auf unbehandelte Ablehnungen zu reagieren und kann zu einer besseren Fehlerdiagnose beitragen.

### Verwendung
Das `PromiseRejectionEvent` kann in einem `window`-Event-Listener registriert werden, um auf unhandled Rejections zu reagieren. Hier ist ein Beispiel, wie man dies umsetzt:

```javascript
window.addEventListener('unhandledrejection', function(event) {
    console.error('Unhandled promise rejection:', event.reason);
});
```

### Details
- **Event Typ**: `PromiseRejectionEvent`
- **Ereignis-Parameter**: Das Ereignis hat einen Parameter `reason`, der den Grund der Ablehnung enthält.
- **Kompatibilität**: Das `PromiseRejectionEvent` wird in modernen Browsern unterstützt, jedoch sollten Entwickler die Kompatibilität mit älteren Versionen prüfen.

## Beispiele

### Beispiel 1: Einfache Verwendung des `PromiseRejectionEvent`
```javascript
window.addEventListener('unhandledrejection', function(event) {
    console.log('Ein unbehandelter Fehler ist aufgetreten: ', event.reason);
});

const promise = new Promise((resolve, reject) => {
    reject('Ein Fehler ist aufgetreten');
});
```

### Beispiel 2: Umgang mit mehreren Promises
```javascript
window.addEventListener('unhandledrejection', function(event) {
    console.warn('Unhandled rejection detected:', event.reason);
});

Promise.all([
    Promise.resolve(1),
    Promise.reject('Fehler bei Promise 2'),
    Promise.resolve(3)
]).catch(err => console.error('Ein Promise in der Gruppe wurde abgelehnt:', err));
```

## Erklärung
Ein häufiger Fehler im Umgang mit `PromiseRejectionEvent` ist das Ignorieren von nicht behandelten Rejections. Entwickler sollten sicherstellen, dass alle Promises entweder mit `.catch()` behandelt oder innerhalb eines `try...catch`-Blocks verwendet werden. Das globale Handling von unhandled Rejections kann zwar nützlich sein, sollte jedoch nicht als Ersatz für ordnungsgemäße Fehlerbehandlung in der Anwendung angesehen werden.

Ein weiterer Punkt ist die Performance: Das Zuhören auf unhandled Rejections kann zusätzliche Verarbeitungsressourcen in Anspruch nehmen. Daher sollte es mit Bedacht genutzt werden.

## Ein-Satz-Zusammenfassung
Der `PromiseRejectionEvent` in JavaScript ist ein Ereignis, das bei unbehandelten Promise-Ablehnungen auftritt und Entwicklern hilft, Fehler global zu erfassen und zu protokollieren.