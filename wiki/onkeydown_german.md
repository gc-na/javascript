<!--
Meta Description: # onkeydown: Die JavaScript-Ereignisbehandlung für Tastaturanschläge ## Synopsis Das `onkeydown`-Ereignis in JavaScript wird verwendet, um auf Tastatu...
Meta Keywords: die, event, onkeydown, das, taste
-->

# onkeydown: Die JavaScript-Ereignisbehandlung für Tastaturanschläge

## Synopsis
Das `onkeydown`-Ereignis in JavaScript wird verwendet, um auf Tastaturanschläge zu reagieren, sobald eine Taste gedrückt wird. Es ist besonders nützlich für die Entwicklung interaktiver Webanwendungen, die auf Benutzereingaben angewiesen sind.

## Dokumentation
Das `onkeydown`-Ereignis wird auf einem Element ausgelöst, wenn der Benutzer eine Taste auf der Tastatur drückt. Dieses Ereignis gehört zur Gruppe der Keyboard-Events, die auch `onkeypress` und `onkeyup` umfasst. Im Gegensatz zu `onkeypress`, das nur für druckbare Zeichen reagiert, erfasst `onkeydown` alle Tastenanschläge, einschließlich Modifier-Tasten wie Shift, Alt und Ctrl.

### Verwendung
Um das `onkeydown`-Ereignis zu verwenden, können Sie es direkt in HTML definieren oder über JavaScript hinzufügen. Hier ist die grundlegende Syntax:

```html
<input type="text" onkeydown="myFunction(event)">
```

In JavaScript kann das Ereignis wie folgt hinzugefügt werden:

```javascript
document.getElementById("myInput").onkeydown = function(event) {
    // Ihre Funktion hier
};
```

### Details
- **Ereignisobjekt**: Das `event`-Objekt, das an die Funktion übergeben wird, enthält Informationen über die gedrückte Taste. Wichtige Eigenschaften sind:
  - `event.key`: Der Wert der Taste.
  - `event.code`: Der physische Code der Taste.
  - `event.altKey`, `event.ctrlKey`, `event.shiftKey`: Boolean-Werte, die anzeigen, ob die entsprechenden Modifier-Tasten gedrückt sind.
- **Verhinderung von Standardaktionen**: Um die Standardaktion einer Taste zu verhindern (z.B. das Eingeben eines Zeichens in ein Textfeld), können Sie `event.preventDefault()` verwenden.

## Beispiele
### Beispiel 1: Grundlegende Verwendung
```html
<input type="text" id="myInput" onkeydown="alert('Eine Taste wurde gedrückt!')">
```

### Beispiel 2: Erfassung einer bestimmten Taste
```javascript
document.addEventListener('keydown', function(event) {
    if (event.key === 'Enter') {
        console.log('Die Eingabetaste wurde gedrückt!');
    }
});
```

### Beispiel 3: Verhindern der Standardaktion
```javascript
document.getElementById('myInput').onkeydown = function(event) {
    if (event.key === 'Tab') {
        event.preventDefault(); // Verhindert das Wechseln des Fokus
        alert('Tab-Taste wurde gedrückt, aber Fokuswechsel verhindert!');
    }
};
```

## Erklärung
Ein häufiges Problem bei der Verwendung von `onkeydown` ist die Verwirrung über die Unterschiede zu `onkeypress` und `onkeyup`. `onkeydown` wird ausgelöst, sobald eine Taste gedrückt wird, während `onkeyup` ausgelöst wird, wenn die Taste wieder losgelassen wird. `onkeypress` ist veraltet und sollte vermieden werden, da es nicht alle Tastenanschläge erfasst.

Eine weitere wichtige Anmerkung ist, dass das `onkeydown`-Ereignis nicht auf allen Elementen gleich funktioniert. Zum Beispiel kann es in bestimmten Kontexten (wie in Textfeldern) unerwartete Ergebnisse liefern, wenn nicht sorgfältig getestet wird.

## Ein-Satz-Zusammenfassung
Das `onkeydown`-Ereignis in JavaScript ermöglicht die Erfassung von Tastaturanschlägen und ist ein wichtiger Bestandteil der interaktiven Webentwicklung.