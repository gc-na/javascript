<!--
Meta Description: # XRInputSource in JavaScript: Eine umfassende Anleitung für Entwickler ## Synopsis XRInputSource ist ein JavaScript-Objekt, das in der WebXR-API verw...
Meta Keywords: die, und, inputsource, xrinputsource, session
-->

# XRInputSource in JavaScript: Eine umfassende Anleitung für Entwickler

## Synopsis
XRInputSource ist ein JavaScript-Objekt, das in der WebXR-API verwendet wird, um Eingabegeräte wie Controller und andere interaktive Geräte in Virtual-Reality- und Augmented-Reality-Anwendungen zu erkennen und zu verwalten.

## Dokumentation
### Zweck
XRInputSource dient dazu, Entwicklern den Zugriff auf Eingabegeräte zu ermöglichen, die in WebXR-Anwendungen verwendet werden. Es bietet eine standardisierte Möglichkeit, Informationen über die Eingabegeräte abzurufen, die mit einer XR-Sitzung verbunden sind.

### Verwendung
XRInputSource ist Teil des XRSession-Objekts und wird typischerweise im Kontext einer WebXR-Anwendung verwendet. Es bietet verschiedene Eigenschaften, um Informationen über das Eingabegerät zu erhalten, darunter:

- `handedness`: Gibt an, ob das Eingabegerät für die linke oder rechte Hand bestimmt ist.
- `targetRaySpace`: Ein XRSpace, der den Ursprungsort und die Richtung des Eingabegeräts beschreibt.
- `gamepad`: Beinhaltet Informationen über den Gamepad-Zustand, wenn das Eingabegerät ein Gamepad ist.

### Details
Um XRInputSource zu verwenden, müssen Sie eine XR-Sitzung initialisieren und die `inputsources`-Eigenschaft verwenden, um auf die verbundenen Eingabegeräte zuzugreifen. Hier ein grundlegendes Beispiel:

```javascript
navigator.xr.requestSession('immersive-vr').then(session => {
    session.addEventListener('selectstart', event => {
        const inputSource = event.inputSource;
        console.log('Eingabegerät: ', inputSource);
    });
});
```

## Beispiele
### Beispiel 1: Zugriff auf Eingabegeräte
```javascript
navigator.xr.requestSession('immersive-vr').then(session => {
    session.addEventListener('inputsourceschange', event => {
        event.added.forEach(inputSource => {
            console.log('Neues Eingabegerät hinzugefügt: ', inputSource);
        });
    });
});
```

### Beispiel 2: Informationen über die Hand
```javascript
navigator.xr.requestSession('immersive-vr').then(session => {
    session.addEventListener('selectstart', event => {
        const inputSource = event.inputSource;
        console.log('Hand: ', inputSource.handedness);
    });
});
```

## Erklärung
### Häufige Fallstricke
1. **Nicht unterstützte Geräte**: Stellen Sie sicher, dass das verwendete Gerät WebXR unterstützt, da einige ältere Geräte möglicherweise nicht kompatibel sind.
2. **Ereignisbindung**: Achten Sie darauf, die Ereignisse korrekt zu binden, um keine Eingaben zu verpassen.
3. **Session-Management**: Verwenden Sie `requestSession` nur, wenn die XR-Umgebung bereit ist, um Laufzeitfehler zu vermeiden.

### Zusätzliche Hinweise
Die Verwendung von XRInputSource kann variieren, je nachdem, ob Sie VR- oder AR-Anwendungen erstellen. Achten Sie darauf, die spezifischen Eigenschaften und Methoden zu verwenden, die für Ihre Anwendung relevant sind.

## Zusammenfassung in einem Satz
XRInputSource ist ein JavaScript-Objekt, das Entwicklern ermöglicht, Eingabegeräte in WebXR-Anwendungen zu erkennen und zu verwalten.