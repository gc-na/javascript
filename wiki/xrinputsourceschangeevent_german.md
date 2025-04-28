<!--
Meta Description: # XRInputSourcesChangeEvent: Ein Leitfaden zur Verwendung in JavaScript ## Synopsis Das `XRInputSourcesChangeEvent` ist ein wichtiges Ereignis in der ...
Meta Keywords: ein, die, ist, xrinputsourceschangeevent, das
-->

# XRInputSourcesChangeEvent: Ein Leitfaden zur Verwendung in JavaScript

## Synopsis
Das `XRInputSourcesChangeEvent` ist ein wichtiges Ereignis in der WebXR-API, das auf Änderungen der Eingabegeräte in einer XR-Umgebung hinweist. Es wird genutzt, um die Interaktivität und das Benutzererlebnis in Virtual Reality (VR) und Augmented Reality (AR) Anwendungen zu verbessern.

## Dokumentation
### Zweck
`XRInputSourcesChangeEvent` wird ausgelöst, wenn sich die Eingabegeräte, wie Controller oder Handtracking-Geräte, in einer XR-Sitzung ändern. Dies ermöglicht Entwicklern, die Benutzeroberfläche dynamisch an die verfügbaren Eingabemöglichkeiten anzupassen.

### Nutzung
Das Ereignis kann in einer WebXR-Anwendung verwendet werden, um auf Änderungen in den Input-Quellen zu reagieren. Wenn beispielsweise ein Benutzer einen Controller hinzufügt oder entfernt, kann die Anwendung darauf reagieren, indem sie die Benutzeroberfläche aktualisiert oder bestimmte Funktionen aktiviert oder deaktiviert.

### Details
- **Ereignistyp**: `XRInputSourcesChangeEvent`
- **Eigenschaften**: 
  - `session`: Die aktuelle XR-Sitzung, in der das Ereignis aufgetreten ist.
  - `added`: Ein Array von neu hinzugefügten Eingabegeräten.
  - `removed`: Ein Array von entfernten Eingabegeräten.

### Beispiel
Hier ist ein einfaches Beispiel, wie man auf ein `XRInputSourcesChangeEvent` reagiert:

```javascript
navigator.xr.requestSession('immersive-vr').then((session) => {
  session.addEventListener('inputsourceschange', (event) => {
    event.added.forEach((inputSource) => {
      console.log('Neues Eingabegerät hinzugefügt:', inputSource);
    });
    event.removed.forEach((inputSource) => {
      console.log('Eingabegerät entfernt:', inputSource);
    });
  });

  // Starten der XR-Sitzung
  session.start();
});
```

## Erklärung
Ein häufiges Problem bei der Verwendung von `XRInputSourcesChangeEvent` ist, dass Entwickler möglicherweise nicht alle möglichen Änderungen der Eingabegeräte richtig behandeln. Es ist wichtig, sowohl das Hinzufügen als auch das Entfernen von Geräten zu berücksichtigen. 

Ein weiterer Hinweis ist, sicherzustellen, dass die XR-Sitzung aktiv ist, bevor man versucht, auf Eingabeereignisse zuzugreifen. Wenn die Sitzung nicht aktiv ist, können keine Eingabegeräte erkannt werden, was zu unerwartetem Verhalten führen kann.

## Eine-Satz-Zusammenfassung
`XRInputSourcesChangeEvent` ermöglicht es Entwicklern, auf Änderungen der Eingabegeräte in einer XR-Sitzung zu reagieren und somit ein interaktives Benutzererlebnis zu schaffen.