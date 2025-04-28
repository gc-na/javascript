<!--
Meta Description: # onunhandledrejection: Umgang mit nicht behandelten Promise-Ablehnungen in JavaScript ## Synopsis `onunhandledrejection` ist ein globales Ereignis in...
Meta Keywords: onunhandledrejection, nicht, das, wird, promise
-->

# onunhandledrejection: Umgang mit nicht behandelten Promise-Ablehnungen in JavaScript

## Synopsis
`onunhandledrejection` ist ein globales Ereignis in JavaScript, das aufgerufen wird, wenn ein Promise abgelehnt wird und diese Ablehnung nicht behandelt wird. Es ermöglicht Entwicklern, nicht behandelte Promise-Ablehnungen zu erkennen und darauf zu reagieren.

## Dokumentation
Das `onunhandledrejection`-Ereignis wird vom JavaScript-Laufzeitsystem ausgelöst, wenn ein Promise abgelehnt wird und es keinen entsprechenden `catch`-Block gibt, um die Ablehnung zu behandeln. Diese Funktion ist besonders nützlich, um potenzielle Fehlerquellen zu identifizieren und zu protokollieren, sowie um das Nutzererlebnis zu verbessern, indem man dem Benutzer hilfreiche Fehlermeldungen anzeigt.

### Verwendung
Um das `onunhandledrejection`-Ereignis zu verwenden, können Sie einen Event-Listener im globalen Kontext hinzufügen:

```javascript
window.onunhandledrejection = function(event) {
    console.error('Nicht behandelte Ablehnung:', event.reason);
};
```

In diesem Beispiel wird eine Fehlermeldung in der Konsole ausgegeben, wenn eine nicht behandelte Ablehnung auftritt.

### Details
- **Ereignis-Objekt**: Das Ereignisobjekt, das an den Handler übergeben wird, enthält eine `reason`-Eigenschaft, die den Grund für die Ablehnung des Promise angibt.
- **Kompatibilität**: `onunhandledrejection` wird von den meisten modernen Browsern unterstützt, einschließlich Chrome, Firefox und Edge. Internet Explorer unterstützt diese Funktion nicht.

## Beispiele
Hier sind einige einfache Beispiele zur Veranschaulichung der Verwendung von `onunhandledrejection`:

### Beispiel 1: Einfaches Promise ohne Behandlung
```javascript
const myPromise = new Promise((resolve, reject) => {
    reject('Etwas ist schiefgelaufen!');
});

window.onunhandledrejection = function(event) {
    console.error('Nicht behandelte Ablehnung:', event.reason);
};
```

### Beispiel 2: Behandlung mit `catch`
```javascript
const myPromise = new Promise((resolve, reject) => {
    reject('Ein Fehler ist aufgetreten!');
});

myPromise.catch(error => {
    console.log('Fehler behandelt:', error);
});
```
In diesem Beispiel wird die Ablehnung behandelt, und das `onunhandledrejection`-Ereignis wird nicht ausgelöst.

## Erklärung
Ein häufiges Problem bei der Verwendung von Promises ist das Vergessen, einen `catch`-Block hinzuzufügen. Dies führt dazu, dass unbehandelte Ablehnungen auftreten, die zu unerwarteten Fehlern und einem schlechten Nutzererlebnis führen können. Durch die Verwendung von `onunhandledrejection` können Entwickler diese Fälle identifizieren und geeignete Maßnahmen ergreifen.

Ein weiterer Punkt ist, dass das `onunhandledrejection`-Ereignis nicht nur in der Konsole protokolliert werden sollte. Es kann auch nützlich sein, den Fehler an einen Fehlerverfolgungsdienst zu senden oder dem Benutzer eine benutzerfreundliche Fehlermeldung anzuzeigen.

## Ein-Satz-Zusammenfassung
`onunhandledrejection` ist ein JavaScript-Ereignis, das es Entwicklern ermöglicht, mit nicht behandelten Promise-Ablehnungen umzugehen und potenzielle Fehlerquellen zu identifizieren.