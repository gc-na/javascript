<!--
Meta Description: # ontransitionend: Ereignis in JavaScript zur Behandlung von CSS-Übergängen ## Synopsis Das `ontransitionend`-Ereignis in JavaScript ermöglicht Entwic...
Meta Keywords: das, box, ereignis, css, sie
-->

# ontransitionend: Ereignis in JavaScript zur Behandlung von CSS-Übergängen

## Synopsis
Das `ontransitionend`-Ereignis in JavaScript ermöglicht Entwicklern, auf das Ende eines CSS-Übergangs zu reagieren. Dies ist besonders nützlich, um Animationen zu steuern oder nach dem Abschluss von Übergängen spezifische Logik auszuführen.

## Dokumentation
Das `ontransitionend`-Ereignis wird ausgelöst, wenn ein CSS-Übergang auf einem Element vollständig abgeschlossen ist. Es wird häufig in Kombination mit CSS-Übergängen verwendet, um die Interaktivität und Benutzerfreundlichkeit von Webseiten zu verbessern.

### Verwendung
Um das `ontransitionend`-Ereignis zu verwenden, müssen Sie einen Event-Listener an ein DOM-Element anhängen. Hier ist der grundlegende Ablauf:

1. Wählen Sie das Element aus, auf das Sie den Übergang anwenden möchten.
2. Fügen Sie einen Event-Listener für das `transitionend`-Ereignis hinzu.
3. Definieren Sie eine Funktion, die ausgeführt wird, wenn das Ereignis ausgelöst wird.

### Details
- **Ereignisname:** `transitionend`
- **Bubbles:** Ja
- **Cancelable:** Nein
- **Event-Objekt:** Das Event-Objekt enthält nützliche Informationen wie die Eigenschaft, die den Übergang ausgelöst hat, und das Ziel des Ereignisses.

## Beispiele

### Beispiel 1: Einfaches Übergangsende erfassen
```javascript
const box = document.querySelector('.box');

box.addEventListener('transitionend', () => {
    console.log('Der Übergang ist beendet!');
});

// CSS für den Übergang
box.style.transition = 'opacity 2s';
box.style.opacity = '0';
```

### Beispiel 2: Übergangsart erfassen
```javascript
const box = document.querySelector('.box');

box.addEventListener('transitionend', (event) => {
    if (event.propertyName === 'opacity') {
        console.log('Der Opazitätsübergang ist abgeschlossen!');
    }
});

// CSS für den Übergang
box.style.transition = 'opacity 2s, transform 2s';
box.style.opacity = '0';
```

## Erklärung
Ein häufiges Problem beim Umgang mit dem `ontransitionend`-Ereignis ist, dass es mehrmals ausgelöst werden kann, wenn mehrere CSS-Eigenschaften gleichzeitig übergangen werden. Dies kann zu unerwartetem Verhalten führen. Um dies zu vermeiden, sollten Sie immer die `propertyName`-Eigenschaft des Ereignisobjekts überprüfen, um sicherzustellen, dass Sie nur auf das spezifische Übergangsende reagieren, das Sie erwarten.

Ein weiterer Hinweis ist, dass das `transitionend`-Ereignis möglicherweise nicht ausgelöst wird, wenn der Übergang vorzeitig abgebrochen wird, beispielsweise durch eine Änderung der CSS-Eigenschaften während des Übergangs.

## Ein-Satz-Zusammenfassung
Das `ontransitionend`-Ereignis in JavaScript ermöglicht Entwicklern, auf den Abschluss von CSS-Übergängen zu reagieren und damit die Interaktivität von Webseiten zu verbessern.