<!--
Meta Description: # queryLocalFonts: Lokale Schriftarten in JavaScript abfragen ## Synopsis Die Funktion `queryLocalFonts` ermöglicht es Entwicklern, lokale Schriftarte...
Meta Keywords: schriftarten, die, querylocalfonts, funktion, ist
-->

# queryLocalFonts: Lokale Schriftarten in JavaScript abfragen

## Synopsis
Die Funktion `queryLocalFonts` ermöglicht es Entwicklern, lokale Schriftarten, die im Browser des Benutzers installiert sind, abzufragen. Dies bietet eine wertvolle Möglichkeit, um Schriftarten dynamisch zu laden und die Benutzererfahrung zu verbessern.

## Documentation
### Zweck
`queryLocalFonts` ist eine JavaScript-Funktion, die eine Liste der lokal installierten Schriftarten zurückgibt. Diese Funktion ist besonders nützlich für Webanwendungen, die Schriftarten dynamisch anpassen oder Benutzerpräferenzen für Schriftarten berücksichtigen möchten.

### Verwendung
Um `queryLocalFonts` zu verwenden, muss die Funktion in einem unterstützten Browser ausgeführt werden. Sie gibt ein Promise-Objekt zurück, das mit einer Liste von Schriftarten aufgelöst wird.

### Details
- **Syntax**: 
  ```javascript
  queryLocalFonts().then(fonts => {
      // Verarbeitung der Schriftarten
  });
  ```
- **Rückgabewert**: Ein Promise, das ein Array von Schriftarten zurückgibt.
- **Browserunterstützung**: Diese Funktion ist in modernen Browsern verfügbar, jedoch nicht in allen. Es wird empfohlen, die Kompatibilität zu überprüfen.

## Examples
### Grundlegende Nutzung
Hier ist ein einfaches Beispiel, wie `queryLocalFonts` verwendet werden kann, um eine Liste von Schriftarten anzuzeigen:

```javascript
async function displayLocalFonts() {
    try {
        const fonts = await queryLocalFonts();
        console.log('Lokale Schriftarten:', fonts);
    } catch (error) {
        console.error('Fehler beim Abfragen der Schriftarten:', error);
    }
}

displayLocalFonts();
```

### Nutzung in einer Anwendung
In einer Webanwendung könnte die Schriftartauswahl so aussehen:

```javascript
async function loadFonts() {
    const fonts = await queryLocalFonts();
    const fontSelect = document.getElementById('fontSelect');

    fonts.forEach(font => {
        const option = document.createElement('option');
        option.value = font;
        option.textContent = font;
        fontSelect.appendChild(option);
    });
}

loadFonts();
```

## Explanation
### Häufige Stolpersteine
- **Browserkompatibilität**: Nicht alle Browser unterstützen `queryLocalFonts`. Es ist wichtig, die aktuelle Unterstützung zu überprüfen und gegebenenfalls Fallback-Lösungen anzubieten.
- **Fehlerbehandlung**: Achten Sie darauf, Fehler zu behandeln, die beim Abfragen der Schriftarten auftreten können, z.B. wenn der Benutzer keine Schriftarten installiert hat oder die Funktion nicht unterstützt wird.

### Zusätzliche Hinweise
- Diese Funktion sollte nicht als einzige Methode zur Schriftartverwaltung verwendet werden, da sie abhängig von den lokal installierten Schriftarten ist.
- Testen Sie die Funktion in verschiedenen Umgebungen, um sicherzustellen, dass sie wie erwartet funktioniert.

## One Line Summary
`queryLocalFonts` ist eine JavaScript-Funktion, die es Entwicklern ermöglicht, lokal installierte Schriftarten im Browser abzufragen und zu nutzen.