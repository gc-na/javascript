<!--
Meta Description: # PerformanceResourceTiming in JavaScript: Optimierung der Ressourcenverfolgung ## Synopsis `PerformanceResourceTiming` ist eine Schnittstelle in Java...
Meta Keywords: die, der, resource, ressourcen, performanceresourcetiming
-->

# PerformanceResourceTiming in JavaScript: Optimierung der Ressourcenverfolgung

## Synopsis
`PerformanceResourceTiming` ist eine Schnittstelle in JavaScript, die es Entwicklern ermöglicht, detaillierte Informationen über die Ladezeiten und die Leistung von Ressourcen zu erfassen, die von einem Dokument geladen werden. Diese Informationen sind entscheidend für die Optimierung der Webanwendung und die Verbesserung der Benutzererfahrung.

## Dokumentation
Die `PerformanceResourceTiming`-Schnittstelle bietet spezifische Eigenschaften, die Informationen über Netzwerkressourcen bereitstellen, die während der Navigation oder der Interaktion mit einer Webseite geladen werden. Diese Eigenschaften umfassen unter anderem:

- **name**: Der vollständige URI der geladenen Ressource.
- **startTime**: Der Zeitpunkt, zu dem der Ladevorgang der Ressource begann.
- **duration**: Die Gesamtdauer des Ladevorgangs in Millisekunden.
- **responseEnd**: Der Zeitpunkt, an dem die Antwort des Servers vollständig empfangen wurde.
- **fetchStart**: Der Zeitpunkt, zu dem die Anfrage zur Ressource gesendet wurde.

### Nutzung
Um `PerformanceResourceTiming` zu verwenden, können Entwickler die `performance.getEntriesByType("resource")`-Methode verwenden, um eine Liste aller geladenen Ressourcen zu erhalten. Diese Methode gibt ein Array von `PerformanceResourceTiming`-Objekten zurück.

## Beispiele
Hier sind einige grundlegende Beispiele für die Verwendung von `PerformanceResourceTiming`:

### Beispiel 1: Ressourcen laden und Leistungsdaten abrufen
```javascript
// Alle Ressourcen des aktuellen Dokuments abrufen
const resources = performance.getEntriesByType("resource");

resources.forEach(resource => {
    console.log(`Ressource: ${resource.name}`);
    console.log(`Startzeit: ${resource.startTime}`);
    console.log(`Dauer: ${resource.duration} ms`);
});
```

### Beispiel 2: Filtern nach bestimmten Ressourcen
```javascript
// Nur Bilder abfragen
const images = performance.getEntriesByType("resource").filter(resource => resource.initiatorType === "img");

images.forEach(image => {
    console.log(`Bild: ${image.name}`);
    console.log(`Ladezeit: ${image.duration} ms`);
});
```

## Erklärung
Ein häufiger Fehler bei der Verwendung von `PerformanceResourceTiming` ist, dass einige Entwickler die Daten vor dem vollständigen Laden der Seite abfragen. Es ist wichtig sicherzustellen, dass die Ressourcen vollständig geladen sind, bevor die Leistungsdaten abgerufen werden. Außerdem kann der Zugriff auf diese Daten in unterschiedlichen Browsern variieren, insbesondere bei älteren Versionen. 

Ein weiterer Punkt ist, dass einige Ressourcen möglicherweise von CORS (Cross-Origin Resource Sharing) betroffen sind, was bedeutet, dass die Leistungsdaten möglicherweise nicht verfügbar sind, wenn die Ressourcen von einer anderen Domain stammen.

## Einzeiler-Zusammenfassung
`PerformanceResourceTiming` ermöglicht die präzise Überwachung und Analyse der Ladezeiten von Ressourcen in JavaScript-Anwendungen, um die Leistung zu optimieren.