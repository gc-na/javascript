<!--
Meta Description: # JavaScript onload: Ein umfassender Leitfaden zur Verwendung des onload-Ereignisses ## Synopsis Das `onload`-Ereignis in JavaScript ermöglicht das Au...
Meta Keywords: onload, html, die, das, javascript
-->

# JavaScript onload: Ein umfassender Leitfaden zur Verwendung des onload-Ereignisses

## Synopsis
Das `onload`-Ereignis in JavaScript ermöglicht das Ausführen von Code, sobald eine Webseite vollständig geladen ist. Dies ist besonders nützlich, um sicherzustellen, dass alle DOM-Elemente und Ressourcen verfügbar sind, bevor Skripte ausgeführt werden.

## Dokumentation
Das `onload`-Ereignis wird häufig verwendet, um sicherzustellen, dass der gesamte Inhalt einer Webseite vollständig geladen ist, bevor JavaScript-Code ausgeführt wird. Es kann sowohl auf das `window`-Objekt als auch auf einzelne HTML-Elemente angewendet werden.

### Zweck
Das Hauptziel des `onload`-Ereignisses ist es, den Programmierer in die Lage zu versetzen, Skripte zu steuern, die von der vollständigen Verfügbarkeit von Ressourcen abhängen. Dies schließt Bilder, Skripte, Stylesheets und andere Medien ein.

### Verwendung
Um das `onload`-Ereignis zu verwenden, können Sie es entweder als HTML-Attribut in einem Tag oder in JavaScript definieren. Hier sind die zwei Hauptmethoden:

1. **HTML-Attribut**:
   ```html
   <body onload="myFunction()">
   ```
   
2. **JavaScript**:
   ```javascript
   window.onload = function() {
       myFunction();
   };
   ```

### Details
- Das `onload`-Ereignis wird ausgelöst, nachdem die gesamte Webseite, einschließlich aller Abhängigkeiten, geladen ist.
- Mehrere `onload`-Handler können nur durch Zuweisung an eine Funktion überschrieben werden. Wenn Sie mehrere Funktionen ausführen möchten, sollten Sie sie in einer einzigen Funktion zusammenfassen oder `addEventListener` verwenden.

## Beispiele

### Beispiel 1: Verwendung von onload im HTML-Tag
```html
<!DOCTYPE html>
<html>
<head>
    <title>Beispiel für onload</title>
    <script>
        function myFunction() {
            alert("Die Seite ist vollständig geladen!");
        }
    </script>
</head>
<body onload="myFunction()">
    <h1>Willkommen auf meiner Webseite!</h1>
</body>
</html>
```

### Beispiel 2: Verwendung von onload mit JavaScript
```html
<!DOCTYPE html>
<html>
<head>
    <title>Beispiel für onload</title>
    <script>
        function myFunction() {
            console.log("Die Seite ist vollständig geladen!");
        }
        
        window.onload = myFunction;
    </script>
</head>
<body>
    <h1>Willkommen auf meiner Webseite!</h1>
</body>
</html>
```

## Erklärung
Beim Arbeiten mit `onload` gibt es einige häufige Fallstricke, die Sie beachten sollten:
- **Zeitpunkt der Ausführung**: Das `onload`-Ereignis wird ausgelöst, nachdem alle Inhalte geladen sind, was möglicherweise länger dauert, wenn große Ressourcen geladen werden.
- **Überschreiben von Funktionen**: Wenn Sie `window.onload` mehrmals zuweisen, wird nur die letzte zugewiesene Funktion ausgeführt. Verwenden Sie `addEventListener` für mehrere Handler.
- **Ressourcenabhängigkeit**: Wenn Ihr Skript von externen Ressourcen abhängt, stellen Sie sicher, dass diese Ressourcen vor dem Laden des Skripts verfügbar sind.

## Einzeilensummary
Das `onload`-Ereignis in JavaScript ermöglicht die Ausführung von Code, sobald die gesamte Webseite vollständig geladen ist.