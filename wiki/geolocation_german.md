<!--
Meta Description: # Geolocation in JavaScript: Standortbestimmung im Web ## Synopsis Die Geolocation-API in JavaScript ermöglicht es Webanwendungen, den geografischen S...
Meta Keywords: die, geolocation, position, der, error
-->

# Geolocation in JavaScript: Standortbestimmung im Web

## Synopsis
Die Geolocation-API in JavaScript ermöglicht es Webanwendungen, den geografischen Standort eines Benutzers präzise zu bestimmen und zu verwenden. Diese Funktion ist besonders nützlich für standortbasierte Dienste, wie z.B. Kartenanwendungen oder lokale Wetterdienste.

## Dokumentation

### Zweck
Die Geolocation-API ermöglicht Entwicklern den Zugriff auf die Standortdaten des Benutzers, die durch GPS, Wi-Fi oder Mobilfunknetzwerke bestimmt werden können. Dies eröffnet zahlreiche Anwendungsmöglichkeiten, darunter Standortverfolgung, benutzerspezifische Inhalte oder Navigation.

### Verwendung
Um die Geolocation-API in JavaScript zu verwenden, müssen Entwickler die `navigator.geolocation`-Objekte nutzen, die in modernen Webbrowsern verfügbar sind. Der Zugriff auf Standortdaten erfolgt in der Regel über die Methoden `getCurrentPosition()` und `watchPosition()`.

### Details
- **getCurrentPosition(success, error, options)**: Diese Methode ruft die aktuelle Position des Benutzers ab. Der `success`-Callback erhält ein `Position`-Objekt, das die Koordinaten und andere Standortinformationen enthält. Der `error`-Callback wird aufgerufen, wenn ein Fehler auftritt.
- **watchPosition(success, error, options)**: Diese Methode beobachtet Änderungen der Position des Benutzers und ruft den `success`-Callback jedes Mal auf, wenn sich der Standort ändert.
- **options**: Ein optionales Objekt, das Parameter wie `enableHighAccuracy`, `timeout` und `maximumAge` festlegt.

## Beispiele

### Beispiel 1: Aktuelle Position abrufen
```javascript
if (navigator.geolocation) {
    navigator.geolocation.getCurrentPosition(function(position) {
        console.log("Latitude: " + position.coords.latitude);
        console.log("Longitude: " + position.coords.longitude);
    }, function(error) {
        console.error("Fehler beim Abrufen der Position: " + error.message);
    });
} else {
    console.log("Geolocation wird in diesem Browser nicht unterstützt.");
}
```

### Beispiel 2: Standortveränderungen überwachen
```javascript
if (navigator.geolocation) {
    navigator.geolocation.watchPosition(function(position) {
        console.log("Neue Position: ");
        console.log("Latitude: " + position.coords.latitude);
        console.log("Longitude: " + position.coords.longitude);
    }, function(error) {
        console.error("Fehler beim Überwachen der Position: " + error.message);
    });
} else {
    console.log("Geolocation wird in diesem Browser nicht unterstützt.");
}
```

## Erklärung
- **Berechtigungen**: Der Browser fordert den Benutzer um Erlaubnis, den Standort zu teilen. Diese Berechtigung muss erteilt werden, andernfalls schlägt der Zugriff fehl.
- **Genauigkeit**: Die Genauigkeit der Standortbestimmung hängt von den verwendeten Technologien ab. GPS bietet die höchste Genauigkeit, während Wi-Fi und Mobilfunknetze weniger präzise sein können.
- **Sicherheit**: Die Geolocation-API kann nur über HTTPS oder auf localhost verwendet werden, um den Datenschutz der Benutzer zu gewährleisten.
- **Fehlerbehandlung**: Entwickler sollten die einzelnen Fehlercodes, die im `error`-Callback bereitgestellt werden, behandeln, um den Benutzern hilfreiche Informationen zu geben.

## Ein-Satz-Zusammenfassung
Die Geolocation-API in JavaScript ermöglicht es Webanwendungen, den aktuellen geografischen Standort des Benutzers präzise zu bestimmen und in Echtzeit zu verfolgen.