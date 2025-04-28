<!--
Meta Description: # USBConnectionEvent in JavaScript: Ereignisse für USB-Verbindungen ## Synopsis Der `USBConnectionEvent` ist ein Ereignis in JavaScript, das in der We...
Meta Keywords: usb, event, die, ist, usbconnectionevent
-->

# USBConnectionEvent in JavaScript: Ereignisse für USB-Verbindungen

## Synopsis
Der `USBConnectionEvent` ist ein Ereignis in JavaScript, das in der Web-Anwendungsentwicklung verwendet wird, um auf Änderungen des Status von USB-Verbindungen zu reagieren. Dieses Ereignis ist Teil der WebUSB-API und ermöglicht es Entwicklern, mit USB-Geräten zu kommunizieren.

## Dokumentation
Der `USBConnectionEvent` tritt auf, wenn ein USB-Gerät verbunden oder getrennt wird. Dieses Ereignis ist besonders nützlich für Webanwendungen, die mit Hardware wie Druckern, Scannern oder anderen Peripheriegeräten interagieren müssen. 

### Zweck
Der Hauptzweck des `USBConnectionEvent` besteht darin, Entwicklern die Möglichkeit zu geben, auf Änderungen im Status von USB-Geräten zu reagieren. Dies kann das Starten oder Stoppen von Datenübertragungen oder das Aktualisieren der Benutzeroberfläche umfassen.

### Verwendung
Um auf ein `USBConnectionEvent` zu hören, verwenden Sie den `addEventListener`-Befehl in Kombination mit dem spezifischen Event-Typ `connect` oder `disconnect`. 

Hier ist die grundlegende Syntax:

```javascript
navigator.usb.addEventListener('connect', (event) => {
    console.log('USB-Gerät verbunden:', event.device);
});

navigator.usb.addEventListener('disconnect', (event) => {
    console.log('USB-Gerät getrennt:', event.device);
});
```

### Details
- **Event-Typen**: `connect` und `disconnect` sind die beiden Haupttypen von USB-Verbindungsereignissen.
- **Event-Objekt**: Das Ereignisobjekt enthält Informationen zum verbundenen Gerät, einschließlich seiner ID und des Typs.
- **Browserunterstützung**: Die WebUSB-API und die Verwendung von `USBConnectionEvent` sind möglicherweise nicht in allen Browsern unterstützt. Überprüfen Sie die Kompatibilität, bevor Sie diese Funktion in einer produktiven Umgebung verwenden.

## Beispiele
### Beispiel 1: Verbinden eines USB-Geräts

```javascript
navigator.usb.addEventListener('connect', (event) => {
    console.log(`Gerät verbunden: ${event.device.productName}`);
});
```

### Beispiel 2: Trennen eines USB-Geräts

```javascript
navigator.usb.addEventListener('disconnect', (event) => {
    console.log(`Gerät getrennt: ${event.device.productName}`);
});
```

### Beispiel 3: Reaktion auf mehrere Geräte

```javascript
let connectedDevices = [];

navigator.usb.addEventListener('connect', (event) => {
    connectedDevices.push(event.device);
    console.log(`Gerät verbunden: ${event.device.productName}, insgesamt verbundene Geräte: ${connectedDevices.length}`);
});
```

## Erklärung
Ein häufiger Stolperstein bei der Verwendung von `USBConnectionEvent` ist die Browserkompatibilität. Stellen Sie sicher, dass die WebUSB-API in dem von Ihnen verwendeten Browser unterstützt wird. Darüber hinaus ist es wichtig, die Berechtigungen für den Zugriff auf die USB-Geräte zu handhaben, da einige Browser Benutzeraufforderungen anzeigen, wenn auf USB-Geräte zugegriffen wird.

Ein weiterer Punkt ist, dass das Event möglicherweise nicht sofort ausgelöst wird, wenn ein Gerät verbunden oder getrennt wird, insbesondere bei Geräten, die länger zum Initialisieren benötigen. Entwickeln Sie Ihre Anwendung daher so, dass sie robust gegen Verzögerungen und unerwartete Verhaltensweisen ist.

## Einzeiler Zusammenfassung
`USBConnectionEvent` ist ein JavaScript-Ereignis, das es Entwicklern ermöglicht, auf Änderungen des Status von USB-Geräten zu reagieren.