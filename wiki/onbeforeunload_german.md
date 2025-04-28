<!--
Meta Description: # JavaScript onbeforeunload: Warnen vor dem Verlassen der Seite ## Synopsis Die `onbeforeunload`-Ereignisbindung in JavaScript ermöglicht es Entwickle...
Meta Keywords: die, onbeforeunload, sie, javascript, eine
-->

# JavaScript onbeforeunload: Warnen vor dem Verlassen der Seite

## Synopsis
Die `onbeforeunload`-Ereignisbindung in JavaScript ermöglicht es Entwicklern, Benutzer zu warnen, wenn sie versuchen, eine Webseite zu verlassen oder neu zu laden. Dies ist besonders nützlich, um den Verlust ungespeicherter Daten zu verhindern.

## Dokumentation
### Zweck
Das `onbeforeunload`-Ereignis wird ausgelöst, bevor das Dokument oder das Fenster entladen wird. Es gibt Entwicklern die Möglichkeit, eine Warnmeldung anzuzeigen, die den Benutzer darauf hinweist, dass er die Seite verlässt. Dies ist besonders wichtig in Anwendungen, in denen Benutzer Daten eingeben, die möglicherweise verloren gehen könnten.

### Verwendung
Um das `onbeforeunload`-Ereignis zu verwenden, müssen Sie einen Event-Listener für das `window`-Objekt hinzufügen. Diese Funktion sollte eine Zeichenkette zurückgeben, die die Warnmeldung enthält.

### Details
- **Syntax**: 
  ```javascript
  window.onbeforeunload = function(event) {
      return "Sind Sie sicher, dass Sie die Seite verlassen möchten?";
  };
  ```
- **Hinweis**: Die genaue Anzeige der Warnmeldung kann von den Browsern unterschiedlich behandelt werden. Viele moderne Browser zeigen eine generische Warnmeldung an und ignorieren die benutzerdefinierte Nachricht aus Sicherheitsgründen.

## Beispiele
### Einfaches Beispiel
```javascript
window.onbeforeunload = function(event) {
    return "Ihre Änderungen wurden möglicherweise nicht gespeichert.";
};
```

### Beispiel mit Bedingungen
```javascript
let isFormDirty = false;

document.querySelector('input').addEventListener('input', () => {
    isFormDirty = true;
});

window.onbeforeunload = function(event) {
    if (isFormDirty) {
        return "Sie haben ungespeicherte Änderungen. Möchten Sie die Seite wirklich verlassen?";
    }
};
```

## Erklärung
- **Gemeinsame Fallstricke**: 
  - Viele Browser zeigen keine benutzerdefinierte Nachricht mehr an, sondern verwenden eine generische Warnung. Dies kann frustrierend sein, da die spezifische Warnung, die Sie festgelegt haben, nicht angezeigt wird.
  - Das `onbeforeunload`-Ereignis kann nicht in allen Kontexten verwendet werden, z. B. in Modalen oder innerhalb von iframes, je nach Browsereinstellungen und -richtlinien.
  
- **Leistung**: 
  - Vermeiden Sie es, `onbeforeunload` unnötig zu verwenden, da es die Benutzererfahrung beeinträchtigen kann, insbesondere wenn es häufig ausgelöst wird.

## Einzeilige Zusammenfassung
`onbeforeunload` in JavaScript ermöglicht es, Benutzer zu warnen, bevor sie eine Webseite verlassen, wodurch der Verlust ungespeicherter Änderungen verhindert werden kann.