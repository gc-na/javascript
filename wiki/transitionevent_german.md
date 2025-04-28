<!--
Meta Description: # TransitionEvent in JavaScript: Ein umfassender Leitfaden ## Synopsis Der `TransitionEvent` ist ein Ereignis in JavaScript, das ausgelöst wird, wenn ...
Meta Keywords: transition, die, der, transitionevent, event
-->

# TransitionEvent in JavaScript: Ein umfassender Leitfaden

## Synopsis
Der `TransitionEvent` ist ein Ereignis in JavaScript, das ausgelöst wird, wenn eine CSS-Transition abgeschlossen wird. Es ermöglicht Entwicklern, auf Übergänge zwischen Zuständen von DOM-Elementen zu reagieren und bietet eine Möglichkeit, Animationen und visuelle Effekte zu steuern.

## Dokumentation
### Zweck
`TransitionEvent` wird verwendet, um Informationen über CSS-Transitions bereitzustellen, die auf ein Element angewendet werden. Diese Ereignisse sind nützlich, um benutzerdefinierte Logik oder Animationen auszuführen, sobald eine Transition abgeschlossen oder unterbrochen wurde.

### Verwendung
Ein `TransitionEvent` wird typischerweise in Verbindung mit den CSS-Transition-Eigenschaften in einer Webanwendung verwendet. Um einen `TransitionEvent` zu verwenden, müssen Sie einen Event-Listener für den `transitionend`-Event auf ein DOM-Element registrieren.

#### Syntax
```javascript
element.addEventListener('transitionend', function(event) {
    // Logik hier
});
```

### Details
Der `TransitionEvent` enthält folgende Eigenschaften:
- `propertyName`: Der Name der CSS-Eigenschaft, die die Transition ausgelöst hat.
- `elapsedTime`: Die Zeit, die seit dem Start der Transition vergangen ist.
- `pseudoElement`: Gibt an, ob die Transition auf einem Pseudo-Element angewendet wurde.

## Beispiele
### Einfaches Beispiel
```html
<!DOCTYPE html>
<html lang="de">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <style>
        .box {
            width: 100px;
            height: 100px;
            background-color: red;
            transition: background-color 2s;
        }
        .box:hover {
            background-color: blue;
        }
    </style>
</head>
<body>
    <div class="box"></div>
    <script>
        const box = document.querySelector('.box');
        
        box.addEventListener('transitionend', (event) => {
            console.log(`Transition ended on: ${event.propertyName}`);
        });
    </script>
</body>
</html>
```

### Beispiel mit mehreren Eigenschaften
```javascript
const anotherBox = document.querySelector('.another-box');
anotherBox.addEventListener('transitionend', (event) => {
    console.log(`Transition ended for: ${event.propertyName} after ${event.elapsedTime} seconds`);
});
```

## Erklärung
Ein häufiger Fallstrick bei der Verwendung von `TransitionEvent` ist, dass mehrere Übergänge auf demselben Element gleichzeitig stattfinden können. In solchen Fällen wird das `transitionend`-Ereignis für jede betroffene CSS-Eigenschaft ausgelöst. Es ist wichtig zu prüfen, ob das `propertyName` des Ereignisses mit der erwarteten Eigenschaft übereinstimmt, um unerwünschte Reaktionen zu vermeiden.

Ein weiterer Punkt ist, dass das `transitionend`-Ereignis nicht ausgelöst wird, wenn die Transition abgebrochen wird (z. B. durch das Entfernen der Klasse, die die Transition auslöst), was in der Logik berücksichtigt werden sollte.

## Zusammenfassung in einem Satz
`TransitionEvent` in JavaScript ermöglicht es Entwicklern, auf das Ende von CSS-Transitions zu reagieren und bietet wichtige Informationen über die durchgeführten Änderungen.