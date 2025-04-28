<!--
Meta Description: # PasswordCredential in JavaScript: Sichere Anmeldeinformationen verwalten ## Synopsis `PasswordCredential` ist eine Web API in JavaScript, die es Ent...
Meta Keywords: credential, anmeldeinformationen, passwordcredential, die, von
-->

# PasswordCredential in JavaScript: Sichere Anmeldeinformationen verwalten

## Synopsis
`PasswordCredential` ist eine Web API in JavaScript, die es Entwicklern ermöglicht, Benutzeranmeldeinformationen sicher zu erstellen, zu speichern und zu verwalten. Sie erleichtert die Implementierung von sicheren Anmeldeverfahren in Webanwendungen.

## Dokumentation
`PasswordCredential` ist ein Teil der Credential Management API, die dazu dient, Benutzern eine nahtlose und sichere Anmeldeerfahrung zu bieten. Mit `PasswordCredential` können Entwickler Anmeldeinformationen für Benutzer in Form von Benutzernamen und Passwörtern sicher speichern und abrufen.

### Zweck
Das Hauptziel von `PasswordCredential` ist es, die Sicherheit und Benutzerfreundlichkeit bei der Verwaltung von Anmeldeinformationen zu erhöhen. Es ermöglicht Webanwendungen, Benutzerdaten lokal zu speichern und zu verwenden, ohne dass diese Daten im Klartext gespeichert werden müssen.

### Verwendung
Um `PasswordCredential` zu verwenden, müssen Sie die API wie folgt implementieren:

1. **Erstellen einer `PasswordCredential`-Instanz**:
   ```javascript
   const credential = new PasswordCredential({
       id: 'benutzer@example.com',
       password: 'sicheresPasswort123'
   });
   ```

2. **Speichern von Anmeldeinformationen**:
   ```javascript
   navigator.credentials.store(credential)
       .then(() => {
           console.log('Anmeldeinformationen gespeichert!');
       })
       .catch((error) => {
           console.error('Fehler beim Speichern der Anmeldeinformationen:', error);
       });
   ```

3. **Abrufen von Anmeldeinformationen**:
   ```javascript
   navigator.credentials.get({ password: true })
       .then((credential) => {
           if (credential) {
               console.log('Benutzername:', credential.id);
               console.log('Passwort:', credential.password);
           } else {
               console.log('Keine Anmeldeinformationen gefunden.');
           }
       })
       .catch((error) => {
           console.error('Fehler beim Abrufen der Anmeldeinformationen:', error);
       });
   ```

## Beispiele
### Beispiel 1: Speichern der Anmeldeinformationen
```javascript
const credential = new PasswordCredential({
   id: 'user@example.com',
   password: 'examplePassword'
});

navigator.credentials.store(credential)
   .then(() => {
       console.log('Anmeldeinformationen erfolgreich gespeichert.');
   });
```

### Beispiel 2: Abrufen von Anmeldeinformationen
```javascript
navigator.credentials.get({ password: true })
   .then(credential => {
       if (credential) {
           console.log('Benutzername:', credential.id);
           console.log('Passwort:', credential.password);
       }
   });
```

## Erklärung
Ein häufiger Stolperstein bei der Verwendung von `PasswordCredential` kann die Unterstützung in verschiedenen Browsern sein. Es ist wichtig, die Kompatibilität zu überprüfen, da nicht alle Browser die Credential Management API unterstützen. 

Ein weiterer Punkt ist, dass die `store`-Methode nur funktioniert, wenn der Benutzer die Berechtigung erteilt hat. Stellen Sie sicher, dass Sie die Benutzererfahrung im Auge behalten und den Benutzer um Erlaubnis bitten, bevor Sie versuchen, Anmeldeinformationen zu speichern.

## Ein-Satz-Zusammenfassung
`PasswordCredential` ist eine JavaScript-API zur sicheren Verwaltung von Benutzeranmeldeinformationen in Webanwendungen.