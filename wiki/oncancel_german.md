<!--
Meta Description: # Oncancel in JavaScript: Event Handling für Abbrüche ## Synopsis Die `oncancel`-Eigenschaft in JavaScript ermöglicht Entwicklern, auf Abbruchereignis...
Meta Keywords: die, signal, oncancel, controller, ist
-->

# Oncancel in JavaScript: Event Handling für Abbrüche

## Synopsis
Die `oncancel`-Eigenschaft in JavaScript ermöglicht Entwicklern, auf Abbruchereignisse zu reagieren. Diese Funktion ist besonders nützlich in Kombination mit der `AbortController`-API, die das Abbrechen von asynchronen Operationen ermöglicht.

## Dokumentation
### Zweck
Die `oncancel`-Eigenschaft wird verwendet, um eine Callback-Funktion festzulegen, die ausgeführt wird, wenn eine Abbruchbedingung erfüllt ist. Dies ist besonders relevant in Situationen, in denen eine asynchrone Aufgabe, wie ein Netzwerkaufruf oder eine Animation, vorzeitig beendet werden muss.

### Verwendung
Um `oncancel` zu verwenden, müssen Sie zuerst einen `AbortController` erstellen. Anschließend können Sie die `signal`-Eigenschaft des Controllers verwenden, um Abbruchereignisse zu überwachen. Die `oncancel`-Eigenschaft wird auf das Signal gesetzt, um eine Funktion zu definieren, die bei Abbruch aufgerufen wird.

### Details
- **AbortController**: Ein Interface, das es ermöglicht, asynchrone Vorgänge abzubrechen.
- **AbortSignal**: Ein Signal, das den Abbruchstatus verfolgt.
- **oncancel**: Eine Callback-Funktion, die bei Abbruchereignissen ausgeführt wird.

### Syntax
```javascript
const controller = new AbortController();
const signal = controller.signal;

signal.oncancel = function() {
    console.log('Abbruchsignal empfangen.');
};

// Abbrechen der Operation
controller.abort();
```

## Beispiele
### Beispiel 1: Grundlagen der Verwendung von oncancel
```javascript
const controller = new AbortController();
const signal = controller.signal;

signal.oncancel = function() {
    console.log('Die Abbruchoperation wurde ausgelöst.');
};

// Simulation eines Abbruchs
setTimeout(() => {
    controller.abort();
}, 1000);
```

### Beispiel 2: Verwendung mit Fetch API
```javascript
const controller = new AbortController();
const signal = controller.signal;

signal.oncancel = () => {
    console.log('Fetch-Anfrage wurde abgebrochen.');
};

fetch('https://api.example.com/data', { signal })
    .then(response => response.json())
    .then(data => console.log(data))
    .catch(err => {
        if (err.name === 'AbortError') {
            console.log('Die Anfrage wurde abgebrochen.');
        } else {
            console.error('Ein Fehler ist aufgetreten:', err);
        }
    });

// Abbrechen der Anfrage
controller.abort();
```

## Erklärung
Ein häufiges Problem bei der Verwendung von `oncancel` ist, dass die Callback-Funktion möglicherweise nicht aufgerufen wird, wenn der Abbruch nicht korrekt eingerichtet ist. Stellen Sie sicher, dass der `AbortController` und das zugehörige `AbortSignal` ordnungsgemäß erstellt und verwendet werden. Darüber hinaus können Benutzer vergessen, den Abbruch tatsächlich auszulösen, was zu unerwartetem Verhalten führen kann. Es ist immer ratsam, die Fehlerbehandlung für Abbruchereignisse zu implementieren, um das Nutzererlebnis zu optimieren.

## Ein Satz Zusammenfassung
Die `oncancel`-Eigenschaft in JavaScript ermöglicht es Entwicklern, auf Abbruchereignisse zu reagieren, indem sie eine Callback-Funktion definieren, die bei einem Abbruchsignal ausgeführt wird.