<!--
Meta Description: # MediaQueryListEvent in JavaScript: Eine umfassende Anleitung ## Synopsis Der `MediaQueryListEvent` ist ein Ereignistyp in JavaScript, der es Entwick...
Meta Keywords: media, die, ist, mediaquerylistevent, query
-->

# MediaQueryListEvent in JavaScript: Eine umfassende Anleitung

## Synopsis
Der `MediaQueryListEvent` ist ein Ereignistyp in JavaScript, der es Entwicklern ermöglicht, auf Änderungen von Media Queries zu reagieren. Dies ist besonders nützlich für responsive Designs, bei denen das Layout und Verhalten einer Webseite je nach Bildschirmgröße oder -ausrichtung variieren.

## Dokumentation
### Zweck
`MediaQueryListEvent` wird verwendet, um Änderungen an einer Media Query zu erkennen. Es ist Teil der `Window.matchMedia()`-API und wird ausgelöst, wenn sich die Übereinstimmung einer Media Query ändert.

### Verwendung
Um `MediaQueryListEvent` zu nutzen, müssen Sie zuerst eine Media Query mit `window.matchMedia()` erstellen. Anschließend können Sie einen Listener für Änderungen an dieser Media Query hinzufügen, um auf das `MediaQueryListEvent` zu reagieren.

### Details
- **Eigenschaft `matches`**: Diese Eigenschaft gibt zurück, ob die Media Query zum aktuellen Viewport passt (`true`) oder nicht (`false`).
- **Eigenschaft `media`**: Diese Eigenschaft gibt die Media Query zurück, die an das `MediaQueryList`-Objekt gebunden ist.
- **Ereignis**: Das `MediaQueryListEvent`-Ereignis wird ausgelöst, wenn die Übereinstimmung der Media Query wechselt. Dies geschieht beispielsweise bei einer Änderung der Fenstergröße.

## Beispiele
### Beispiel 1: Einfache Verwendung von `MediaQueryListEvent`

```javascript
// Definieren einer Media Query
const mediaQueryList = window.matchMedia('(max-width: 600px)');

// Funktion, die bei Änderungen aufgerufen wird
function handleMediaChange(event) {
    if (event.matches) {
        console.log('Das Viewport ist jetzt kleiner als 600px.');
    } else {
        console.log('Das Viewport ist jetzt größer als 600px.');
    }
}

// Initiale Überprüfung der Media Query
handleMediaChange(mediaQueryList);

// Hinzufügen eines Event Listeners
mediaQueryList.addEventListener('change', handleMediaChange);
```

### Beispiel 2: Verwendung mit CSS-Klassen

```javascript
const mediaQueryList = window.matchMedia('(prefers-color-scheme: dark)');

function updateTheme(event) {
    if (event.matches) {
        document.body.classList.add('dark-theme');
    } else {
        document.body.classList.remove('dark-theme');
    }
}

updateTheme(mediaQueryList);
mediaQueryList.addEventListener('change', updateTheme);
```

## Erklärung
Ein häufiger Stolperstein bei der Verwendung von `MediaQueryListEvent` ist das Vergessen, den Event Listener zu entfernen, wenn er nicht mehr benötigt wird, was zu Speicherlecks führen kann. Achten Sie darauf, den Listener zu entfernen, wenn die Komponente, die ihn verwendet, unmontiert wird oder nicht mehr relevant ist.

Ein weiterer Punkt ist, dass die Unterstützung für `addEventListener` auf `MediaQueryList` in älteren Browsern möglicherweise nicht vorhanden ist. In solchen Fällen kann die Methode `addListener` verwendet werden, um denselben Effekt zu erzielen, jedoch ist die Verwendung von `addEventListener` die modernere und empfohlene Methode.

## Ein-Satz-Zusammenfassung
`MediaQueryListEvent` in JavaScript ermöglicht Entwicklern, auf Änderungen von Media Queries zu reagieren und dadurch dynamisch auf verschiedene Bildschirmgrößen oder -einstellungen zu reagieren.