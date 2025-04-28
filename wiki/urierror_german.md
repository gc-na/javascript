<!--
Meta Description: # URIError in JavaScript: Verständnis und Anwendung ## Synopsis URIError ist eine eingebaute Fehlerklasse in JavaScript, die auftritt, wenn eine ungül...
Meta Keywords: urierror, uri, ist, der, ungültige
-->

# URIError in JavaScript: Verständnis und Anwendung

## Synopsis
URIError ist eine eingebaute Fehlerklasse in JavaScript, die auftritt, wenn eine ungültige URI (Uniform Resource Identifier) verwendet wird. Diese Fehlerklasse ist besonders relevant bei der Verwendung von Funktionen zum Kodieren oder Dekodieren von URIs.

## Dokumentation
URIError ist ein von der JavaScript-Engine generierter Fehler, der auftritt, wenn eine URI-Operation fehlerhaft ist. Dies geschieht häufig bei der Verwendung der Funktionen `decodeURI()`, `decodeURIComponent()`, `encodeURI()` und `encodeURIComponent()`. Diese Funktionen dienen dazu, URIs zu kodieren oder zu dekodieren, und wenn ungültige Zeichen oder Formate verwendet werden, wird ein URIError ausgelöst.

### Zweck
Der Zweck von URIError besteht darin, Entwicklern zu signalisieren, dass eine URI nicht korrekt verarbeitet werden konnte, was häufig auf falsche Eingaben oder ungültige Zeichen zurückzuführen ist.

### Verwendung
- **decodeURI()**: Dekodiert eine kodierte URI.
- **decodeURIComponent()**: Dekodiert einen kodierten URI-Komponenten.
- **encodeURI()**: Kodiert eine URI, um sicherzustellen, dass sie in einem URL-Kontext verwendet werden kann.
- **encodeURIComponent()**: Kodiert einen URI-Komponenten und ersetzt spezielle Zeichen.

### Details
Wenn ein URIError auftritt, können Sie die Fehlermeldung abfangen und entsprechende Maßnahmen ergreifen. Der Fehler kann über einen try-catch-Block behandelt werden, um die Anwendung vor einem unerwarteten Absturz zu bewahren.

## Beispiele

### Beispiel 1: Verwendung von `decodeURI()`
```javascript
try {
    let decoded = decodeURI("http://example.com/?name=John%20Doe");
    console.log(decoded); // Ausgabe: "http://example.com/?name=John Doe"
} catch (e) {
    if (e instanceof URIError) {
        console.error("URIError: Ungültige URI");
    }
}
```

### Beispiel 2: Verwendung von `encodeURIComponent()`
```javascript
try {
    let encoded = encodeURIComponent("John Doe!");
    console.log(encoded); // Ausgabe: "John%20Doe%21"
} catch (e) {
    if (e instanceof URIError) {
        console.error("URIError: Ungültige URI-Komponente");
    }
}
```

### Beispiel 3: Auslösen eines URIError
```javascript
try {
    let faulty = decodeURIComponent("%");
} catch (e) {
    if (e instanceof URIError) {
        console.error("URIError: Ungültige URI-Komponente"); // Ausgabe: "URIError: Ungültige URI-Komponente"
    }
}
```

## Erklärung
Ein URIError tritt häufig auf, wenn Sie versuchen, eine URI zu dekodieren, die nicht ordnungsgemäß kodiert ist. Zum Beispiel werden bei der Funktion `decodeURIComponent()` zwei aufeinanderfolgende Prozentzeichen ohne gültige Hexadezimalzahlen danach als ungültig betrachtet und lösen einen Fehler aus. 

Ein weiteres häufiges Problem ist die Verwendung von `encodeURI()` für Teile einer URI, die nicht für diese Funktion bestimmt sind. Hierbei ist es wichtig, zwischen `encodeURIComponent()` und `encodeURI()` zu unterscheiden, da letztere nur bestimmte Zeichen in einer vollständigen URI kodiert.

## Einzeilige Zusammenfassung
URIError ist ein Fehler in JavaScript, der auftritt, wenn ungültige URIs in kodierenden oder dekodierenden Funktionen verwendet werden.