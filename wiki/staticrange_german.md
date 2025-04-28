<!--
Meta Description: # StaticRange in JavaScript: Eine umfassende Anleitung ## Synopsis `StaticRange` ist eine JavaScript-Schnittstelle, die eine nicht veränderbare Darste...
Meta Keywords: staticrange, range, die, ist, und
-->

# StaticRange in JavaScript: Eine umfassende Anleitung

## Synopsis
`StaticRange` ist eine JavaScript-Schnittstelle, die eine nicht veränderbare Darstellung eines Textbereichs im DOM bietet. Sie ermöglicht Entwicklern, Text- und Elementauswahlen innerhalb eines Dokuments zu erzeugen und zu verwalten, ohne die Gefahr, dass sich die Auswahl aufgrund von DOM-Änderungen ändert.

## Dokumentation
`StaticRange` ist Teil der Web-API und ermöglicht es, einen bestimmten Bereich von Text oder Elementen im DOM zu definieren. Diese Schnittstelle ist besonders nützlich, wenn Sie mit Bereichen arbeiten möchten, die nicht durch Benutzerinteraktionen oder andere Skripte beeinflusst werden können.

### Zweck
Die Hauptidee hinter `StaticRange` ist es, eine stabile Referenz auf einen bestimmten Bereich im Dokument zu erstellen, die unabhängig von Änderungen im DOM bleibt. Dies ist besonders hilfreich in Anwendungen, die mit Textverarbeitung, Rich-Text-Editoren oder ähnlichen Funktionen arbeiten.

### Verwendung
Um ein `StaticRange`-Objekt zu erstellen, verwenden Sie den `StaticRange`-Konstruktor, der zwei Parameter erwartet: `start` und `end`, die beide eine `Range`-Objektinstanz repräsentieren.

```javascript
const range = new Range();
range.setStart(startNode, startOffset);
range.setEnd(endNode, endOffset);

const staticRange = new StaticRange({ start: range.startContainer, startOffset: range.startOffset, end: range.endContainer, endOffset: range.endOffset });
```

### Details
- **Konstruktor**: `StaticRange` hat einen Konstruktor, der ein Objekt mit den Eigenschaften `start` und `end` erwartet.
- **Eigenschaften**: Die Eigenschaften `startContainer`, `startOffset`, `endContainer` und `endOffset` geben den Bereich des Textes oder der Elemente an.
- **Unveränderlichkeit**: Ein `StaticRange`-Objekt ist unveränderlich, was bedeutet, dass es keine Methoden zur Modifikation des Bereichs bietet.

## Beispiele
Hier sind einige einfache Beispiele zur Verwendung von `StaticRange`:

### Beispiel 1: Erstellen eines StaticRange
```javascript
const startNode = document.getElementById('start');
const endNode = document.getElementById('end');
const range = new Range();
range.setStart(startNode, 0);
range.setEnd(endNode, 1);

const staticRange = new StaticRange({
    start: range.startContainer,
    startOffset: range.startOffset,
    end: range.endContainer,
    endOffset: range.endOffset
});
```

### Beispiel 2: Zugriff auf Eigenschaften
```javascript
console.log(staticRange.startContainer); // Gibt den Start-Container aus
console.log(staticRange.endContainer);   // Gibt den End-Container aus
```

## Erklärung
Ein häufiges Problem beim Arbeiten mit `StaticRange` ist, dass Entwickler möglicherweise versuchen, den Bereich nach seiner Erstellung zu ändern. Da `StaticRange` unveränderlich ist, sollten Änderungen am DOM, die den Bereich betreffen, nicht versucht werden; stattdessen sollte ein neuer `StaticRange` erstellt werden.

Außerdem ist es wichtig zu beachten, dass `StaticRange` nicht in allen Browsern unterstützt wird. Stellen Sie sicher, dass Sie die Kompatibilität prüfen, bevor Sie diese Funktion in Produktion verwenden.

## Ein-Satz-Zusammenfassung
`StaticRange` ist eine JavaScript-Schnittstelle zur Erstellung und Verwaltung stabiler Text- und Elementauswahlen im DOM, die unveränderlich sind und nicht auf DOM-Änderungen reagieren.