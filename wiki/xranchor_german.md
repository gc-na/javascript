<!--
Meta Description: # XRAnchor: Ein Leitfaden für die Verwendung von XR-Ankern in JavaScript ## Synopsis XRAnchor ist eine zentrale Komponente der WebXR-API, die es Entwi...
Meta Keywords: die, sie, xrsession, let, xranchor
-->

# XRAnchor: Ein Leitfaden für die Verwendung von XR-Ankern in JavaScript

## Synopsis
XRAnchor ist eine zentrale Komponente der WebXR-API, die es Entwicklern ermöglicht, virtuelle Objekte in der realen Welt zu verankern, um eine immersive Augmented-Reality-Erfahrung zu schaffen.

## Documentation
### Zweck
XRAnchor wird verwendet, um eine Verbindung zwischen digitalen Inhalten und realen Umgebungen herzustellen. Es ermöglicht die Platzierung von 3D-Objekten an bestimmten Positionen im physischen Raum, sodass diese Objekte stabil und konsistent für den Benutzer bleiben, während sich dieser bewegt.

### Verwendung
Um ein XRAnchor zu erstellen, benötigen Sie eine XRSession, die eine WebXR-Sitzung darstellt. Sie können Anker anstellen, indem Sie die Methoden zur Erkennung von Umgebungen nutzen, wie etwa `XRReferenceSpace` und `XRHitTestSource`.

### Details
Ein XRAnchor speichert Informationen über die Position, Ausrichtung und Ankerinformationen eines Objekts im Raum. Diese Anker sind entscheidend für AR-Anwendungen, da sie helfen, digitale Inhalte präzise im Raum zu platzieren.

## Examples
### Beispiel 1: Erstellen eines XRAnchors
```javascript
let xrSession = await navigator.xr.requestSession('immersive-ar');
let referenceSpace = await xrSession.requestReferenceSpace('local');
let hitTestSource = await xrSession.requestHitTestSource({ space: referenceSpace });

xrSession.addEventListener('select', (event) => {
    let hitTestResults = hitTestSource.getResults();
    if (hitTestResults.length > 0) {
        let anchorPose = hitTestResults[0].getPose(referenceSpace);
        let anchor = xrSession.addAnchor(anchorPose.transform);
        // Fügen Sie hier Ihr 3D-Objekt hinzu.
    }
});
```

### Beispiel 2: Abrufen eines bestehenden Ankers
```javascript
let anchors = xrSession.getAnchors();
anchors.forEach(anchor => {
    let pose = anchor.getPose(referenceSpace);
    // Aktualisieren Sie die Position des 3D-Objekts basierend auf der Pose des Ankers.
});
```

## Explanation
Ein häufiger Fehler beim Arbeiten mit XRAnchors ist das Vergessen, die XRSession korrekt zu initialisieren. Achten Sie darauf, dass die Session aktiviert ist, bevor Sie versuchen, Anker zu erstellen oder zu verwenden. Ein weiterer Punkt ist die Handhabung von Anker-Lebenszyklen. Anker können nach einer gewissen Zeit nicht mehr gültig sein, insbesondere wenn sich die Umgebungsbedingungen ändern oder die Session unterbrochen wird. Daher sollten Sie regelmäßig überprüfen, ob Ihre Anker noch gültig sind.

## One Line Summary
XRAnchor ist ein grundlegendes Element der WebXR-API, das Entwicklern hilft, virtuelle Objekte präzise in der realen Welt zu verankern und immersive AR-Erlebnisse zu schaffen.