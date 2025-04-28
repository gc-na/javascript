<!--
Meta Description: # Die `close`-Methode in JavaScript: Anwendung und Bedeutung ## Synopsis Die `close`-Methode in JavaScript wird verwendet, um ein geöffnete Fenster od...
Meta Keywords: websocket, close, schließen, der, die
-->

# Die `close`-Methode in JavaScript: Anwendung und Bedeutung

## Synopsis
Die `close`-Methode in JavaScript wird verwendet, um ein geöffnete Fenster oder einen Tab zu schließen. Sie ist Teil der Window- und WebSocket-Objekte und spielt eine wichtige Rolle bei der Verwaltung von Browserfenstern und Netzwerkverbindungen.

## Dokumentation
Die `close`-Methode wird hauptsächlich in zwei Kontexten verwendet: beim Schließen von Fenstern oder Tabs und beim Beenden von WebSocket-Verbindungen.

### Verwendung der `close`-Methode

1. **Fenster/Tab schließen**:
   - Syntax: `window.close();`
   - Diese Methode schließt das aktuell geöffnete Fenster, wenn es durch ein Skript geöffnet wurde.

2. **WebSocket schließen**:
   - Syntax: `webSocket.close();`
   - Hiermit wird eine WebSocket-Verbindung ordnungsgemäß beendet.

### Details
- **Fenster schließen**: Die `close`-Methode kann nur Fenster schließen, die durch `window.open()` erstellt wurden. Wenn das Fenster nicht durch ein Skript geöffnet wurde, wird der Aufruf von `window.close()` ignoriert.
- **WebSocket schließen**: Beim Schließen einer WebSocket-Verbindung kann optional ein Statuscode und ein Grund angegeben werden, um den Grund für das Schließen zu erläutern. Beispiel: `webSocket.close(1000, "Normal closure");`

## Beispiele

### Beispiel 1: Fenster schließen
```javascript
let newWindow = window.open("https://example.com");
newWindow.close(); // Schließt das neu geöffnete Fenster
```

### Beispiel 2: WebSocket schließen
```javascript
let webSocket = new WebSocket("wss://example.com/socket");
webSocket.onopen = function() {
    console.log("WebSocket verbunden");
    webSocket.close(1000, "Normale Schließung");
};
webSocket.onclose = function(event) {
    console.log("WebSocket geschlossen:", event);
};
```

## Erklärung
Bei der Verwendung der `close`-Methode gibt es einige häufige Fallstricke:

- **Erlaubnis zum Schließen**: Ein Skript kann ein Fenster nur schließen, wenn es dieses selbst geöffnet hat. Das bedeutet, dass der Aufruf von `window.close()` für Fenster, die von einem Benutzer manuell geöffnet wurden, keine Auswirkung hat.
- **WebSocket-Statuscodes**: Bei der Nutzung der `close`-Methode für WebSocket-Verbindungen ist es wichtig, die richtigen Statuscodes zu verwenden, da dies die Art und Weise beeinflussen kann, wie der Server das Schließen der Verbindung interpretiert. Die häufigsten Statuscodes sind:
  - `1000`: Normale Schließung
  - `1001`: Geplant geschlossen (z. B. Server wird heruntergefahren)

## Ein-Satz-Zusammenfassung
Die `close`-Methode in JavaScript dient zum Schließen von Fenstern und Beenden von WebSocket-Verbindungen und erfordert bestimmte Bedingungen zur ordnungsgemäßen Funktion.