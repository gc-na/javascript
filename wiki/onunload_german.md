<!--
Meta Description: # JavaScript `onunload`: Ereignis beim Verlassen der Seite ## Synopsis Das `onunload`-Ereignis in JavaScript wird ausgelöst, wenn ein Benutzer eine We...
Meta Keywords: onunload, das, seite, ereignis, verlassen
-->

# JavaScript `onunload`: Ereignis beim Verlassen der Seite

## Synopsis
Das `onunload`-Ereignis in JavaScript wird ausgelöst, wenn ein Benutzer eine Webseite verlässt, sei es durch das Schließen des Browsers, das Navigieren zu einer anderen Seite oder das Neuladen der aktuellen Seite. Es ermöglicht Entwicklern, bestimmte Aktionen durchzuführen, bevor die Seite verlassen wird.

## Dokumentation
### Zweck
Das `onunload`-Ereignis ist nützlich, um Aufgaben wie das Speichern von Benutzerdaten, das Senden von Analysedaten oder das Bestätigen von Benutzeraktionen durchzuführen, bevor die Seite geschlossen oder gewechselt wird.

### Verwendung
Das `onunload`-Ereignis kann in HTML-Elementen, in `<body>`-Tags oder direkt im JavaScript-Code verwendet werden. Es wird häufig in Verbindung mit dem `window`-Objekt eingesetzt.

#### Syntax
```javascript
window.onunload = function(event) {
    // Code, der beim Verlassen der Seite ausgeführt werden soll
};
```

### Details
- Das `onunload`-Ereignis wird nicht ausgelöst, wenn die Seite durch einen Seitenwechsel oder eine Neuladen-Aktion aktualisiert wird.
- Es ist wichtig zu beachten, dass moderne Browser Einschränkungen für einige Funktionen während des `onunload`-Ereignisses haben, um die Benutzererfahrung zu verbessern und Missbrauch zu verhindern.

## Beispiele
### Beispiel 1: Einfaches `onunload`-Ereignis
```html
<!DOCTYPE html>
<html>
<head>
    <title>onunload Beispiel</title>
    <script>
        window.onunload = function() {
            console.log("Die Seite wird verlassen.");
        };
    </script>
</head>
<body>
    <h1>Willkommen auf meiner Webseite!</h1>
</body>
</html>
```

### Beispiel 2: Bestätigung vor dem Verlassen
```html
<!DOCTYPE html>
<html>
<head>
    <title>Bestätigung beim Verlassen</title>
    <script>
        window.onbeforeunload = function() {
            return "Sind Sie sicher, dass Sie die Seite verlassen möchten?";
        };
    </script>
</head>
<body>
    <h1>Verlassen Sie diese Seite?</h1>
</body>
</html>
```

## Erklärung
### Häufige Fallstricke
- **Browserunterstützung**: Einige Browser unterstützen das `onunload`-Ereignis nicht vollständig oder haben eingeschränkte Funktionen. Beispielsweise kann das Anzeigen von Dialogen beim Verlassen der Seite in vielen modernen Browsern nicht mehr funktionieren.
- **Performance**: Zu viele und komplexe Operationen im `onunload`-Ereignis können die Ladegeschwindigkeit der Seite negativ beeinflussen.
- **Verhalten bei Neuladen**: Das `onunload`-Ereignis wird nicht ausgelöst, wenn die Seite durch Neuladen aktualisiert wird. Stattdessen sollte `onbeforeunload` verwendet werden, um den Benutzer vor dem Verlassen zu warnen.

## Einzeiler Zusammenfassung
Das `onunload`-Ereignis in JavaScript ermöglicht es Entwicklern, Aktionen auszuführen, wenn ein Benutzer die Webseite verlässt.