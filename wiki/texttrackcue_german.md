<!--
Meta Description: # TextTrackCue in JavaScript: Eine umfassende Anleitung ## Synopsis `TextTrackCue` ist ein JavaScript-Objekt, das in HTML5-Video- und Audioelementen v...
Meta Keywords: die, und, der, texttrackcue, video
-->

# TextTrackCue in JavaScript: Eine umfassende Anleitung

## Synopsis
`TextTrackCue` ist ein JavaScript-Objekt, das in HTML5-Video- und Audioelementen verwendet wird, um Untertitel, Beschriftungen und andere Textüberlagerungen zu erstellen und zu verwalten.

## Documentation
`TextTrackCue` wird im Kontext von HTML5-Video- und Audioelementen verwendet, um Textinhalte zu synchronisieren, die während der Medienwiedergabe angezeigt werden. Es stellt eine Schnittstelle dar, die es Entwicklern ermöglicht, Textüberlagerungen zu definieren, die zu bestimmten Zeitpunkten in einem Medienstream angezeigt werden.

### Zweck
Der Hauptzweck von `TextTrackCue` besteht darin, Entwicklern die Möglichkeit zu geben, Untertitel oder Beschriftungen für Medieninhalte zu erstellen. Dies verbessert die Zugänglichkeit und das Benutzererlebnis, indem es auch hörgeschädigten Benutzern ermöglicht, Inhalte zu verstehen.

### Verwendung
`TextTrackCue` ist Teil der `TextTrack`-Schnittstelle und bietet eine einfache Möglichkeit, Textüberlagerungen zu definieren. Um eine neue `TextTrackCue`-Instanz zu erstellen, benötigen Sie die Start- und Endzeit sowie den Textinhalt.

### Eigenschaften
- **startTime**: Die Zeit (in Sekunden), zu der der Cue angezeigt wird.
- **endTime**: Die Zeit (in Sekunden), zu der der Cue ausgeblendet wird.
- **text**: Der Textinhalt des Cues.

### Methoden
- **getCueAsHTML()**: Gibt den Cue-Inhalt als HTML zurück.

## Examples
Hier sind einige einfache Beispiele für die Verwendung von `TextTrackCue`:

### Beispiel 1: Erstellen und Hinzufügen eines Cue
```javascript
// Zugriff auf das Videoelement
const video = document.querySelector('video');
const track = video.addTextTrack('subtitles', 'Deutsch', 'de');

// Erstellen eines neuen TextTrackCue
const cue = new VTTCue(0, 5, 'Willkommen zu unserem Video!');

// Hinzufügen des Cues zur Textspur
track.addCue(cue);
```

### Beispiel 2: Änderungen an einem bestehenden Cue
```javascript
// Zugriff auf das Videoelement
const video = document.querySelector('video');
const track = video.textTracks[0];

// Zugriff auf den ersten Cue
const cue = track.cues[0];
cue.text = 'Änderung: Willkommen zu unserem neuen Video!';
```

## Explanation
Ein häufiges Missverständnis beim Arbeiten mit `TextTrackCue` ist, dass die Cues automatisch angezeigt werden, ohne dass der Texttrack aktiviert wird. Stellen Sie sicher, dass der Texttrack vor der Wiedergabe des Videos aktiviert ist, um die Cues korrekt anzuzeigen. 

Ein weiterer häufiger Stolperstein ist die Verwendung des falschen Datentyps für die Zeiten. `startTime` und `endTime` müssen in Sekunden angegeben werden, und es ist wichtig sicherzustellen, dass `endTime` größer als `startTime` ist.

## One Line Summary
`TextTrackCue` ist ein JavaScript-Objekt zur Verwaltung von Untertiteln und Textüberlagerungen in HTML5-Medien.