<!--
Meta Description: # onhashchange: Ereignisse bei Änderungen der URL-Hash in JavaScript ## Synopsis Das `onhashchange`-Event in JavaScript ermöglicht Entwicklern, auf Ve...
Meta Keywords: der, hash, onhashchange, das, event
-->

# onhashchange: Ereignisse bei Änderungen der URL-Hash in JavaScript

## Synopsis
Das `onhashchange`-Event in JavaScript ermöglicht Entwicklern, auf Veränderungen des URL-Hash-Teils zu reagieren. Dies ist besonders nützlich für Single Page Applications (SPAs), bei denen die Navigation ohne Seitenneuladen erfolgt.

## Dokumentation
### Zweck
Das `onhashchange`-Event wird ausgelöst, wenn sich der Hash-Wert der URL ändert. Der Hash-Wert ist der Teil der URL, der nach dem `#`-Symbol kommt. Mit diesem Event können Entwickler dynamisch auf Änderungen reagieren, beispielsweise um Inhalte zu laden oder die Benutzeroberfläche zu aktualisieren.

### Verwendung
Um das `onhashchange`-Event zu nutzen, muss eine Funktion definiert werden, die bei einer Änderung des Hashes aufgerufen wird. Diese Funktion kann auf das globale `window`-Objekt angewendet werden.

#### Syntax
```javascript
window.onhashchange = function() {
    // Code, der bei einer Hash-Änderung ausgeführt wird
};
```

### Details
- **Ereignisobjekt**: Bei der Auslösung des `onhashchange`-Events wird kein Ereignisobjekt übergeben. Stattdessen kann der neue Hash über `location.hash` abgerufen werden.
- **Browserunterstützung**: Das `onhashchange`-Event wird von den meisten modernen Browsern unterstützt, einschließlich Chrome, Firefox, Safari und Edge. Internet Explorer unterstützt es ab Version 8.

## Beispiele
### Einfaches Beispiel
```javascript
window.onhashchange = function() {
    console.log("Der Hash hat sich geändert! Neuer Hash: " + location.hash);
};

// Beispiel: Hash manuell ändern
location.hash = "neuerHash"; // Dies löst das onhashchange-Event aus.
```

### Anwendung in einer SPA
```javascript
window.onhashchange = function() {
    switch (location.hash) {
        case "#home":
            loadHomePage();
            break;
        case "#about":
            loadAboutPage();
            break;
        case "#contact":
            loadContactPage();
            break;
        default:
            loadDefaultPage();
    }
};

// Funktionen zum Laden der Seiten
function loadHomePage() { /* Code zum Laden der Startseite */ }
function loadAboutPage() { /* Code zum Laden der Über-Seite */ }
function loadContactPage() { /* Code zum Laden der Kontaktseite */ }
function loadDefaultPage() { /* Code zum Laden der Standardseite */ }
```

## Erklärung
### Häufige Fallstricke
- **Initialer Aufruf**: Das `onhashchange`-Event wird nicht beim ersten Laden der Seite ausgelöst. Um den aktuellen Hash beim ersten Laden zu verarbeiten, sollte eine separate Funktion aufgerufen werden.
- **Browser-Verhalten**: Bei schnellen Änderungen des Hashes (z. B. durch mehrere Klicks) kann das Event mehrfach ausgelöst werden, was zu unerwarteten Ergebnissen führen kann.

### Zusätzliche Hinweise
- Das `onhashchange`-Event ist nützlich, um den aktuellen Status der Anwendung zu speichern und den Benutzer bei der Navigation durch den Verlauf der Anwendung zu unterstützen.
- Für komplexere Anwendungen und Anforderungen an die URL-Verwaltung könnte es sinnvoll sein, ein Routing-Framework zu verwenden, das eine erweiterte Funktionalität bietet.

## Zusammenfassung in einem Satz
Das `onhashchange`-Event in JavaScript ermöglicht es Entwicklern, auf Änderungen des URL-Hashs zu reagieren und dynamische Inhalte in Webanwendungen zu aktualisieren.