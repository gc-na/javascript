<!--
Meta Description: # PerformanceMeasure in JavaScript: Ein Leitfaden zur Leistungsanalyse ## Synopsis PerformanceMeasure ist eine API in JavaScript, die es Entwicklern e...
Meta Keywords: die, performance, der, und, messung
-->

# PerformanceMeasure in JavaScript: Ein Leitfaden zur Leistungsanalyse

## Synopsis
PerformanceMeasure ist eine API in JavaScript, die es Entwicklern ermöglicht, die Leistung von Webanwendungen zu messen und zu analysieren. Diese Funktion hilft dabei, Engpässe zu identifizieren und die Benutzererfahrung zu verbessern.

## Documentation
### Zweck
Die PerformanceMeasure-API gehört zur Performance-Management-API und wird verwendet, um benutzerdefinierte Zeitmessungen innerhalb einer Anwendung zu erstellen. Diese Messungen können dazu beitragen, die Leistung von Codeabschnitten zu bewerten und zu optimieren.

### Verwendung
Um PerformanceMeasure zu verwenden, müssen Sie die `performance.measure()` Methode aufrufen. Diese Methode benötigt einen Namen für die Messung und zwei Zeitstempel, die den Beginn und das Ende der Messung definieren.

#### Syntax
```javascript
performance.measure(measureName, startMark, endMark);
```

- `measureName`: Ein string, der den Namen der Messung angibt.
- `startMark`: (optional) Der Startzeitpunkt der Messung. Dies kann ein Markierungsname sein, der zuvor mit `performance.mark()` gesetzt wurde.
- `endMark`: (optional) Der Endzeitpunkt der Messung. Auch dies kann ein Markierungsname sein.

### Details
- Die `performance.mark()` Methode wird häufig verwendet, um Zeitmarken zu setzen, die dann als Referenz für die Messungen dienen.
- Die gemessenen Daten können über `performance.getEntriesByType('measure')` abgerufen werden.
- Die API ist nützlich für die Analyse und Optimierung der Ladezeiten, Rendering-Zeiten und anderer kritischer Bereiche in einer Webanwendung.

## Examples
### Beispiel 1: Grundlegende Verwendung
```javascript
// Setzen einer Startmarke
performance.mark('start');

// Ausführen eines Codeabschnitts
for (let i = 0; i < 1000000; i++) {
    // intensive Berechnungen
}

// Setzen einer Endmarke
performance.mark('end');

// Messen der Zeit zwischen den Markierungen
performance.measure('MyMeasure', 'start', 'end');

// Abrufen und Protokollieren der Messung
const measures = performance.getEntriesByType('measure');
console.log(measures);
```

### Beispiel 2: Verwendung ohne Markierungen
```javascript
// Direkte Messung ohne Markierungen
performance.measure('DirectMeasure', performance.now() - 200, performance.now());

// Protokollieren der Ergebnisse
console.log(performance.getEntriesByType('measure'));
```

## Explanation
Bei der Verwendung von PerformanceMeasure sollten folgende Punkte beachtet werden:
- **Genauigkeit der Markierungen**: Stellen Sie sicher, dass die Markierungen korrekt gesetzt werden, um akkurate Messwerte zu erhalten.
- **Browser-Kompatibilität**: Die Performance API wird von den meisten modernen Browsern unterstützt, jedoch sollten Sie die spezifischen Versionen überprüfen.
- **Leistungsbeeinträchtigung**: Zu viele Messungen in einer kurzen Zeitspanne können die Leistung beeinträchtigen. Verwenden Sie sie daher mit Bedacht.

## One Line Summary
PerformanceMeasure in JavaScript ermöglicht die präzise Messung und Analyse der Leistungsmerkmale von Webanwendungen, um Optimierungspotenziale zu identifizieren.