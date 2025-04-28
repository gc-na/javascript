<!--
Meta Description: # onerror in JavaScript: Fehlerbehandlung für Webanwendungen ## Synopsis Das `onerror`-Ereignis in JavaScript dient der Fehlerbehandlung in Webanwendu...
Meta Keywords: onerror, script, javascript, fehler, von
-->

# onerror in JavaScript: Fehlerbehandlung für Webanwendungen

## Synopsis
Das `onerror`-Ereignis in JavaScript dient der Fehlerbehandlung in Webanwendungen, indem es Entwicklern ermöglicht, auf Fehler im Skript oder beim Laden von Ressourcen zu reagieren.

## Documentation
Das `onerror`-Ereignis wird verwendet, um Fehler zu erfassen, die während der Ausführung von JavaScript-Code oder beim Laden von externen Ressourcen wie Bildern oder Skripten auftreten. Es bietet eine Möglichkeit, Fehler zu protokollieren und gegebenenfalls benutzerfreundliche Fehlermeldungen anzuzeigen oder alternative Maßnahmen zu ergreifen.

### Verwendung
Die Verwendung von `onerror` ist einfach und kann in verschiedenen Kontexten erfolgen:

1. **Globale Fehlerbehandlung**: Durch die Zuweisung einer Funktion an `window.onerror` können Sie Fehler, die in Ihrem gesamten Skript auftreten, zentral behandeln.
   
   ```javascript
   window.onerror = function(message, source, lineno, colno, error) {
       console.error(`Fehler: ${message} in ${source}:${lineno}:${colno}`);
   };
   ```

2. **Fehlerbehandlung für Bilder**: Sie können das `onerror`-Attribut auch direkt in HTML-Elementen verwenden, um auf Ladefehler zu reagieren.

   ```html
   <img src="image.jpg" onerror="this.onerror=null; this.src='fallback.jpg';" alt="Bild konnte nicht geladen werden">
   ```

3. **Fehlerbehandlung in Skripten**: Sie können das `onerror`-Ereignis auch für dynamisch geladene Skripte verwenden.

   ```javascript
   const script = document.createElement('script');
   script.src = 'some-script.js';
   script.onerror = function() {
       console.error('Das Skript konnte nicht geladen werden.');
   };
   document.head.appendChild(script);
   ```

## Examples
Hier sind einige grundlegende Beispiele für die Verwendung von `onerror`:

### Beispiel 1: Globale Fehlerbehandlung

```javascript
window.onerror = function(message) {
    alert(`Ein Fehler ist aufgetreten: ${message}`);
};
```

### Beispiel 2: Fehlerbehandlung für ein Bild

```html
<img src="invalid-image.jpg" onerror="this.src='default-image.jpg';" alt="Standardbild angezeigt">
```

### Beispiel 3: Fehlerhandling bei einem Script-Tag

```javascript
const script = document.createElement('script');
script.src = 'invalid-script.js';
script.onerror = function() {
    console.log('Fehler: Skript konnte nicht geladen werden.');
};
document.head.appendChild(script);
```

## Explanation
Ein häufiger Stolperstein beim Einsatz von `onerror` ist, dass Fehler im JavaScript-Code nicht immer zu einem `onerror`-Ereignis führen. Beispielsweise werden Syntaxfehler nicht erfasst. Außerdem kann das `onerror`-Ereignis in verschiedenen Browsern unterschiedlich behandelt werden, was zu Inkompatibilitäten führen kann. Es ist wichtig, die Rückgabewerte und Parameter der `onerror`-Funktion zu verstehen, um die Fehlerprotokollierung korrekt zu implementieren.

Ein weiterer Punkt ist, dass beim Setzen von `onerror` auf ein Bild oder Skript kein weiterer Fehler-Handler aufgerufen wird, wenn die Zuweisung zu `this.onerror` innerhalb der Fehlerbehandlungsfunktion erfolgt. Daher sollte diese Zuweisung sicherstellen, dass die Funktion nicht erneut aufgerufen wird.

## One Line Summary
Das `onerror`-Ereignis in JavaScript ermöglicht eine effektive Fehlerbehandlung und Protokollierung während der Ausführung von Skripten und dem Laden von Ressourcen.