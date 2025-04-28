<!--
Meta Description: # CredentialsContainer in JavaScript: Sicheres Speichern von Anmeldedaten ## Synopsis Der `CredentialsContainer` in JavaScript ermöglicht es Entwickle...
Meta Keywords: anmeldedaten, credentials, die, der, und
-->

# CredentialsContainer in JavaScript: Sicheres Speichern von Anmeldedaten

## Synopsis
Der `CredentialsContainer` in JavaScript ermöglicht es Entwicklern, Benutzerauthentifizierungsdaten sicher zu speichern und zu verwalten. Dies verbessert die Benutzererfahrung durch nahtlose Anmeldungen ohne wiederholtes Eingeben von Anmeldedaten.

## Dokumentation
### Zweck
`CredentialsContainer` ist Teil der Web API und bietet eine standardisierte Schnittstelle, um Anmeldedaten wie Benutzernamen und Passwörter sicher zu speichern. Diese API ist besonders nützlich für Webanwendungen, die eine Authentifizierung erfordern, und bietet eine Möglichkeit, die Benutzeranmeldung zu automatisieren und zu erleichtern.

### Verwendung
Um `CredentialsContainer` zu nutzen, müssen Entwickler die API im Kontext eines Browsers aufrufen, der diese unterstützt. Die Hauptmethoden sind:
- `get()`: Ruft die gespeicherten Anmeldedaten ab.
- `store()`: Speichert neue Anmeldedaten.

### Details
Die `CredentialsContainer` API ist in modernen Browsern implementiert und kann über das globale `navigator` Objekt aufgerufen werden. Die Verwendung der API ist asynchron und basiert auf Promises, was eine reibungslose Handhabung der Anmeldedaten ermöglicht.

```javascript
if ('credentials' in navigator) {
    // Anmeldedaten abrufen
    navigator.credentials.get({ password: true })
        .then(credentials => {
            if (credentials) {
                console.log(`Benutzername: ${credentials.id}`);
            } else {
                console.log('Keine Anmeldedaten gefunden.');
            }
        })
        .catch(err => console.error('Fehler beim Abrufen der Anmeldedaten:', err));
}
```

## Beispiele
### Beispiel 1: Anmeldedaten speichern
```javascript
if ('credentials' in navigator) {
    const credentials = new PasswordCredential({
        id: 'benutzername@example.com',
        password: 'sicheresPasswort'
    });

    navigator.credentials.store(credentials)
        .then(() => console.log('Anmeldedaten erfolgreich gespeichert.'))
        .catch(err => console.error('Fehler beim Speichern der Anmeldedaten:', err));
}
```

### Beispiel 2: Anmeldedaten abrufen
```javascript
if ('credentials' in navigator) {
    navigator.credentials.get({ password: true })
        .then(credentials => {
            if (credentials) {
                console.log(`Benutzername: ${credentials.id}, Passwort: ${credentials.password}`);
            }
        })
        .catch(err => console.error('Fehler:', err));
}
```

## Erklärung
### Häufige Fallstricke
- **Browserunterstützung**: Nicht alle Browser unterstützen die `CredentialsContainer` API. Es ist wichtig, die Browserkompatibilität zu überprüfen, bevor Sie diese API verwenden.
- **Sicherheitsrichtlinien**: Einige Browser haben Sicherheitsrichtlinien, die den Zugriff auf Anmeldedaten einschränken können, insbesondere in unsicheren Umgebungen (HTTP).
- **Fehlende Anmeldedaten**: Wenn keine Anmeldedaten gespeichert sind, gibt die `get()` Methode `null` zurück. Entwickler sollten dies entsprechend behandeln.

## Ein-Satz-Zusammenfassung
Der `CredentialsContainer` in JavaScript erleichtert das sichere Speichern und Abrufen von Anmeldedaten, um die Benutzeranmeldung zu optimieren.