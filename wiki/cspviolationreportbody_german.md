<!--
Meta Description: # CSPViolationReportBody: Umgang mit Content Security Policy-Verletzungsberichten in JavaScript ## Synopsis CSPViolationReportBody ist ein wichtiges I...
Meta Keywords: die, der, csp, ein, cspviolationreportbody
-->

# CSPViolationReportBody: Umgang mit Content Security Policy-Verletzungsberichten in JavaScript

## Synopsis
CSPViolationReportBody ist ein wichtiges Interface in JavaScript, das die Details von Verletzungsberichten der Content Security Policy (CSP) bereitstellt. Es ermöglicht Entwicklern, Sicherheitsvorfälle zu erkennen und entsprechend zu reagieren.

## Dokumentation
### Zweck
Die CSP (Content Security Policy) ist ein Sicherheitsmechanismus, der dazu dient, verschiedene Arten von Angriffen wie Cross-Site Scripting (XSS) und Dateninjektionen zu verhindern. Wenn ein Browser eine CSP-Verletzung erkennt, sendet er einen Bericht an die angegebene URL. CSPViolationReportBody stellt die Struktur dieser Berichte dar und ermöglicht Entwicklern, die genauen Details der Verstöße zu analysieren.

### Verwendung
CSPViolationReportBody wird in Kombination mit der `report-uri` oder `report-to` Direktive in einer CSP-Header-Definition verwendet. Wenn eine Verletzung auftritt, wird ein POST-Antrag an die definierte URL gesendet, der ein JSON-Objekt enthält, das das CSPViolationReportBody darstellt.

### Details
Das CSPViolationReportBody-Objekt enthält folgende wichtige Informationen:
- **document-uri**: Die URI des Dokuments, in dem die Verletzung aufgetreten ist.
- **referrer**: Die Referrer-URI des Dokuments.
- **violated-directive**: Die spezifische CSP-Direktive, die verletzt wurde.
- **effective-directive**: Die aktuelle, wirksame CSP-Direktive.
- **original-policy**: Die ursprüngliche CSP-Policy, die angewendet wurde.
- **source-file**: Die URI der Datei, die die verletzende Ressource enthält.
- **line-number**: Die Zeilennummer im Quellcode, wo die Verletzung aufgetreten ist.
- **column-number**: Die Spaltennummer im Quellcode, wo die Verletzung aufgetreten ist.
- **status-code**: Der HTTP-Status-Code, der mit der Verletzung verbunden ist.

## Beispiele
### Beispiel 1: Einfache Verwendung
Wenn eine CSP-Verletzung auftritt, wird ein Bericht im folgenden Format gesendet:

```json
{
  "document-uri": "https://example.com/page.html",
  "referrer": "https://example.com/",
  "violated-directive": "script-src 'self'",
  "effective-directive": "script-src 'self'",
  "original-policy": "default-src 'self'; script-src 'self'",
  "source-file": "https://example.com/unsafe-script.js",
  "line-number": 10,
  "column-number": 15,
  "status-code": 200
}
```

### Beispiel 2: Verarbeitung eines Berichts
Hier ein Beispiel, wie man einen CSP-Violationsbericht auf der Serverseite empfangen und verarbeiten kann:

```javascript
const express = require('express');
const bodyParser = require('body-parser');

const app = express();
app.use(bodyParser.json());

app.post('/csp-report', (req, res) => {
    const report = req.body;
    console.log('CSP Violations Report:', report);
    res.status(204).send();
});

app.listen(3000, () => {
    console.log('Server listening on port 3000');
});
```

## Erklärung
### Häufige Fallstricke
1. **Falsche URL für den Bericht**: Stellen Sie sicher, dass die URL, an die die Berichte gesendet werden, korrekt konfiguriert ist.
2. **CORS-Probleme**: Wenn der Bericht an eine andere Domain gesendet wird, stellen Sie sicher, dass die CORS-Richtlinien richtig gesetzt sind, um den Empfang zu ermöglichen.
3. **Unzureichende CSP-Richtlinien**: Überprüfen Sie Ihre CSP, um sicherzustellen, dass sie alle potenziellen Angriffe abdeckt.

### Zusätzliche Hinweise
- Berichte können auch durch Browsererweiterungen oder durch falsche Konfigurationen von Drittanbieter-Skripten erzeugt werden. Achten Sie darauf, diese Aspekte bei der Analyse der Berichte zu berücksichtigen.

## Ein Satz Zusammenfassung
CSPViolationReportBody ermöglicht es Entwicklern, die Details von Content Security Policy-Verletzungen in JavaScript zu erfassen und zu analysieren, um die Sicherheit ihrer Webanwendungen zu verbessern.