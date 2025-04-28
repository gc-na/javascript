<!--
Meta Description: # CustomEvent in JavaScript: Erstellen und Verwenden von benutzerdefinierten Ereignissen ## Synopsis `CustomEvent` ist eine eingebaute JavaScript-Klas...
Meta Keywords: customevent, die, von, detail, javascript
-->

# CustomEvent in JavaScript: Erstellen und Verwenden von benutzerdefinierten Ereignissen

## Synopsis
`CustomEvent` ist eine eingebaute JavaScript-Klasse, die es Entwicklern ermöglicht, benutzerdefinierte Ereignisse zu erstellen und zu verwalten. Diese Funktionalität ist besonders nützlich, um die Interaktivität und Flexibilität von Webanwendungen zu erhöhen.

## Dokumentation
### Zweck
`CustomEvent` ermöglicht es Entwicklern, eigene Ereignisse zu definieren, die an DOM-Elemente angehängt werden können. Dies ist nützlich, um spezifische Aktionen oder Zustandsänderungen innerhalb einer Anwendung zu kommunizieren.

### Verwendung
Um ein `CustomEvent` zu erstellen, verwenden Sie den Konstruktor `CustomEvent`. Dieser nimmt zwei Parameter:
1. `type`: Ein String, der den Namen des Ereignisses angibt.
2. `eventInitDict` (optional): Ein Objekt, das zusätzliche Eigenschaften für das Ereignis festlegt, wie z.B. `detail`, welches zusätzliche Daten enthält.

Die allgemeine Syntax lautet:
```javascript
const event = new CustomEvent('meinEreignis', {
    detail: { key: 'value' }
});
```

### Details
- **Ereignis-Listener**: Um auf ein benutzerdefiniertes Ereignis zu reagieren, verwenden Sie die Methode `addEventListener` an dem entsprechenden DOM-Element.
- **Ereignis-Dispatch**: Mit der Methode `dispatchEvent` können Sie das Ereignis auslösen und alle zugehörigen Listener benachrichtigen.

## Beispiele
### Beispiel 1: Einfache Verwendung von CustomEvent
```javascript
// Erstellen eines benutzerdefinierten Ereignisses
const meinEreignis = new CustomEvent('meinEreignis', {
    detail: { nachricht: 'Hallo Welt!' }
});

// Hinzufügen eines Event-Listeners
document.addEventListener('meinEreignis', function(e) {
    console.log(e.detail.nachricht); // gibt "Hallo Welt!" aus
});

// Auslösen des Ereignisses
document.dispatchEvent(meinEreignis);
```

### Beispiel 2: Verwendung von CustomEvent mit Daten
```javascript
const datenEreignis = new CustomEvent('datenAktualisiert', {
    detail: { id: 1, status: 'erledigt' }
});

document.addEventListener('datenAktualisiert', function(e) {
    console.log(`ID: ${e.detail.id}, Status: ${e.detail.status}`);
});

document.dispatchEvent(datenEreignis);
```

## Erklärung
- **Kompatibilität**: `CustomEvent` wird von den meisten modernen Browsern unterstützt, jedoch sollte die Verwendung in sehr alten Browsern überprüft werden.
- **Event-Bubbling**: `CustomEvent` unterstützt die Event-Bubbling-Funktionalität standardmäßig. Um dies zu deaktivieren, kann das `bubbles`-Flag im `eventInitDict` auf `false` gesetzt werden.
- **Verwirrung mit Standard-Ereignissen**: Vermeiden Sie die Verwendung von Namen, die mit bestehenden DOM-Ereignissen kollidieren, um Missverständnisse zu vermeiden.

## Ein-Satz-Zusammenfassung
`CustomEvent` ermöglicht die Erstellung und Verwaltung von benutzerdefinierten Ereignissen in JavaScript, um die Interaktivität von Webanwendungen zu verbessern.