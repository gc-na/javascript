<!--
Meta Description: # CloseEvent in JavaScript: Ein umfassender Leitfaden ## Synopsis Der `CloseEvent` in JavaScript ist ein Ereignis, das auftritt, wenn eine WebSocket-V...
Meta Keywords: den, closeevent, ein, das, websocket
-->

# CloseEvent in JavaScript: Ein umfassender Leitfaden

## Synopsis
Der `CloseEvent` in JavaScript ist ein Ereignis, das auftritt, wenn eine WebSocket-Verbindung geschlossen wird. Es ermöglicht Entwicklern, auf Abschlussereignisse zu reagieren und entsprechende Maßnahmen zu ergreifen.

## Dokumentation
### Zweck
`CloseEvent` wird verwendet, um Informationen über das Schließen einer WebSocket-Verbindung bereitzustellen. Dies ist besonders nützlich, um den Benutzer über den Verbindungsstatus zu informieren und gegebenenfalls neue Verbindungsversuche zu starten.

### Verwendung
Ein `CloseEvent` wird automatisch generiert, wenn eine WebSocket-Verbindung geschlossen wird, sei es durch den Server, den Client oder aufgrund eines Fehlers. Es kann in einem `onclose`-Event-Handler verarbeitet werden. Der `CloseEvent` enthält wichtige Informationen wie den Statuscode und den Grund für das Schließen.

### Details
- **Eigenschaften:**
  - `code`: Ein numerischer Wert, der den Statuscode des Schließereignisses angibt.
  - `reason`: Eine optionale Zeichenkette, die den Grund für das Schließen beschreibt.
  - `wasClean`: Ein boolescher Wert, der angibt, ob die Verbindung ordentlich geschlossen wurde.

### Beispiel
Hier ist ein einfaches Beispiel zur Verwendung von `CloseEvent` in einem WebSocket:

```javascript
const socket = new WebSocket('ws://example.com/socket');

socket.onopen = function(event) {
    console.log('Verbindung hergestellt!');
};

socket.onclose = function(event) {
    console.log('Verbindung geschlossen!');
    console.log('Code:', event.code);
    console.log('Grund:', event.reason);
    console.log('War der Schließvorgang ordentlich?', event.wasClean);
};

socket.onerror = function(error) {
    console.error('WebSocket-Fehler:', error);
};
```

## Erklärung
Ein häufiger Fehler besteht darin, den `onclose`-Handler nicht korrekt zu definieren. Dies kann dazu führen, dass wichtige Informationen über das Schließen der Verbindung verloren gehen. Es ist auch wichtig, den Statuscode und die Gründe für das Schließen zu überprüfen, um Fehler zu diagnostizieren und die Benutzererfahrung zu verbessern. Beachten Sie, dass die `reason`-Eigenschaft nicht immer gesetzt ist und in einigen Fällen leer sein kann.

## Einzeilige Zusammenfassung
`CloseEvent` in JavaScript ermöglicht Entwicklern, auf das Schließen von WebSocket-Verbindungen zu reagieren und wichtige Informationen über den Schließvorgang bereitzustellen.