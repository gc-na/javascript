<!--
Meta Description: # MediaDeviceInfo in JavaScript: Eine umfassende Anleitung ## Synopsis Die `MediaDeviceInfo`-Schnittstelle in JavaScript bietet Informationen über die...
Meta Keywords: die, der, ein, mediadeviceinfo, und
-->

# MediaDeviceInfo in JavaScript: Eine umfassende Anleitung

## Synopsis
Die `MediaDeviceInfo`-Schnittstelle in JavaScript bietet Informationen über die verfügbaren Mediengeräte eines Benutzers, wie Mikrofone, Kameras und Lautsprecher. Sie ist ein wichtiger Bestandteil der WebRTC-API und ermöglicht Entwicklern, die Interaktion mit Multimedia-Inhalten in Webanwendungen zu steuern.

## Dokumentation
Die `MediaDeviceInfo`-Objekte enthalten Informationen über die verschiedenen Mediengeräte, die auf einem Gerät verfügbar sind. Diese Informationen können verwendet werden, um dem Benutzer eine Auswahl an Geräten zu präsentieren oder um spezifische Geräte für Audio- und Video-Streams auszuwählen.

### Verwendung
Um auf die Informationen der verfügbaren Mediengeräte zuzugreifen, verwenden Sie die `navigator.mediaDevices.enumerateDevices()`-Methode. Diese Methode gibt ein Promise zurück, das ein Array von `MediaDeviceInfo`-Objekten enthält.

### Eigenschaften
- `deviceId`: Eine eindeutige ID für das Gerät.
- `kind`: Der Typ des Geräts (z. B. "audioinput", "audiooutput", "videoinput").
- `label`: Ein beschreibender Name für das Gerät (z. B. der Name des Mikrofon- oder Kameraherstellers). Dies kann leer sein, wenn der Benutzer keine Berechtigung erteilt hat.
- `groupId`: Eine ID, die Geräte zusammenfasst, die zu einer Gruppe gehören, z. B. mehrere Kameras eines Herstellers.

## Beispiele
### Beispiel 1: Auflisten der verfügbaren Mediengeräte
```javascript
navigator.mediaDevices.enumerateDevices()
  .then(devices => {
    devices.forEach(device => {
      console.log(`${device.kind}: ${device.label} (ID: ${device.deviceId})`);
    });
  })
  .catch(err => {
    console.error(`${err.name}: ${err.message}`);
  });
```

### Beispiel 2: Filterung von Audio-Eingabegeräten
```javascript
navigator.mediaDevices.enumerateDevices()
  .then(devices => {
    const audioInputs = devices.filter(device => device.kind === 'audioinput');
    console.log('Verfügbare Audio-Eingabegeräte:', audioInputs);
  });
```

## Erklärung
Ein häufiger Stolperstein bei der Verwendung von `MediaDeviceInfo` ist die Berechtigung des Benutzers. Wenn der Benutzer den Zugriff auf seine Mediengeräte verweigert, werden die `label`-Eigenschaften der Geräte in der `enumerateDevices()`-Ausgabe leer sein. Es ist daher wichtig, den Benutzer um Erlaubnis zu bitten, bevor Sie auf die Geräte zugreifen. Verwenden Sie dafür die `getUserMedia()`-Methode.

Ein weiterer Punkt ist, dass die `deviceId` für die gleiche Hardware bei jedem Aufruf der Methode unterschiedlich sein kann, wenn der Benutzer den Browser oder die Seite wechselt. Dies kann zu Verwirrung führen, wenn Sie versuchen, ein bestimmtes Gerät wiederzuerkennen.

## Ein Satz Zusammenfassung
Die `MediaDeviceInfo`-Schnittstelle in JavaScript ermöglicht Entwicklern den Zugriff auf und die Verwaltung von Mediengeräten, die auf einem Gerät verfügbar sind, und ist entscheidend für die Interaktion mit Audio- und Video-Streams in Webanwendungen.