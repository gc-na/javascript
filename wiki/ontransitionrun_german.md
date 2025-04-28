<!--
Meta Description: # ontransitionrun: Ereignis in JavaScript zur Überwachung von CSS-Übergängen ## Synopsis Das `ontransitionrun`-Ereignis in JavaScript ermöglicht Entwi...
Meta Keywords: ereignis, das, die, ontransitionrun, übergang
-->

# ontransitionrun: Ereignis in JavaScript zur Überwachung von CSS-Übergängen

## Synopsis
Das `ontransitionrun`-Ereignis in JavaScript ermöglicht Entwicklern, Aktionen auszuführen, wenn ein CSS-Übergang beginnt. Es ist ein wichtiges Werkzeug zur Verbesserung der Benutzererfahrung, indem es visuelles Feedback bei Übergängen bietet.

## Documentation
Das `ontransitionrun`-Ereignis wird ausgelöst, wenn ein CSS-Übergang beginnt. Dieses Ereignis gehört zu einer Reihe von Übergangsevents, die es Entwicklern ermöglichen, auf Änderungen in der CSS-Animation zu reagieren. Es wird häufig in Verbindung mit `transitionend` verwendet, um den vollständigen Ablauf eines Übergangs zu steuern.

### Verwendung
Um das `ontransitionrun`-Ereignis zu verwenden, müssen Sie einen Event-Listener an ein HTML-Element anhängen. Hier ist die grundlegende Struktur:

```javascript
element.addEventListener('transitionrun', function(event) {
    // Aktionen, die ausgeführt werden sollen, wenn der Übergang beginnt
});
```

### Details
- **Event-Objekt**: Das `event`-Objekt enthält Informationen über den Übergang, einschließlich der Eigenschaft, die geändert wird.
- **Browser-Unterstützung**: Das `ontransitionrun`-Ereignis wird von modernen Browsern unterstützt, jedoch sollte die Unterstützung für ältere Versionen überprüft werden.
- **Performance**: Es wird empfohlen, das Ereignis für kleinere Animationen zu verwenden, um die Leistung der Anwendung nicht zu beeinträchtigen.

## Examples
Hier sind einige grundlegende Beispiele für die Verwendung des `ontransitionrun`-Ereignisses:

### Beispiel 1: Einfache Nutzung
```html
<div id="myElement" style="width:100px; height:100px; background-color:red; transition: background-color 2s;"></div>
<script>
    const element = document.getElementById('myElement');
    
    element.addEventListener('transitionrun', function(event) {
        console.log('Übergang läuft für:', event.propertyName);
    });

    // Start des Übergangs
    element.style.backgroundColor = 'blue';
</script>
```

### Beispiel 2: Mehrere Übergänge überwachen
```html
<div id="box" style="width:100px; height:100px; background-color:green; transition: all 1s;"></div>
<script>
    const box = document.getElementById('box');

    box.addEventListener('transitionrun', function(event) {
        console.log('Übergang läuft für:', event.propertyName);
    });

    // Start des Übergangs
    box.style.transform = 'scale(1.5)';
</script>
```

## Explanation
Ein häufiger Fehler beim Arbeiten mit dem `ontransitionrun`-Ereignis ist das Vergessen, sowohl das CSS-Übergangsverhalten als auch das JavaScript-Ereignis zu synchronisieren. Es ist wichtig sicherzustellen, dass der CSS-Übergang korrekt definiert ist, damit das Ereignis tatsächlich ausgelöst wird. Darüber hinaus sollten Entwickler darauf achten, dass die Leistung nicht beeinträchtigt wird, wenn viele Übergänge gleichzeitig überwacht werden.

## One Line Summary
Das `ontransitionrun`-Ereignis in JavaScript ermöglicht es Entwicklern, Aktionen zu initiieren, wenn ein CSS-Übergang beginnt, und verbessert so die Benutzererfahrung.