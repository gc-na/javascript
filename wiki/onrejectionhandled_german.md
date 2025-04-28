<!--
Meta Description: # onrejectionhandled in JavaScript: Umgang mit nicht behandelten Promise-Ablehnungen ## Synopsis `onrejectionhandled` ist ein Ereignis in JavaScript, ...
Meta Keywords: onrejectionhandled, promise, ein, das, ist
-->

# onrejectionhandled in JavaScript: Umgang mit nicht behandelten Promise-Ablehnungen

## Synopsis
`onrejectionhandled` ist ein Ereignis in JavaScript, das ausgelöst wird, wenn ein Promise abgelehnt wird und ein Handler für diese Ablehnung registriert wurde. Es ermöglicht Entwicklern, besser mit Fehlern in asynchronem Code umzugehen und die Benutzererfahrung zu verbessern.

## Dokumentation
### Zweck
Das `onrejectionhandled`-Ereignis ist Teil des Promise-Managements in JavaScript. Es wird ausgelöst, wenn ein Promise abgelehnt wird und ein `rejection handler` registriert wird, nachdem die Ablehnung erfolgt ist. Dies hilft, die Überwachung und das Debugging von Fehlern in asynchronen Operationen zu optimieren.

### Verwendung
Um `onrejectionhandled` zu nutzen, kann man das globale `window`-Objekt verwenden. Das Ereignis wird ausgelöst, wenn das Promise abgelehnt wurde und ein Handler registriert wird. Hier ist die grundlegende Syntax:

```javascript
window.onrejectionhandled = function(event) {
    console.log('Ein Promise wurde abgelehnt und behandelt:', event.reason);
};
```

### Details
- `onrejectionhandled` ist ein globales Ereignis, das sowohl im Browser als auch in Node.js verfügbar ist.
- Es wird nur ausgelöst, wenn es einen zugehörigen `catch`-Handler oder `then`-Handler gibt, der die Ablehnung behandelt.
- Das Ereignis enthält Informationen über den Grund der Ablehnung, die über `event.reason` abgerufen werden kann.

## Beispiele
### Beispiel 1: Einfaches onrejectionhandled
```javascript
window.onrejectionhandled = function(event) {
    console.log('Promise abgelehnt:', event.reason);
};

const promise = new Promise((resolve, reject) => {
    reject('Fehler aufgetreten!');
});

// Registrierung des Handlers nach der Ablehnung
promise.catch(err => console.error('Fehler:', err));
```

### Beispiel 2: Verwendung mit async/await
```javascript
window.onrejectionhandled = function(event) {
    console.log('Promise abgelehnt:', event.reason);
};

async function example() {
    try {
        await Promise.reject('Ein Fehler ist aufgetreten!');
    } catch (error) {
        console.error('Fehler:', error);
    }
}

example();
```

## Erklärung
Ein häufiges Problem bei der Verwendung von Promises ist, dass nicht behandelte Ablehnungen zu unvorhersehbarem Verhalten führen können. Mit `onrejectionhandled` können Entwickler sicherstellen, dass sie über alle Ablehnungen informiert werden, die mit einem Handler bearbeitet werden.

### Häufige Fallstricke
- Stellen Sie sicher, dass der Handler für `onrejectionhandled` registriert ist, bevor die Ablehnung auftritt. Andernfalls wird das Ereignis möglicherweise nicht ausgelöst.
- Überprüfen Sie, ob Sie den Fehler in der richtigen Reihenfolge behandeln, um unerwartete Fehler zu vermeiden.

## Ein-Satz-Zusammenfassung
Das `onrejectionhandled`-Ereignis ermöglicht eine verbesserte Fehlerbehandlung in JavaScript, indem es Entwickler über behandelte Ablehnungen von Promises informiert.