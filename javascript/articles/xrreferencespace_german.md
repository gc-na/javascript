<!--
Meta Description: # XRReferenceSpace in JavaScript: Grundlagen und Anwendung ## Synopsis XRReferenceSpace ist eine zentrale Komponente der WebXR-API, die es Entwicklern...
Meta Keywords: der, die, xrreferencespace, und, ist
-->

# XRReferenceSpace in JavaScript: Grundlagen und Anwendung

## Synopsis
XRReferenceSpace ist eine zentrale Komponente der WebXR-API, die es Entwicklern ermöglicht, virtuelle und erweiterte Realitäten in Webanwendungen zu integrieren. Diese Schnittstelle definiert den räumlichen Bezugspunkt für XR-Inhalte und ermöglicht eine präzise Interaktion mit der physischen und virtuellen Umgebung.

## Documentation
### Zweck
XRReferenceSpace dient dazu, einen Bezugspunkt für XR-Anwendungen zu schaffen, der es ermöglicht, virtuelle Objekte relativ zur physischen Welt zu positionieren und zu bewegen. Diese Referenzräume sind entscheidend, um ein immersives Erlebnis zu bieten.

### Verwendung
Um XRReferenceSpace zu verwenden, müssen Sie zunächst eine XRSession initiieren und dann die Methode `getReferenceSpace()` aufrufen. Diese gibt ein XRReferenceSpace-Objekt zurück, das Ihnen erlaubt, die Position und Orientierung in der XR-Umgebung zu steuern.

### Details
Die WebXR-API unterstützt verschiedene Arten von Referenzräumen, darunter:
- **local**: Ein Referenzraum, der sich relativ zur Startposition des Nutzers definiert.
- **local-floor**: Ähnlich wie local, jedoch wird die Y-Achse so festgelegt, dass der Boden als Referenzpunkt dient.
- **bounded**: Ein Referenzraum, der die Grenzen eines definierten Bereichs berücksichtigt.
- **unbounded**: Ein Referenzraum ohne festgelegte Grenzen, der für Anwendungen mit unbegrenztem Raum nützlich ist.

### Beispielcode
Hier ist ein einfaches Beispiel, wie man ein XRReferenceSpace in einer WebXR-Anwendung einrichtet:

```javascript
navigator.xr.requestSession('immersive-vr').then((session) => {
    return session.requestReferenceSpace('local-floor');
}).then((referenceSpace) => {
    console.log('Reference Space:', referenceSpace);
}).catch((error) => {
    console.error('Error during XR session:', error);
});
```

## Explanation
Ein häufiger Stolperstein bei der Arbeit mit XRReferenceSpace ist die korrekte Handhabung der Referenzräume. Stellen Sie sicher, dass der gewählte Referenzraum mit den Anforderungen Ihrer Anwendung übereinstimmt. Beispielsweise ist der `local-floor`-Raum ideal für Anwendungen, die eine Interaktion mit dem Boden erfordern, während der `unbounded`-Raum besser für Spiele oder Simulationen geeignet ist, die in einem größeren Kontext stattfinden.

Zusätzlich sollten Sie darauf achten, dass nicht alle Geräte alle Referenzräume unterstützen. Es ist wichtig, die Verfügbarkeit von Referenzräumen zu überprüfen, bevor Sie sie in Ihrer Anwendung verwenden.

## One Line Summary
XRReferenceSpace ist eine essenzielle Schnittstelle in der WebXR-API, die Entwicklern hilft, virtuelle Objekte präzise im Raum zu positionieren und zu manipulieren.