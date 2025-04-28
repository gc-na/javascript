<!--
Meta Description: # WakeLock in JavaScript: Bildschirmwachhaltung für webbasierte Anwendungen ## Synopsis Die WakeLock-API in JavaScript ermöglicht es Entwicklern, den ...
Meta Keywords: die, wakelock, wake, den, api
-->

# WakeLock in JavaScript: Bildschirmwachhaltung für webbasierte Anwendungen

## Synopsis
Die WakeLock-API in JavaScript ermöglicht es Entwicklern, den Bildschirm eines Geräts aktiv zu halten, um zu verhindern, dass er in den Energiesparmodus wechselt. Dies ist besonders nützlich für Anwendungen, die kontinuierlich Informationen anzeigen müssen, wie z.B. Präsentationen oder Überwachungsdashboards.

## Dokumentation
### Zweck
Die WakeLock-API wurde entwickelt, um die Benutzererfahrung zu verbessern, indem sie sicherstellt, dass der Bildschirm eines Geräts nicht in den Standby-Modus wechselt, während eine Anwendung aktiv ist. Dies ist entscheidend für Anwendungen, die eine ununterbrochene Anzeige benötigen, um die Interaktivität zu gewährleisten.

### Verwendung
Um die WakeLock-API zu verwenden, müssen Entwickler die `navigator.wakeLock`-Schnittstelle nutzen. Hierbei gibt es zwei Hauptmethoden: `request()` und `release()`, die verwendet werden, um einen Wake Lock anzufordern und freizugeben.

#### Syntax
```javascript
const wakeLock = await navigator.wakeLock.request('screen');
```

### Details
- **Typen von Wake Locks**: Aktuell unterstützt die API hauptsächlich den `'screen'`-Typ, der den Bildschirm wach hält.
- **Fehlerbehandlung**: Entwickler sollten mit Fehlern umgehen, die auftreten können, wenn die Anforderung eines Wake Locks fehlschlägt, z.B. wenn der Benutzer die Berechtigung verweigert.
- **Automatische Freigabe**: Wake Locks werden automatisch freigegeben, wenn die Seite entladen wird oder der Benutzer die Seite verlässt.

## Beispiele
### Einfaches Beispiel
```javascript
let wakeLock = null;

async function requestWakeLock() {
    try {
        wakeLock = await navigator.wakeLock.request('screen');
        console.log('Wake Lock aktiviert');
    } catch (err) {
        console.error(`${err.name}, ${err.message}`);
    }
}

async function releaseWakeLock() {
    if (wakeLock !== null) {
        await wakeLock.release();
        wakeLock = null;
        console.log('Wake Lock freigegeben');
    }
}

// Wake Lock anfordern
requestWakeLock();

// Wake Lock freigeben, z.B. bei einem Button-Klick
document.getElementById('releaseButton').addEventListener('click', releaseWakeLock);
```

## Erklärung
### Häufige Stolpersteine
- **Berechtigungen**: Stellen Sie sicher, dass die Anwendung eine sichere Umgebung (HTTPS) verwendet, da Wake Lock nur in sicheren Kontexten verfügbar ist.
- **Browserunterstützung**: Die WakeLock-API wird nicht von allen Browsern unterstützt. Überprüfen Sie die Kompatibilität, bevor Sie die API verwenden.
- **Benutzerinteraktion**: Einige Browser erlauben das Anfordern eines Wake Locks nur als Reaktion auf eine Benutzerinteraktion (z.B. einen Mausklick).

### Zusätzliche Hinweise
- Es ist ratsam, den Wake Lock nur solange aktiv zu halten, wie es unbedingt notwendig ist, um den Akkuverbrauch zu minimieren.
- Überwachen Sie den Zustand des Wake Locks, um sicherzustellen, dass er in den gewünschten Situationen aktiv bleibt und freigegeben wird, wenn er nicht mehr benötigt wird.

## Ein-Satz-Zusammenfassung
Die WakeLock-API in JavaScript ermöglicht es Entwicklern, den Bildschirm eines Geräts wach zu halten, um die Benutzererfahrung von webbasierenden Anwendungen zu verbessern.