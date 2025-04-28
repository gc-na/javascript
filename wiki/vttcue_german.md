<!--
Meta Description: # VTTCue: Eine umfassende Übersicht über die Nutzung in JavaScript ## Synopsis VTTCue ist ein JavaScript-Objekt, das zum Erstellen und Verwalten von U...
Meta Keywords: die, vttcue, der, cue, von
-->

# VTTCue: Eine umfassende Übersicht über die Nutzung in JavaScript

## Synopsis
VTTCue ist ein JavaScript-Objekt, das zum Erstellen und Verwalten von Untertiteln in HTML5-Videoelementen verwendet wird. Es ermöglicht Entwicklern, präzise Untertitel mit Zeitstempeln und Formatierungen zu erstellen.

## Documentation
VTTCue ist Teil der WebVTT (Web Video Text Tracks) Spezifikation, die von HTML5 unterstützt wird. Die Hauptaufgabe von VTTCue ist es, Textspuren für Videos zu definieren, die während der Wiedergabe angezeigt werden können. Es ermöglicht die Angabe von Zeitstempeln, die die Anzeigezeit der Untertitel steuern, sowie das Hinzufügen von Stil- und Formatierungsoptionen.

### Eigenschaften
- **startTime**: Die Zeit (in Sekunden), zu der der Cue angezeigt wird.
- **endTime**: Die Zeit (in Sekunden), zu der der Cue ausgeblendet wird.
- **text**: Der eigentliche Text, der als Untertitel angezeigt wird.
- **line**: Die vertikale Position des Untertitels.
- **position**: Die horizontale Position des Untertitels.

### Konstruktor
```javascript
const cue = new VTTCue(startTime, endTime, text);
```

## Examples
Hier sind einige grundlegende Beispiele zur Verwendung von VTTCue:

### Beispiel 1: Einfacher Cue erstellen
```javascript
const cue = new VTTCue(0, 5, "Willkommen zu unserem Video!");
console.log(cue.startTime); // Gibt 0 aus
console.log(cue.endTime);   // Gibt 5 aus
console.log(cue.text);      // Gibt "Willkommen zu unserem Video!" aus
```

### Beispiel 2: Cue zu einer Textspur hinzufügen
```javascript
const videoElement = document.querySelector('video');
const trackElement = videoElement.querySelector('track');

const cue1 = new VTTCue(0, 10, "Hallo!");
const cue2 = new VTTCue(10, 20, "Danke fürs Zuschauen!");

trackElement.track.addCue(cue1);
trackElement.track.addCue(cue2);
```

## Explanation
Bei der Verwendung von VTTCue sollten einige häufige Fallstricke beachtet werden:

- **Zeitstempel**: Achten Sie darauf, dass die `endTime` immer größer als die `startTime` ist. Andernfalls wird der Cue nicht angezeigt.
- **Formatierung**: VTTCue unterstützt einfache HTML-Formatierungen nicht direkt. Für komplexere Formate sollten CSS-Stile verwendet werden.
- **Browser-Kompatibilität**: Stellen Sie sicher, dass der verwendete Browser HTML5 und WebVTT unterstützt, da nicht alle älteren Browser diese Funktionen unterstützen.

## One Line Summary
VTTCue ist ein JavaScript-Objekt zur Verwaltung und Anzeige von Untertiteln in HTML5-Videoelementen.