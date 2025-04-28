<!--
Meta Description: # PerformanceMark: Leistungsüberwachung in JavaScript ## Synopsis PerformanceMark ist eine Schnittstelle in der Web Performance API, die es Entwickler...
Meta Keywords: performance, die, der, performancemark, javascript
-->

# PerformanceMark: Leistungsüberwachung in JavaScript 

## Synopsis
PerformanceMark ist eine Schnittstelle in der Web Performance API, die es Entwicklern ermöglicht, benutzerdefinierte Leistungsmarken zu setzen und zu messen, um die Leistung von Webanwendungen zu analysieren.

## Dokumentation
Die `PerformanceMark`-Schnittstelle gehört zur Performance API von JavaScript und ermöglicht es Entwicklern, spezifische Zeitpunkte im Code zu markieren. Diese Markierungen können dann verwendet werden, um die Leistung der Anwendung zu überwachen und zu optimieren. 

### Zweck
Der Hauptzweck von `PerformanceMark` ist es, bestimmte Punkte im Lebenszyklus einer Anwendung zu erfassen, um die Dauer zwischen verschiedenen Ereignissen zu messen.

### Verwendung
Um eine neue Performance-Marke zu erstellen, verwenden Sie die Methode `performance.mark()`. Hier ein einfaches Beispiel:

```javascript
performance.mark('start');

// Code, dessen Leistung gemessen werden soll
for (let i = 0; i < 1000000; i++) {}

performance.mark('end');
```

Zusätzlich können Sie die Zeit zwischen den Marken mit der `performance.measure()`-Methode messen:

```javascript
performance.measure('myMeasurement', 'start', 'end');
```

### Details
- **Markenname**: Der Name jeder Marke muss eindeutig sein, um Verwirrung zu vermeiden.
- **Messungen**: Sie können mehrere Messungen zwischen den Marken erstellen, um verschiedene Zeitabschnitte zu analysieren.
- **Browserunterstützung**: Die Performance API wird von den meisten modernen Browsern unterstützt, aber es ist ratsam, die Kompatibilität zu überprüfen.

## Beispiele
Hier sind einige grundlegende Beispiele zur Verwendung von `PerformanceMark`:

### Einfaches Markenbeispiel
```javascript
performance.mark('beginTask');
// Simulieren einer Aufgabe
setTimeout(() => {
    performance.mark('endTask');
    performance.measure('taskDuration', 'beginTask', 'endTask');
    const measurements = performance.getEntriesByName('taskDuration');
    console.log(measurements);
}, 1000);
```

### Mehrere Marken
```javascript
performance.mark('step1');
// Erster Schritt der Verarbeitung
performance.mark('step2');
// Zweiter Schritt der Verarbeitung
performance.measure('processDuration', 'step1', 'step2');
```

## Erklärung
Ein häufiges Problem bei der Verwendung von `PerformanceMark` ist, dass Entwickler möglicherweise nicht genügend Marken setzen, um einen vollständigen Überblick über die Leistung ihrer Anwendung zu erhalten. Es ist wichtig, strategisch Marken an kritischen Stellen im Anwendungscode festzulegen, um optimale Ergebnisse zu erzielen.

Ein weiterer Punkt ist die Überprüfung der Browserkompatibilität, da ältere Versionen von Browsern möglicherweise nicht alle Funktionen der Performance API unterstützen. Verwenden Sie Fallback-Methoden oder Polyfills, wenn Sie eine breitere Unterstützung benötigen.

## Einzeilenzusammenfassung
PerformanceMark in JavaScript ermöglicht es Entwicklern, benutzerdefinierte Leistungsmarken zu setzen und die Effizienz ihrer Webanwendungen zu messen.