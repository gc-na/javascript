<!--
Meta Description: # XMLHttpRequestUpload: Hochladen von Dateien mit JavaScript ## Synopsis `XMLHttpRequestUpload` ist eine JavaScript-Schnittstelle, die speziell für da...
Meta Keywords: upload, die, uploads, const, xmlhttprequestupload
-->

# XMLHttpRequestUpload: Hochladen von Dateien mit JavaScript

## Synopsis
`XMLHttpRequestUpload` ist eine JavaScript-Schnittstelle, die speziell für das Überwachen des Fortschritts von Datei-Uploads via XMLHttpRequest entwickelt wurde. Sie ermöglicht Entwicklern, den Fortschritt von Uploads in Echtzeit zu verfolgen und auf Ereignisse zu reagieren.

## Dokumentation
### Zweck
`XMLHttpRequestUpload` wird verwendet, um Uploads von Dateien über AJAX-Anfragen zu verwalten. Es bietet Funktionen, um den Fortschritt des Uploads zu überwachen und Ereignisse zu handhaben, die während des Uploads auftreten.

### Verwendung
Um `XMLHttpRequestUpload` zu verwenden, müssen Sie zunächst ein `XMLHttpRequest`-Objekt erstellen. Anschließend können Sie die `upload`-Eigenschaft des XMLHttpRequest-Objekts verwenden, um die Upload-Funktionalität zu aktivieren.

#### Grundlegende Eigenschaften
- **onprogress**: Ein Ereignis, das während des Uploads ausgelöst wird, um den Fortschritt anzuzeigen.
- **onload**: Ein Ereignis, das ausgelöst wird, wenn der Upload erfolgreich abgeschlossen ist.
- **onerror**: Ein Ereignis, das auftritt, wenn beim Upload ein Fehler auftritt.

### Details
`XMLHttpRequestUpload` ist besonders nützlich für Anwendungen, die große Dateien oder mehrere Dateien gleichzeitig hochladen. Es ermöglicht den Benutzern, den Fortschritt des Uploads zu visualisieren und auf verschiedene Upload-Zustände zu reagieren.

## Beispiele
### Einfaches Beispiel für einen Datei-Upload
```javascript
// HTML-Element für die Datei-Auswahl
<input type="file" id="fileInput" />
<button id="uploadButton">Hochladen</button>
<div id="progressStatus"></div>

<script>
    const uploadButton = document.getElementById('uploadButton');
    const fileInput = document.getElementById('fileInput');
    const progressStatus = document.getElementById('progressStatus');

    uploadButton.addEventListener('click', () => {
        const file = fileInput.files[0];
        const xhr = new XMLHttpRequest();
        
        const upload = xhr.upload;

        // Fortschrittsanzeige
        upload.addEventListener('progress', (event) => {
            if (event.lengthComputable) {
                const percentComplete = (event.loaded / event.total) * 100;
                progressStatus.textContent = `Hochladefortschritt: ${percentComplete.toFixed(2)}%`;
            }
        });

        // Erfolgreiches Hochladen
        upload.addEventListener('load', () => {
            progressStatus.textContent = 'Upload erfolgreich!';
        });

        // Fehler beim Hochladen
        upload.addEventListener('error', () => {
            progressStatus.textContent = 'Fehler beim Hochladen!';
        });

        xhr.open('POST', '/upload-endpoint');
        const formData = new FormData();
        formData.append('file', file);
        xhr.send(formData);
    });
</script>
```

## Erklärung
Ein häufiges Problem bei der Verwendung von `XMLHttpRequestUpload` ist das Vergessen, die richtigen Event-Listener hinzuzufügen. Stellen Sie sicher, dass Sie die Listener für `onprogress`, `onload` und `onerror` einrichten, um den Upload vollständig zu überwachen. Außerdem sollten Sie bedenken, dass die `upload`-Eigenschaft nur verfügbar ist, wenn die Anfrage mit `XMLHttpRequest` erstellt wird und nicht bei anderen Transportmethoden.

## Ein-Satz-Zusammenfassung
`XMLHttpRequestUpload` ist eine essentielle JavaScript-Schnittstelle zum Überwachen und Verwalten des Fortschritts von Datei-Uploads.