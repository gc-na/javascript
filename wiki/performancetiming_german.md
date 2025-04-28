<!--
Meta Description: # PerformanceTiming in JavaScript: Optimierung der Web-Performance ## Synopsis PerformanceTiming ist ein Teil der Navigation Timing API, die es Entwic...
Meta Keywords: die, der, timing, performancetiming, performance
-->

# PerformanceTiming in JavaScript: Optimierung der Web-Performance

## Synopsis
PerformanceTiming ist ein Teil der Navigation Timing API, die es Entwicklern ermöglicht, die Ladezeiten und Leistung von Webanwendungen zu messen. Diese API bietet präzise Zeitstempel, um verschiedene Phasen des Seitenladens zu analysieren und zu optimieren.

## Documentation
Die PerformanceTiming-Schnittstelle liefert wichtige Informationen über die Zeit, die für verschiedene Schritte beim Laden einer Webseite benötigt wird. Sie ermöglicht Entwicklern, Engpässe zu identifizieren und die Nutzererfahrung zu verbessern.

### Zweck
Der Hauptzweck von PerformanceTiming ist es, Entwicklern Daten zur Verfügung zu stellen, mit denen sie die Leistung ihrer Webseiten analysieren können. Diese Daten helfen, die Ladezeiten zu optimieren und die Benutzerinteraktion zu verbessern.

### Verwendung
Um auf PerformanceTiming zuzugreifen, kann der `performance`-API verwendet werden:

```javascript
let timing = performance.timing;
```

### Details
Die `PerformanceTiming`-Schnittstelle umfasst verschiedene Eigenschaften, die Zeitstempel für bestimmte Ereignisse liefern, wie z.B.:
- `navigationStart`: Zeitpunkt, an dem der Benutzer die Anfrage für die Seite initiiert hat.
- `unloadEventStart`: Zeitpunkt, an dem das Unload-Event des vorherigen Dokuments beginnt.
- `fetchStart`: Zeit, zu der der Browser mit dem Abrufen der Ressourcen begonnen hat.
- `domContentLoadedEventEnd`: Zeitpunkt, an dem das DOM vollständig geladen und analysiert wurde.

Die vollständige Liste der Eigenschaften und deren Bedeutung kann in der offiziellen Dokumentation nachgelesen werden.

## Examples
Hier sind einige grundlegende Beispiele zur Verwendung von PerformanceTiming:

### Beispiel 1: Grundlegende Messung der Ladezeit
```javascript
window.onload = function() {
    let timing = performance.timing;
    let loadTime = timing.loadEventEnd - timing.navigationStart;
    console.log("Ladezeit der Seite: " + loadTime + " ms");
};
```

### Beispiel 2: Analyse der DOM-Inhaltsladezeit
```javascript
window.onload = function() {
    let timing = performance.timing;
    let domContentLoadedTime = timing.domContentLoadedEventEnd - timing.navigationStart;
    console.log("Zeit bis der DOM vollständig geladen ist: " + domContentLoadedTime + " ms");
};
```

## Explanation
### Häufige Stolpersteine
- **Timing-Daten sind nicht sofort verfügbar**: Es ist wichtig, sicherzustellen, dass die `performance.timing`-Daten erst nach dem Laden der Seite abgerufen werden.
- **Browserunterstützung**: Nicht alle alten Browser unterstützen die Performance Timing API vollständig. Eine Überprüfung der Browserkompatibilität kann notwendig sein.

### Zusätzliche Hinweise
- Entwickeln Sie ein Verständnis für die verschiedenen Zeitstempel, um gezielte Optimierungen vorzunehmen.
- Nutzen Sie Performance-Analyse-Tools, um die gesammelten Daten visuell darzustellen und Engpässe zu identifizieren.

## One Line Summary
PerformanceTiming ist eine API in JavaScript, die präzise Zeitstempel zur Analyse und Optimierung der Ladezeiten von Webseiten bereitstellt.