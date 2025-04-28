<!--
Meta Description: # NavigationHistoryEntry in JavaScript: Eine umfassende Anleitung ## Synopsis Die `NavigationHistoryEntry`-Schnittstelle in JavaScript ermöglicht den ...
Meta Keywords: die, den, der, history, navigationhistoryentry
-->

# NavigationHistoryEntry in JavaScript: Eine umfassende Anleitung

## Synopsis
Die `NavigationHistoryEntry`-Schnittstelle in JavaScript ermöglicht den Zugriff auf die Einträge im Navigationsverlauf eines Benutzers, was Entwicklern hilft, den Zustand und die Historie während der Nutzung von Webanwendungen zu verwalten.

## Dokumentation
Die `NavigationHistoryEntry`-Schnittstelle ist Teil der Web API und ermöglicht die Interaktion mit den Einträgen im Navigationsverlauf einer Anwendung. Dies ist besonders nützlich für Single-Page-Applications (SPAs), wo eine präzise Verwaltung des Verlaufs erforderlich ist, um dem Benutzer ein nahtloses Erlebnis zu bieten.

### Zweck
Der Hauptzweck von `NavigationHistoryEntry` besteht darin, Entwicklern zu ermöglichen, den Zustand der Anwendung zu speichern und wiederherzustellen, während sie durch verschiedene Ansichten navigieren. Dies verbessert die Benutzererfahrung und sorgt für eine konsistente Interaktion mit der Anwendung.

### Verwendung
`NavigationHistoryEntry` wird typischerweise in Verbindung mit der `history`-Schnittstelle verwendet, um Informationen über die Navigationshistorie zu erhalten. Um auf die Navigationseinträge zuzugreifen, kann die Methode `history.getEntries()` verwendet werden, die eine Liste von `NavigationHistoryEntry`-Objekten zurückgibt.

### Details
- **Eigenschaften**:
  - `url`: Gibt die URL des Eintrags im Verlauf zurück.
  - `title`: Gibt den Titel des Eintrags zurück.
  - `state`: Gibt den Zustand des Eintrags zurück, der durch `history.pushState()` oder `history.replaceState()` festgelegt wurde.

- **Methoden**:
  - `history.go()`: Bewegt den Benutzer zu einer bestimmten Position im Verlauf.
  - `history.pushState()`: Fügt einen neuen Eintrag zu der Historie hinzu.
  - `history.replaceState()`: Ändert den aktuellen Eintrag in der Historie.

## Beispiele
Hier sind einige grundlegende Beispiele zur Verwendung von `NavigationHistoryEntry`.

### Beispiel 1: Zugriff auf den Verlauf
```javascript
// Zugriff auf den Verlaufseintrag
const entries = history.getEntries();
entries.forEach(entry => {
    console.log(entry.url, entry.title);
});
```

### Beispiel 2: Hinzufügen eines neuen Eintrags
```javascript
// Einen neuen Verlaufseintrag hinzufügen
history.pushState({page: 1}, "Seite 1", "/seite1");
```

### Beispiel 3: Ändern des aktuellen Eintrags
```javascript
// Den aktuellen Verlaufseintrag ändern
history.replaceState({page: 2}, "Seite 2", "/seite2");
```

## Erklärung
Ein häufiger Stolperstein bei der Verwendung von `NavigationHistoryEntry` ist das Verständnis, wann und wie Zustände gespeichert und wiederhergestellt werden. Entwickler sollten sicherstellen, dass sie `pushState` und `replaceState` effizient nutzen, um unnötige Einträge im Verlauf zu vermeiden. Außerdem kann die Verwendung von `history.go()` irreführend sein, wenn die Zielposition nicht korrekt angegeben wird.

Ein weiterer wichtiger Punkt ist, dass nicht alle Browser die gleiche Implementierung oder Unterstützung für `NavigationHistoryEntry` bieten. Es ist ratsam, die Kompatibilität zu überprüfen, bevor man sich auf diese API verlässt.

## Ein-Satz-Zusammenfassung
Die `NavigationHistoryEntry`-Schnittstelle in JavaScript ermöglicht Entwicklern den effizienten Zugriff und die Verwaltung der Navigationshistorie einer Webanwendung, um das Benutzererlebnis zu optimieren.