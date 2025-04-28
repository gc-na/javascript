<!--
Meta Description: # Das JavaScript `ondragend` Ereignis: Ein umfassender Leitfaden ## Synopsis Das `ondragend` Ereignis in JavaScript wird ausgelöst, wenn ein Drag-and-...
Meta Keywords: das, ondragend, drag, ereignis, drop
-->

# Das JavaScript `ondragend` Ereignis: Ein umfassender Leitfaden

## Synopsis
Das `ondragend` Ereignis in JavaScript wird ausgelöst, wenn ein Drag-and-Drop-Vorgang erfolgreich abgeschlossen wird. Es ermöglicht Entwicklern, benutzerdefinierte Logik auszuführen, sobald ein Element an einen neuen Ort gezogen und dort abgelegt wird.

## Dokumentation
### Zweck
Das `ondragend` Ereignis ist ein Teil der Drag-and-Drop API von HTML5. Es wird verwendet, um festzustellen, wann ein Benutzer ein gezogenes Element an seine endgültige Position ablegt. Dieses Ereignis ist nützlich für Anwendungen, die interaktive Benutzeroberflächen erfordern.

### Verwendung
Um das `ondragend` Ereignis zu verwenden, muss es an ein HTML-Element gebunden werden, das als „ziehbar“ (draggable) definiert ist. Dies geschieht in der Regel durch Setzen des Attributs `draggable="true"`.

### Details
- **Syntax**: 
  ```javascript
  element.ondragend = function(event) {
      // Ihre Logik hier
  };
  ```
- **Ereignisobjekt**: Das Ereignisobjekt enthält Informationen über den Drag-and-Drop-Vorgang und ermöglicht den Zugriff auf die Daten, die während des Drag-Vorgangs übertragen werden.
- **Browserkompatibilität**: Das `ondragend` Ereignis wird von allen modernen Browsern unterstützt.

## Beispiele
### Einfaches Beispiel
```html
<!DOCTYPE html>
<html lang="de">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Drag and Drop Beispiel</title>
    <style>
        #dragElement {
            width: 100px;
            height: 100px;
            background-color: red;
            cursor: move;
        }
        #dropZone {
            width: 200px;
            height: 200px;
            background-color: lightgray;
            border: 2px dashed #000;
            margin-top: 20px;
        }
    </style>
</head>
<body>
    <div id="dragElement" draggable="true">Ziehen Sie mich!</div>
    <div id="dropZone">Hier ablegen</div>

    <script>
        const dragElement = document.getElementById('dragElement');
        const dropZone = document.getElementById('dropZone');

        dragElement.ondragend = function(event) {
            alert('Element wurde abgelegt!');
        };
    </script>
</body>
</html>
```

### Beispiel mit Daten
```javascript
dragElement.ondragend = function(event) {
    console.log('Element ID:', event.target.id);
    console.log('Drag Vorgang abgeschlossen');
};
```

## Erklärung
### Häufige Fallstricke
- **Vergessen, `draggable` zu setzen**: Wenn das `draggable` Attribut nicht gesetzt ist, wird das `ondragend` Ereignis nicht ausgelöst.
- **Unzureichende Ereignisverarbeitung**: Stellen Sie sicher, dass Sie auch das `ondragstart` und `ondragover` Ereignis implementieren, um einen vollständigen Drag-and-Drop-Workflow zu gewährleisten.
- **Browser-Spezifische Unterschiede**: Überprüfen Sie die Unterstützung des Drag-and-Drop-Mechanismus in verschiedenen Browsern, da es Unterschiede in der Implementierung geben kann.

### Zusätzliche Hinweise
- Nutzen Sie CSS, um visuelles Feedback während des Drag-and-Drop-Vorgangs zu geben.
- Testen Sie Ihre Implementierung gründlich, um sicherzustellen, dass alle Szenarien abgedeckt sind.

## Einzeilensummary
Das `ondragend` Ereignis in JavaScript signalisiert den Abschluss eines Drag-and-Drop-Vorgangs und ermöglicht das Ausführen benutzerdefinierter Logik.