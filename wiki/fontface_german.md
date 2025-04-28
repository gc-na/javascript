<!--
Meta Description: # FontFace in JavaScript: Schriftarten dynamisch laden und anwenden ## Synopsis Die `FontFace`-API in JavaScript ermöglicht es Entwicklern, benutzerde...
Meta Keywords: die, fontface, schriftart, laden, der
-->

# FontFace in JavaScript: Schriftarten dynamisch laden und anwenden

## Synopsis
Die `FontFace`-API in JavaScript ermöglicht es Entwicklern, benutzerdefinierte Schriftarten programmgesteuert zu laden und zu verwenden, wodurch eine flexiblere Gestaltung von Webanwendungen möglich ist.

## Dokumentation
### Zweck
Die `FontFace`-Schnittstelle gehört zur Web Font Loader API und erlaubt das Erstellen, Laden und Anwenden von Schriftarten direkt über JavaScript. Dies ist besonders nützlich, wenn Schriftarten nicht im CSS definiert sind oder dynamisch zur Laufzeit geladen werden sollen.

### Verwendung
Um eine Schriftart mit `FontFace` zu verwenden, müssen folgende Schritte beachtet werden:
1. Erstellen Sie ein neues `FontFace`-Objekt und übergeben Sie den Namen der Schriftart und den Pfad zur Schriftartendatei.
2. Verwenden Sie die Methode `load()`, um die Schriftart zu laden.
3. Nachdem die Schriftart geladen wurde, können Sie sie mit der `document.fonts.add()`-Methode dem Dokument hinzufügen.

### Details
- **Syntax**: `new FontFace(font family, source, descriptors)`
  - `font family`: Der Name der Schriftart, die verwendet werden soll.
  - `source`: Der Pfad zur Schriftartendatei (z.B. als URL).
  - `descriptors`: (optional) Ein Objekt, das zusätzliche Eigenschaften wie `style`, `weight`, `stretch`, `unicodeRange` usw. definiert.

## Beispiele
### Grundlegende Verwendung
```javascript
// Erstellen einer neuen FontFace-Instanz
const myFont = new FontFace('MyCustomFont', 'url(/fonts/mycustomfont.woff2)');

// Laden der Schriftart
myFont.load().then(function(loadedFont) {
    // Schriftart zum Dokument hinzufügen
    document.fonts.add(loadedFont);
    // Schriftart auf ein Element anwenden
    document.body.style.fontFamily = 'MyCustomFont, sans-serif';
}).catch(function(error) {
    console.error('Fehler beim Laden der Schriftart:', error);
});
```

### Mit Deskriptoren
```javascript
const myStyledFont = new FontFace('MyStyledFont', 'url(/fonts/mystyledfont.woff2)', {
    style: 'italic',
    weight: '700'
});

myStyledFont.load().then(function(loadedFont) {
    document.fonts.add(loadedFont);
    document.body.style.fontFamily = 'MyStyledFont, sans-serif';
}).catch(function(error) {
    console.error('Fehler beim Laden der Schriftart:', error);
});
```

## Erklärung
- **Zugriffsprobleme**: Stellen Sie sicher, dass der Pfad zur Schriftartdatei korrekt ist und die Datei vom Server bereitgestellt wird. Andernfalls wird das Laden fehlschlagen.
- **Browserkompatibilität**: Die `FontFace`-API wird von den meisten modernen Browsern unterstützt, jedoch nicht von älteren Versionen. Überprüfen Sie die Kompatibilität, bevor Sie diese API verwenden.
- **Schriftarten-Caching**: Geladene Schriftarten werden im Browser-Cache gespeichert. Bei wiederholtem Laden kann die Schriftart ohne zusätzliche Netzwerkaufrufe verfügbar sein.

## Ein-Satz-Zusammenfassung
Die `FontFace`-API in JavaScript ermöglicht das dynamische Laden und Anwenden benutzerdefinierter Schriftarten, was die Gestaltung von Webanwendungen flexibler macht.