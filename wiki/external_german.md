<!--
Meta Description: # Externe Skripte in JavaScript: Verwendung und Bedeutung ## Zusammenfassung In dieser Dokumentation wird erklärt, wie externe Skripte in JavaScript v...
Meta Keywords: html, die, script, das, und
-->

# Externe Skripte in JavaScript: Verwendung und Bedeutung

## Zusammenfassung
In dieser Dokumentation wird erklärt, wie externe Skripte in JavaScript verwendet werden, um die Funktionalität von Webseiten zu erweitern und Code wiederverwendbar zu gestalten.

## Dokumentation
Externe Skripte in JavaScript sind separate JavaScript-Dateien, die in HTML-Dokumente eingebunden werden, um die Wartbarkeit und Modularität des Codes zu verbessern. Anstatt JavaScript-Code direkt in ein HTML-Dokument zu schreiben, werden diese Skripte in separaten Dateien gespeichert und dann über das `<script>`-Tag in das HTML eingebunden.

### Zweck
Der Hauptzweck von externen Skripten ist die Trennung von HTML und JavaScript, was zu einer besseren Struktur, Lesbarkeit und Wiederverwendbarkeit des Codes führt. Dies erleichtert auch die Zusammenarbeit in Teams, da mehrere Entwickler gleichzeitig an verschiedenen Aspekten der Anwendung arbeiten können.

### Verwendung
Um ein externes Skript einzubinden, verwenden Sie das `<script>`-Tag mit dem `src`-Attribut. Hier ist die allgemeine Syntax:

```html
<script src="pfad/zum/skript.js"></script>
```

Das Skript kann im `<head>`- oder im `<body>`-Bereich Ihrer HTML-Datei platziert werden. Es ist jedoch üblich, externe Skripte am Ende des `<body>`-Tags einzufügen, um sicherzustellen, dass das HTML-Dokument zuerst geladen wird.

### Details
- **Caching**: Externe Skripte werden vom Browser zwischengespeichert, was die Ladezeiten bei wiederholten Besuchen der Seite verbessert.
- **Asynchrone und defer-Attribute**: Sie können die Attribute `async` oder `defer` verwenden, um die Ladepriorität und Ausführung von Skripten zu steuern.
  - `async`: Das Skript wird asynchron geladen und sofort ausgeführt, wenn es verfügbar ist.
  - `defer`: Das Skript wird geladen, aber erst ausgeführt, nachdem das gesamte HTML-Dokument geparsed wurde.

## Beispiele
### Einfaches Beispiel
```html
<!DOCTYPE html>
<html lang="de">
<head>
    <meta charset="UTF-8">
    <title>Beispiel Externes Skript</title>
    <script src="script.js"></script>
</head>
<body>
    <h1>Willkommen zu meinem Beispiel</h1>
</body>
</html>
```

### Beispiel mit `async`
```html
<script src="script.js" async></script>
```

### Beispiel mit `defer`
```html
<script src="script.js" defer></script>
```

## Erklärung
Ein häufiger Fehler kann auftreten, wenn das Skript vor dem Laden des HTML-Dokuments ausgeführt wird, was zu Problemen führen kann, wenn das Skript auf DOM-Elemente zugreift, die noch nicht vorhanden sind. Um dies zu vermeiden, sollte das Skript entweder am Ende des `<body>`-Tags platziert oder mit dem Attribut `defer` verwendet werden.

Ein weiterer Punkt ist, dass die Pfadangabe im `src`-Attribut korrekt sein muss. Ein falscher Pfad führt dazu, dass das Skript nicht geladen werden kann, was zu Fehlern in der Anwendung führt.

## Ein-Satz-Zusammenfassung
Externe Skripte in JavaScript verbessern die Modularität und Wartbarkeit von Webanwendungen durch die Trennung von Code und HTML.