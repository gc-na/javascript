<!--
Meta Description: # crossOriginIsolated in JavaScript: Eine umfassende Anleitung ## Synopsis `crossOriginIsolated` ist eine JavaScript-Eigenschaft, die anzeigt, ob eine...
Meta Keywords: die, crossoriginisolated, ist, anwendung, eigenschaft
-->

# crossOriginIsolated in JavaScript: Eine umfassende Anleitung

## Synopsis
`crossOriginIsolated` ist eine JavaScript-Eigenschaft, die anzeigt, ob eine Webanwendung in einem isolierten Kontext läuft, was bedeutet, dass sie keine externen Ressourcen lädt, die nicht dieselbe Herkunft haben. Diese Eigenschaft ist entscheidend für die Sicherheit und den Schutz von Daten in modernen Webanwendungen.

## Dokumentation
### Zweck
Die `crossOriginIsolated`-Eigenschaft wird verwendet, um den Sicherheitsstatus einer Webanwendung zu bestimmen. Sie ist ein Teil der `Window`-Schnittstelle und ermöglicht Entwicklern zu überprüfen, ob ihre Anwendung in einem isolierten Zustand läuft. Dies ist besonders wichtig für Anwendungen, die mit Web-APIs arbeiten, die eine sichere Umgebung erfordern, wie z.B. `WebAssembly` oder `SharedArrayBuffer`.

### Verwendung
Die `crossOriginIsolated`-Eigenschaft wird wie folgt verwendet:

```javascript
if (window.crossOriginIsolated) {
    console.log("Die Anwendung ist cross-origin isoliert.");
} else {
    console.log("Die Anwendung ist nicht cross-origin isoliert.");
}
```

### Details
- **Typ**: Boolean
- **Verfügbarkeit**: `crossOriginIsolated` ist in modernen Browsern verfügbar, die Unterstützung für Sicherheitsfunktionen wie `Cross-Origin-Embedder-Policy` und `Cross-Origin-Opener-Policy` bieten.
- **Betriebssysteme und Browser**: Diese Eigenschaft ist in den meisten aktuellen Versionen von Chrome, Firefox und Edge verfügbar, während ältere Versionen oder weniger verbreitete Browser möglicherweise nicht unterstützt werden.

## Beispiele
### Einfaches Beispiel
Hier ist ein einfaches Beispiel, das demonstriert, wie man die `crossOriginIsolated`-Eigenschaft abruft:

```javascript
if (window.crossOriginIsolated) {
    console.log("Die Anwendung läuft sicher.");
} else {
    console.log("Die Anwendung hat keinen sicheren Kontext.");
}
```

### Beispiel mit WebAssembly
In einem WebAssembly-Kontext könnte die Überprüfung wie folgt aussehen:

```javascript
if (window.crossOriginIsolated) {
    // Lade und verwende WebAssembly
    loadWebAssembly();
} else {
    console.warn("WebAssembly kann nicht in einem unsicheren Kontext verwendet werden.");
}
```

## Erklärung
### Häufige Probleme
Ein häufiges Missverständnis bei der Verwendung von `crossOriginIsolated` ist die Annahme, dass alle Webanwendungen standardmäßig in einem isolierten Zustand laufen. Dies ist nicht der Fall; die Anwendung muss speziell konfiguriert werden, um die entsprechenden Header (`Cross-Origin-Embedder-Policy` und `Cross-Origin-Opener-Policy`) zu setzen.

### Zusätzliche Hinweise
- **Sicherheitsrichtlinien**: Um `crossOriginIsolated` zu aktivieren, müssen Server die richtigen CORS-Header setzen. Andernfalls wird die Anwendung nicht als isoliert erkannt.
- **Browserunterstützung**: Überprüfen Sie die Browserkompatibilität bei der Entwicklung, um sicherzustellen, dass die Anwendung auf allen Zielplattformen korrekt funktioniert.

## Einzeilige Zusammenfassung
`crossOriginIsolated` ist eine JavaScript-Eigenschaft, die den Sicherheitsstatus einer Anwendung angibt, indem sie feststellt, ob sie in einem isolierten Kontext läuft.