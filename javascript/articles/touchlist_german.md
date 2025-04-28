<!--
Meta Description: # TouchList in JavaScript: Eine umfassende Anleitung ## Synopsis Die `TouchList` ist ein JavaScript-Objekt, das eine Sammlung von Touch-Punkten beschr...
Meta Keywords: die, touchlist, touch, auf, der
-->

# TouchList in JavaScript: Eine umfassende Anleitung

## Synopsis
Die `TouchList` ist ein JavaScript-Objekt, das eine Sammlung von Touch-Punkten beschreibt, die von Touch-Ereignissen wie Berührungen auf einem Touchscreen-Gerät erzeugt werden. Es wird häufig in der Webentwicklung verwendet, um die Interaktivität und Benutzererfahrung auf mobilen Geräten zu verbessern.

## Dokumentation
Die `TouchList`-Schnittstelle ist Teil der Touch-Events-Spezifikation und ermöglicht den Zugriff auf eine Liste von `Touch`-Objekten, die Informationen über aktuelle Berührungen auf dem Bildschirm enthalten. Diese Informationen umfassen Details wie die Koordinaten der Berührung, den Berührungsstatus und die Identifikation der Berührung.

### Zweck
Die `TouchList` wird verwendet, um mehrere Berührungen gleichzeitig zu verwalten und zu analysieren, was für Gestensteuerungen und andere interaktive Funktionen auf Touch-fähigen Geräten wichtig ist.

### Verwendung
Um eine `TouchList` zu verwenden, müssen Sie ein Touch-Ereignis abfangen, das durch Benutzerinteraktionen wie `touchstart`, `touchmove` oder `touchend` ausgelöst wird. Innerhalb des Ereignishandlers können Sie auf die `touches`-, `targetTouches`- und `changedTouches`-Eigenschaften des Ereignisobjekts zugreifen, die jeweils eine `TouchList` zurückgeben.

### Eigenschaften
- `length`: Gibt die Anzahl der Berührungspunkte in der `TouchList` zurück.
- `item(index)`: Gibt das `Touch`-Objekt am angegebenen Index zurück.

## Beispiele
Hier sind einige grundlegende Beispiele, wie die `TouchList` in JavaScript verwendet wird:

### Beispiel 1: Zugriff auf Touch-Punkte
```javascript
document.addEventListener('touchstart', function(event) {
    const touchList = event.touches; // Zugriff auf die TouchList
    console.log('Anzahl der Berührungen: ', touchList.length);
    
    for (let i = 0; i < touchList.length; i++) {
        console.log(`Touch ${i}:`, touchList[i]);
    }
});
```

### Beispiel 2: Verfolgen von Touch-Bewegungen
```javascript
document.addEventListener('touchmove', function(event) {
    const touch = event.touches[0]; // Zugriff auf den ersten Touch
    console.log(`Berührung bewegt zu: (${touch.clientX}, ${touch.clientY})`);
});
```

## Erklärung
Ein häufiges Problem bei der Verwendung der `TouchList` ist das Missverständnis, dass `touches`, `targetTouches` und `changedTouches` identisch sind. Diese Eigenschaften haben unterschiedliche Bedeutungen:
- `touches`: Alle aktuellen Berührungen auf dem Bildschirm.
- `targetTouches`: Berührungen, die das Ziel-Element betreffen.
- `changedTouches`: Berührungen, die sich seit dem letzten Ereignis geändert haben.

Ein weiterer wichtiger Punkt ist, dass die `TouchList` nur in den entsprechenden Touch-Events verfügbar ist. Wenn Sie versuchen, sie außerhalb dieser Kontexte zu verwenden, wird sie nicht ordnungsgemäß funktionieren.

## Einzeiler Zusammenfassung
Die `TouchList` in JavaScript ermöglicht den Zugriff auf eine Sammlung von aktuellen Touch-Punkten für eine verbesserte Interaktivität auf Touchscreen-Geräten.