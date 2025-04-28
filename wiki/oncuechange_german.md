<!--
Meta Description: # oncuechange in JavaScript: Ein umfassender Leitfaden ## Synopsis Die `oncuechange`-Eigenschaft in JavaScript ermöglicht Entwicklern, auf Änderungen ...
Meta Keywords: video, oncuechange, ein, cue, activecue
-->

# oncuechange in JavaScript: Ein umfassender Leitfaden

## Synopsis
Die `oncuechange`-Eigenschaft in JavaScript ermöglicht Entwicklern, auf Änderungen im Cue-Status von Medienelementen wie `<video>` oder `<audio>` zu reagieren, was insbesondere für Untertitel und Textüberlagerungen nützlich ist.

## Dokumentation
Die `oncuechange`-Eigenschaft ist ein Ereignis-Handler, der ausgelöst wird, wenn sich der Cue-Status eines Medien-Elements ändert. Ein Cue ist ein definiertes Zeitintervall, in dem bestimmte Textüberlagerungen oder Untertitel angezeigt werden. Diese Eigenschaft kann verwendet werden, um dynamisch auf Änderungen zu reagieren, beispielsweise um Texte anzuzeigen oder zu verstecken.

### Verwendung
Um `oncuechange` zu verwenden, müssen Sie zuerst ein Medienelement (z. B. ein `<video>`-Element) erstellen und dann einen Event-Listener für die `oncuechange`-Ereignisbindung hinzufügen.

### Syntax
```javascript
mediaElement.oncuechange = function() {
    // Ihr Code hier
};
```

### Details
- **Ereignis-Objekt**: Bei der Ausführung des Handlers wird ein Ereignisobjekt bereitgestellt, das Informationen über den aktuellen Cue enthält.
- **Kompatibilität**: Diese Eigenschaft ist in modernen Browsern weitgehend unterstützt, jedoch sollten ältere Browser getestet werden.
- **Anwendungsfall**: Besonders nützlich in Medienanwendungen, bei denen Benutzer interaktive Untertitel oder visuelle Effekte benötigen.

## Beispiele
### Einfaches Beispiel
```html
<video id="myVideo" controls>
    <source src="movie.mp4" type="video/mp4">
    <track src="subtitles_en.vtt" kind="subtitles" srclang="en" label="English">
</video>

<script>
    const video = document.getElementById('myVideo');
    
    video.oncuechange = function() {
        const activeCue = video.textTracks[0].activeCues[0];
        if (activeCue) {
            console.log('Aktiver Cue:', activeCue.text);
        }
    };
</script>
```

### Fortgeschrittenes Beispiel
```html
<video id="myVideo" controls>
    <source src="movie.mp4" type="video/mp4">
    <track src="subtitles_de.vtt" kind="subtitles" srclang="de" label="Deutsch">
</video>

<div id="cueDisplay"></div>

<script>
    const video = document.getElementById('myVideo');
    const cueDisplay = document.getElementById('cueDisplay');
    
    video.oncuechange = function() {
        const activeCue = video.textTracks[0].activeCues[0];
        cueDisplay.innerText = activeCue ? activeCue.text : '';
    };
</script>
```

## Erklärung
Bei der Verwendung von `oncuechange` ist es wichtig, sich der folgenden Aspekte bewusst zu sein:

- **Aktive Cues**: Stellen Sie sicher, dass Sie überprüfen, ob aktive Cues vorhanden sind, da nicht jeder Aufruf des Handlers notwendigerweise einen aktiven Cue zurückgibt.
- **Browserkompatibilität**: Testen Sie Ihre Implementierung in verschiedenen Browsern, da einige ältere Versionen möglicherweise nicht alle Funktionen unterstützen.
- **Performance**: Übermäßige Manipulationen im `oncuechange`-Handler können die Leistung beeinträchtigen, insbesondere bei großen Medieninhalten oder komplexen DOM-Operationen.

## Ein-Satz-Zusammenfassung
Die `oncuechange`-Eigenschaft in JavaScript ermöglicht Entwicklern, flexibel auf Änderungen von Untertiteln und Textüberlagerungen in Medieninhalten zu reagieren.