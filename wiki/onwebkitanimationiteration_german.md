<!--
Meta Description: # onwebkitanimationiteration: JavaScript-Event für CSS-Animationen ## Synopsis `onwebkitanimationiteration` ist ein JavaScript-Event-Handler, der ausg...
Meta Keywords: event, onwebkitanimationiteration, das, animationen, sie
-->

# onwebkitanimationiteration: JavaScript-Event für CSS-Animationen

## Synopsis
`onwebkitanimationiteration` ist ein JavaScript-Event-Handler, der ausgelöst wird, wenn eine CSS-Animation, die mit dem WebKit-Präfix erstellt wurde, eine Iteration abgeschlossen hat. Dieses Event ermöglicht Entwicklern, spezifische Aktionen auszuführen, wenn eine Animation wiederholt wird.

## Dokumentation
### Zweck
Das `onwebkitanimationiteration`-Event ist ein Teil der WebKit-Implementierung von CSS-Animationen und wird verwendet, um Animationen zu steuern und Benutzerinteraktionen zu verbessern. Es ist besonders nützlich, wenn Sie Animationen haben, die mehrmals abgespielt werden, und Sie darauf reagieren möchten, wenn jede Iteration endet.

### Verwendung
Um `onwebkitanimationiteration` zu verwenden, müssen Sie einen Event-Listener für das entsprechende Element hinzufügen. Der Listener reagiert, wenn die Animation eine Iteration erreicht.

### Syntax
```javascript
element.onwebkitanimationiteration = function(event) {
    // Ihre Logik hier
};
```

### Parameter
- **event**: Ein Event-Objekt, das Informationen über das ausgelöste Event enthält, einschließlich der Animation, die das Event ausgelöst hat.

## Beispiele
### Einfaches Beispiel
```html
<!DOCTYPE html>
<html lang="de">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <style>
        .animiert {
            width: 100px;
            height: 100px;
            background-color: red;
            animation: pulsieren 2s infinite;
        }

        @keyframes pulsieren {
            0% { transform: scale(1); }
            50% { transform: scale(1.5); }
            100% { transform: scale(1); }
        }
    </style>
</head>
<body>
    <div class="animiert"></div>
    <script>
        const box = document.querySelector('.animiert');
        box.onwebkitanimationiteration = function() {
            console.log('Animation Iteration abgeschlossen!');
        };
    </script>
</body>
</html>
```

### Beispiel mit mehreren Animationen
```javascript
const box = document.querySelector('.animiert');
let iterationCount = 0;

box.onwebkitanimationiteration = function() {
    iterationCount++;
    console.log(`Iteration ${iterationCount} abgeschlossen!`);
};
```

## Erklärung
Ein häufiges Problem bei der Verwendung von `onwebkitanimationiteration` ist die Browserkompatibilität. Da `onwebkitanimationiteration` spezifisch für WebKit-Browser ist, sollten Entwickler auch das standardisierte `onanimationiteration`-Event verwenden, um eine breitere Unterstützung zu gewährleisten. 

### Tipps
- Nutzen Sie die standardisierte Version: Vermeiden Sie Browserprobleme, indem Sie zusätzlich das `onanimationiteration`-Event verwenden.
- Testen Sie Ihre Animationen in verschiedenen Browsern, um sicherzustellen, dass das Event überall funktioniert.

## Zusammenfassung
`onwebkitanimationiteration` ist ein nützliches JavaScript-Event, das es Entwicklern ermöglicht, auf das Ende einer Iteration von CSS-Animationen zu reagieren, insbesondere in WebKit-basierten Browsern.