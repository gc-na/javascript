<!--
Meta Description: # PushSubscription in JavaScript: Alles, was Sie wissen müssen ## Synopsis Die `PushSubscription`-Schnittstelle in JavaScript ermöglicht es Webanwendu...
Meta Keywords: die, pushsubscription, subscription, push, benachrichtigungen
-->

# PushSubscription in JavaScript: Alles, was Sie wissen müssen

## Synopsis
Die `PushSubscription`-Schnittstelle in JavaScript ermöglicht es Webanwendungen, Push-Benachrichtigungen an Benutzer zu senden, selbst wenn die Anwendung nicht aktiv ist. Diese Funktion ist ein wesentlicher Bestandteil der Web-Push-API und verbessert das Benutzerengagement erheblich.

## Dokumentation
Die `PushSubscription`-Schnittstelle repräsentiert die Abonnement-Informationen für Push-Benachrichtigungen. Sie wird in der Regel von der `ServiceWorker`-API verwendet, um Benutzern die Möglichkeit zu geben, Benachrichtigungen von einer bestimmten Quelle zu empfangen.

### Zweck
Der Hauptzweck von `PushSubscription` ist es, Benutzern eine einfache Möglichkeit zu bieten, Benachrichtigungen zu abonnieren, die von einem Server gesendet werden. Dies ermöglicht es Entwicklern, relevante Informationen, Updates oder Angebote direkt an die Benutzer zu senden.

### Verwendung
Um eine `PushSubscription` zu erstellen, müssen Sie zunächst einen Service Worker registrieren und dann die `PushManager.subscribe`-Methode aufrufen. Die `PushSubscription`-Instanz enthält Informationen wie den Endpunkt, die Berechtigungen und die Authentifizierung.

### Details
- **Attribute**:
  - `endpoint`: Die URL, an die die Push-Nachrichten gesendet werden.
  - `expirationTime`: Der Zeitpunkt, zu dem das Abonnement abläuft (sofern nicht gesetzt, bleibt es unbefristet).
  - `keys`: Die Schlüssel, die zur Authentifizierung und Verschlüsselung der Nachrichten verwendet werden.

## Beispiele

### Beispiel 1: Abonnieren von Push-Benachrichtigungen
```javascript
navigator.serviceWorker.register('/service-worker.js')
  .then(function(registration) {
    return registration.pushManager.subscribe({
      userVisibleOnly: true,
      applicationServerKey: urlB64ToUint8Array('YOUR_PUBLIC_VAPID_KEY')
    });
  })
  .then(function(subscription) {
    console.log('Subscribed:', subscription);
  })
  .catch(function(error) {
    console.error('Subscription failed:', error);
  });
```

### Beispiel 2: Abrufen von Abonnements
```javascript
navigator.serviceWorker.ready.then(function(registration) {
  return registration.pushManager.getSubscription();
}).then(function(subscription) {
  if (subscription) {
    console.log('Existing subscription:', subscription);
  } else {
    console.log('No subscription found.');
  }
});
```

## Erklärung
Ein häufiger Stolperstein beim Arbeiten mit `PushSubscription` ist die Notwendigkeit, die richtigen Berechtigungen vom Benutzer zu erhalten. Benutzer müssen der Anwendung erlauben, Push-Benachrichtigungen zu senden. Auch die Verwendung des richtigen VAPID-Schlüssels ist entscheidend, um die Authentifizierung zu gewährleisten. Zudem kann die Nichtverfügbarkeit des Service Workers in bestimmten Browsern zu Problemen führen.

Eine weitere wichtige Anmerkung ist, dass Abonnements ablaufen können, wenn sie nicht aktiv genutzt werden, und Entwickler sollten Mechanismen implementieren, um inaktive Abonnements regelmäßig zu überprüfen und zu erneuern.

## Ein Satz Zusammenfassung
Die `PushSubscription`-Schnittstelle in JavaScript ermöglicht es Webanwendungen, Benutzern Push-Benachrichtigungen zu senden und deren Abonnements zu verwalten.