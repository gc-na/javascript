<!--
Meta Description: # DocumentType in JavaScript: Eine umfassende Anleitung ## Synopsis Der `DocumentType` in JavaScript beschreibt den Dokumenttyp einer HTML- oder XML-S...
Meta Keywords: doctype, des, der, documenttype, den
-->

# DocumentType in JavaScript: Eine umfassende Anleitung

## Synopsis
Der `DocumentType` in JavaScript beschreibt den Dokumenttyp einer HTML- oder XML-Seite und wird verwendet, um den Parser über die Art des Dokuments zu informieren. Er spielt eine entscheidende Rolle bei der korrekten Interpretation und Darstellung von Inhalten im Browser.

## Documentation
### Zweck
Das `DocumentType`-Objekt ist Teil des Document Object Model (DOM) und stellt Informationen über den Document Type Declaration (DOCTYPE) bereit. Ein DOCTYPE ist erforderlich, um sicherzustellen, dass der Browser die Seite im richtigen Modus rendert. Er beeinflusst, wie HTML-Elemente interpretiert werden und welche Standards eingehalten werden.

### Verwendung
In JavaScript kann auf das `DocumentType`-Objekt über die `document.doctype`-Eigenschaft zugegriffen werden. Diese Eigenschaft gibt das `DocumentType`-Objekt des aktuellen Dokuments zurück, das grundlegende Informationen wie den Namen des DOCTYPE und die öffentliche ID enthält.

**Syntax:**
```javascript
let doctype = document.doctype;
```

### Details
Das `DocumentType`-Objekt hat folgende Eigenschaften:
- **name**: Der Name des DOCTYPE (z.B. `html`).
- **publicId**: Die öffentliche ID des DOCTYPE, falls vorhanden.
- **systemId**: Die System-ID des DOCTYPE, falls vorhanden.

## Examples
### Beispiel 1: Zugriff auf den DocumentType
```javascript
// Zugriff auf das DocumentType-Objekt
let doctype = document.doctype;

console.log(doctype.name); // Gibt den Namen des DOCTYPE aus
console.log(doctype.publicId); // Gibt die öffentliche ID aus
console.log(doctype.systemId); // Gibt die System-ID aus
```

### Beispiel 2: Überprüfung des DOCTYPE
```javascript
// Überprüfung des DOCTYPE
if (document.doctype) {
    console.log("Der DOCTYPE ist: " + document.doctype.name);
} else {
    console.log("Kein DOCTYPE vorhanden.");
}
```

## Explanation
Ein häufiger Fehler besteht darin, dass Entwickler den DOCTYPE für ihre Dokumente vergessen oder falsch angeben, was zu unerwartetem Verhalten und Darstellungsproblemen führen kann. Stellen Sie sicher, dass der DOCTYPE an der obersten Stelle der HTML-Datei steht und korrekt formuliert ist. Zum Beispiel sollte der DOCTYPE für HTML5 wie folgt aussehen:
```html
<!DOCTYPE html>
```

Zusätzlich ist es wichtig zu beachten, dass der Zugriff auf `document.doctype` nur funktioniert, wenn das Dokument bereits geladen ist. Ein Zugriff vor dem Laden des Dokuments kann zu `null` führen.

## One Line Summary
Das `DocumentType`-Objekt in JavaScript ermöglicht den Zugriff auf den DOCTYPE einer HTML- oder XML-Seite und ist entscheidend für die korrekte Dokumentdarstellung im Browser.