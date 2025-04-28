<!--
Meta Description: # PerformanceServerTiming in JavaScript: Optimierung der Server-Leistungsanalyse ## Synopsis PerformanceServerTiming ist eine JavaScript-Schnittstelle...
Meta Keywords: die, server, timing, header, performanceservertiming
-->

# PerformanceServerTiming in JavaScript: Optimierung der Server-Leistungsanalyse

## Synopsis
PerformanceServerTiming ist eine JavaScript-Schnittstelle, die Entwicklern ermöglicht, Leistungsmetriken von Serverantworten zu erfassen und zu analysieren. Diese Informationen helfen dabei, die Performance von Webanwendungen zu optimieren.

## Dokumentation
Die PerformanceServerTiming-Schnittstelle ist Teil der Web Performance API und ermöglicht es Entwicklern, Timing-Informationen über Server-Antworten zu sammeln. Diese Informationen sind besonders nützlich, um die Geschwindigkeit von Anfragen und die Effizienz von Servern zu bewerten.

### Zweck
Mit PerformanceServerTiming können Entwickler die Zeit messen, die ein Server benötigt, um auf Anfragen zu reagieren. Dies ist entscheidend für die Identifizierung von Engpässen und zur Verbesserung der Gesamtleistung einer Webanwendung.

### Verwendung
Um PerformanceServerTiming zu nutzen, müssen Server die entsprechenden Header in ihren HTTP-Antworten bereitstellen. Diese Header enthalten spezifische Timing-Informationen, die dann im Performance-Objekt im Browser verfügbar sind.

### Details
- **Header**: Server müssen `Server-Timing`-Header in den Antworten verwenden. Zum Beispiel:
  ```
  Server-Timing: cache;dur=23, db;dur=47
  ```
- **Zugriff**: Entwickler können über das `performance.getEntriesByType("resource")`-API auf die gesammelten Daten zugreifen.

## Beispiele
### Beispiel 1: Server-Timing-Header setzen
Um Server-Timing-Header in einer Node.js-Anwendung zu setzen, kann folgender Code verwendet werden:
```javascript
app.get('/data', (req, res) => {
    res.setHeader('Server-Timing', 'cache;dur=23, db;dur=47');
    res.send('Daten erfolgreich geladen');
});
```

### Beispiel 2: Zugriff auf Server-Timing-Daten
Nachdem die Server-Timing-Header gesetzt wurden, können die Daten wie folgt abgerufen werden:
```javascript
fetch('/data')
    .then(response => {
        const serverTiming = response.headers.get('Server-Timing');
        console.log('Server-Timing:', serverTiming);
    });
```

## Erklärung
Ein häufiges Problem beim Einsatz von PerformanceServerTiming ist die korrekte Implementierung der Header auf der Serverseite. Wenn die Header nicht richtig gesetzt sind, können keine gültigen Daten im Client abgerufen werden. Zudem ist es wichtig, die Header in einem für den Client lesbaren Format zu übermitteln.

### Gotchas
- **Browser-Unterstützung**: Nicht alle Browser unterstützen die PerformanceServerTiming-Schnittstelle. Es ist wichtig, die Kompatibilität zu prüfen.
- **Serverkonfiguration**: Die Serverkonfiguration muss so eingestellt sein, dass diese Header gesendet werden. In vielen Fällen sind zusätzliche Einstellungen erforderlich.

## Ein-Satz-Zusammenfassung
PerformanceServerTiming in JavaScript ermöglicht die Erfassung und Analyse von Server-Leistungsmetriken, um die Performance von Webanwendungen zu optimieren.