<!--
Meta Description: # TextTrack in JavaScript: Verwendung, Beispiele und Tipps ## Synopsis TextTrack ist eine Schnittstelle in JavaScript, die zur Verwaltung von Untertit...
Meta Keywords: die, video, textspur, und, cue
-->

# TextTrack in JavaScript: Verwendung, Beispiele und Tipps

## Synopsis
TextTrack ist eine Schnittstelle in JavaScript, die zur Verwaltung von Untertiteln und anderen Textspuren in HTML5-Videoplayern verwendet wird. Diese Funktion ermöglicht es Entwicklern, die Benutzererfahrung durch die Anzeige von Textinformationen zu verbessern.

## Dokumentation
### Zweck
Die TextTrack-Schnittstelle ist Teil der HTML5-Video-API und ermöglicht die Interaktion mit Textspuren wie Untertiteln, Beschreibungen oder Kapitelmarkierungen. Sie bietet Methoden zur Steuerung, Anzeige und zur Anpassung von Textinhalten, die mit einem Video synchronisiert sind.

### Verwendung
Um TextTrack in JavaScript zu verwenden, müssen Sie zunächst ein `<video>`-Element mit einer oder mehreren Textspuren (z. B. `<track>`-Elemente) einfügen. Jede Textspur hat spezifische Attribute wie `kind`, `label` und `srclang`, um den Typ, die Sprache und die Beschriftung zu definieren.

#### Beispiel
```html
<video controls>
    <source src="movie.mp4" type="video/mp4">
    <track kind="subtitles" src="subtitles_en.vtt" srclang="en" label="Englisch">
    <track kind="subtitles" src="subtitles_de.vtt" srclang="de" label="Deutsch">
    Your browser does not support the video tag.
</video>
```

In JavaScript können Sie dann auf die TextTracks über die `video`-Elementeigenschaft `textTracks` zugreifen:

```javascript
const video = document.querySelector('video');
const tracks = video.textTracks;

for (let i = 0; i < tracks.length; i++) {
    console.log(tracks[i].label); // Gibt die Beschriftung der Textspur aus
}
```

### Details
TextTrack bietet mehrere Eigenschaften und Methoden, um mit Textspuren zu interagieren:

- **Properties**:
  - `mode`: Gibt den Modus der Textspur an (z. B. `disabled`, `hidden`, `showing`).
  - `label`: Die Beschreibung oder Beschriftung der Textspur.
  - `language`: Die Sprache der Textspur.

- **Methods**:
  - `addCue(Cue cue)`: Fügt der Textspur einen Cue hinzu.
  - `removeCue(Cue cue)`: Entfernt einen Cue aus der Textspur.

## Beispiele
### Grundlegende Nutzung
```javascript
const video = document.querySelector('video');
const track = video.textTracks[0]; // Zugriff auf die erste Textspur

track.mode = 'showing'; // Aktiviert die Anzeige der Textspur
console.log(track.label); // Gibt die Beschriftung der Textspur aus
```

### Cue hinzufügen
```javascript
const cue = new VTTCue(0, 10, "Willkommen zu unserem Video!");
track.addCue(cue); // Fügt einen neuen Cue hinzu
```

## Erklärung
Ein häufiger Fehler tritt auf, wenn man versucht, Cues hinzuzufügen, bevor die Textspur vollständig geladen ist. Stellen Sie sicher, dass die Textspur bereit ist, bevor Sie Änderungen vornehmen.

Ein weiteres häufiges Problem ist, dass einige Browser unterschiedliche Unterstützung für TextTrack und seine Eigenschaften bieten. Testen Sie Ihre Implementierung in verschiedenen Browsern, um Kompatibilitätsprobleme zu vermeiden.

## Ein Satz Zusammenfassung
TextTrack ist eine JavaScript-Schnittstelle zur Verwaltung und Anzeige von Untertiteln und Textinformationen in HTML5-Videos.