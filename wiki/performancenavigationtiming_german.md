<!--
Meta Description: # PerformanceNavigationTiming in JavaScript: Optimierung der Webseitenleistung ## Synopsis PerformanceNavigationTiming ist ein nützliches Interface in...
Meta Keywords: die, der, navigation, performancenavigationtiming, von
-->

# PerformanceNavigationTiming in JavaScript: Optimierung der Webseitenleistung

## Synopsis
PerformanceNavigationTiming ist ein nützliches Interface in JavaScript, das Entwicklern hilft, die Ladezeiten ihrer Webseiten zu messen und zu analysieren. Es ermöglicht eine detaillierte Analyse der Navigation und Performance der Seite, was zu einer besseren Benutzererfahrung führt.

## Documentation
### Zweck
Das PerformanceNavigationTiming-Interface bietet eine präzise Messung der Zeitspanne, die für die Navigation einer Webseite benötigt wird. Es stellt verschiedene Zeitstempel zur Verfügung, die es Entwicklern ermöglichen, die Effizienz ihrer Webseiten zu bewerten und Optimierungen vorzunehmen.

### Verwendung
Um auf die Performance-Daten zuzugreifen, können Sie die `performance.getEntriesByType("navigation")` Methode verwenden. Diese Methode gibt ein Array von PerformanceNavigationTiming-Objekten zurück, die Informationen über die Navigation der aktuellen Seite enthalten.

### Details
Das PerformanceNavigationTiming-Interface erweitert das PerformanceEntry-Interface und stellt folgende Eigenschaften zur Verfügung:

- `startTime`: Der Zeitpunkt, zu dem die Navigation begann.
- `duration`: Die Dauer der Navigation in Millisekunden.
- `redirectCount`: Die Anzahl der Weiterleitungen, die für die Navigation erforderlich waren.
- `type`: Der Typ der Navigation (z. B. "navigate", "reload", "back-forward").
- `nextHopProtocol`: Das verwendete Protokoll für die nächste Hop-Anfrage.

## Examples
Hier sind einige grundlegende Beispiele zur Verwendung von PerformanceNavigationTiming:

### Beispiel 1: Abrufen von Navigationsdaten
```javascript
const navigationEntries = performance.getEntriesByType("navigation");
if (navigationEntries.length > 0) {
    const navigationData = navigationEntries[0];
    console.log(`Navigation Type: ${navigationData.type}`);
    console.log(`Dauer: ${navigationData.duration} ms`);
}
```

### Beispiel 2: Analysieren von Weiterleitungen
```javascript
const navigationEntries = performance.getEntriesByType("navigation");
if (navigationEntries.length > 0) {
    const redirectCount = navigationEntries[0].redirectCount;
    console.log(`Anzahl der Weiterleitungen: ${redirectCount}`);
}
```

## Explanation
Bei der Verwendung von PerformanceNavigationTiming gibt es einige häufige Fallstricke:

- **Browserunterstützung**: Stellen Sie sicher, dass der verwendete Browser das PerformanceNavigationTiming-Interface unterstützt. Ältere Browser unterstützen möglicherweise diese Funktion nicht.
- **Timing-Daten**: Die Daten sind nur verfügbar, nachdem die Seite vollständig geladen wurde. Versuchen Sie nicht, auf die Daten zuzugreifen, bevor die Seite vollständig geladen ist.
- **Caching**: Beachten Sie, dass bei wiederholten Besuchen von Seiten, die im Cache gespeichert sind, die Ladezeiten möglicherweise nicht korrekt gemessen werden, da der Browser die Seite aus dem Cache lädt.

## One Line Summary
PerformanceNavigationTiming ist ein leistungsstarkes Interface in JavaScript zur präzisen Messung und Analyse der Ladezeiten von Webseiten.