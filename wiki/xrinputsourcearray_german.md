<!--
Meta Description: # XRInputSourceArray: Eine umfassende Anleitung zur Verwendung in JavaScript ## Synopsis Der XRInputSourceArray ist eine wichtige JavaScript-Schnittst...
Meta Keywords: sie, die, xrinputsourcearray, eingabegeräte, session
-->

# XRInputSourceArray: Eine umfassende Anleitung zur Verwendung in JavaScript

## Synopsis
Der XRInputSourceArray ist eine wichtige JavaScript-Schnittstelle, die Teil der WebXR API ist. Sie ermöglicht Entwicklern den Zugriff auf Eingabegeräte wie Controller oder Handtracking in virtuellen und erweiterten Realitätserfahrungen.

## Dokumentation
### Zweck
XRInputSourceArray stellt eine Sammlung von XRInputSource-Objekten dar, die alle Eingabegeräte repräsentieren, die mit der aktuellen XR-Sitzung verbunden sind. Diese Schnittstelle ist entscheidend für die Interaktion mit virtuellen Umgebungen, da sie Entwicklern die Möglichkeit gibt, Benutzereingaben effizient zu verwalten.

### Verwendung
Um auf XRInputSourceArray zuzugreifen, benötigen Sie eine aktive XR-Sitzung. Die Eingabegeräte werden typischerweise über das `session.inputSources`-Attribut abgerufen. Hier ist ein einfaches Beispiel, wie Sie XRInputSourceArray in einer WebXR-Anwendung verwenden können.

### Details
- **Typ**: XRInputSourceArray ist ein Array-ähnliches Objekt, das XRInputSource-Instanzen enthält.
- **Eigenschaften**: Es bietet Methoden wie `get()`, um spezifische Eingabegeräte zu erhalten.
- **Kompatibilität**: Die Verwendung von XRInputSourceArray setzt voraus, dass der Browser die WebXR API unterstützt.

## Beispiele
Hier sind einige grundlegende Beispiele, wie Sie XRInputSourceArray in Ihrer WebXR-Anwendung verwenden können:

### Beispiel 1: Zugriff auf Eingabegeräte
```javascript
navigator.xr.requestSession('immersive-vr').then((session) => {
    session.addEventListener('selectstart', (event) => {
        const inputSources = session.inputSources;
        inputSources.forEach((inputSource) => {
            console.log(inputSource);
        });
    });
});
```

### Beispiel 2: Überprüfung auf Controller
```javascript
navigator.xr.requestSession('immersive-vr').then((session) => {
    session.updateWorldTrackingState();

    const inputSources = session.inputSources;
    inputSources.forEach((inputSource) => {
        if (inputSource.handedness === 'right') {
            console.log('Rechter Controller erkannt:', inputSource);
        }
    });
});
```

## Erklärung
### Häufige Fallstricke
- **Browserkompatibilität**: Stellen Sie sicher, dass Sie einen Browser verwenden, der WebXR unterstützt. Nicht alle Browser sind kompatibel.
- **Eingabegeräte**: Achten Sie darauf, dass die Eingabegeräte korrekt verbunden sind, bevor Sie auf sie zugreifen.
- **Ereignisbindung**: Vergewissern Sie sich, dass Sie die richtigen Ereignisse für die Benutzerinteraktion abonniert haben.

### Zusätzliche Hinweise
- Testen Sie Ihre Anwendung in verschiedenen Umgebungen, um sicherzustellen, dass die Eingabegeräte korrekt funktionieren.
- Verwenden Sie Debugging-Tools, um Probleme bei der Erkennung von Eingabegeräten zu identifizieren.

## Ein Satz Zusammenfassung
XRInputSourceArray ist ein entscheidendes API-Feature in JavaScript, das den Zugriff auf und die Verwaltung von Eingabegeräten in WebXR-Anwendungen ermöglicht.