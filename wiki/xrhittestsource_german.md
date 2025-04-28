<!--
Meta Description: # XRHitTestSource in JavaScript: Ein Leitfaden zur Verwendung in WebXR-Anwendungen ## Synopsis XRHitTestSource ist eine Schnittstelle in der WebXR-API...
Meta Keywords: die, der, xrhittestsource, werden, von
-->

# XRHitTestSource in JavaScript: Ein Leitfaden zur Verwendung in WebXR-Anwendungen

## Synopsis
XRHitTestSource ist eine Schnittstelle in der WebXR-API, die es Entwicklern ermöglicht, virtuelle Objekte präzise in der realen Welt zu platzieren, indem sie die Position und Orientierung von physischen Oberflächen erkennen.

## Dokumentation
### Zweck
XRHitTestSource wird verwendet, um eine Interaktion zwischen virtuellen Inhalten und der realen Umgebung zu ermöglichen. Diese Schnittstelle ist besonders nützlich in Augmented Reality (AR)-Anwendungen, wo digitale Objekte nahtlos in die reale Welt integriert werden.

### Verwendung
Um eine Instanz von XRHitTestSource zu erstellen, muss zuerst ein XRSession-Objekt initialisiert werden. Anschließend kann die `requestHitTestSource`-Methode aufgerufen werden, um eine Quelle für die Treffererkennung zu erhalten. Diese Quelle kann dann verwendet werden, um Informationen über die Position von virtuellen Objekten zu erhalten.

### Details
- **Erstellung**: XRHitTestSource kann mit der Methode `requestHitTestSource` erstellt werden, die ein Hit-Test-Ergebnis zurückgibt.
- **Parameter**: Diese Methode akzeptiert ein Objekt mit spezifischen Konfigurationen, wie z.B. der `space`-Eigenschaft, die die räumliche Position definiert, in der die Treffererkennung durchgeführt wird.
- **Methoden**: Die zurückgegebene XRHitTestSource-Instanz kann verwendet werden, um kontinuierlich Informationen über die Position und Orientierung von erkannten Oberflächen zu erhalten.

## Beispiele
### Grundlegende Verwendung
```javascript
let xrSession = await navigator.xr.requestSession('immersive-ar');
let hitTestSource;

xrSession.requestHitTestSource({ space: yourReferenceSpace })
    .then(source => {
        hitTestSource = source;
    });

// In der Render-Schleife
xrSession.requestHitTest(xrFrame.getHitTestSource(hitTestSource)).then(hitResults => {
    if (hitResults.length > 0) {
        let hitPose = hitResults[0].getPose(yourReferenceSpace);
        // Plazieren Sie hier Ihr virtuelles Objekt
    }
});
```

## Erklärung
### Häufige Fallstricke
- **Kompatibilität**: Stellen Sie sicher, dass der Browser die WebXR-API unterstützt, da nicht alle Browser die Funktionalität von XRHitTestSource unterstützen.
- **Referenzraum**: Der angegebene Referenzraum muss vor der Verwendung von XRHitTestSource korrekt definiert werden.
- **Performance**: Häufige Anfragen an die Hit-Test-Quelle können die Leistung beeinträchtigen. Es wird empfohlen, Anfragen nur dann zu stellen, wenn dies unbedingt erforderlich ist.

### Zusätzliche Hinweise
- Die Verwendung von XRHitTestSource kann in Verbindung mit anderen WebXR-Funktionen wie XRFrame und XRReferenceSpace ausgeführt werden, um ein reibungsloses Erlebnis zu gewährleisten.
- Achten Sie darauf, die Quelle zu löschen, wenn sie nicht mehr benötigt wird, um Speicherlecks zu vermeiden.

## Ein-Satz-Zusammenfassung
XRHitTestSource ermöglicht es Entwicklern, virtuelle Objekte präzise in der realen Welt zu platzieren, indem sie die Erkennung physischer Oberflächen in WebXR-Anwendungen nutzen.