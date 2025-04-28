<!--
Meta Description: # SubtleCrypto in JavaScript: Sicherheit und Verschlüsselung mit modernen Webtechnologien ## Synopsis SubtleCrypto ist ein Web-API, das in JavaScript ...
Meta Keywords: die, und, von, subtlecrypto, crypto
-->

# SubtleCrypto in JavaScript: Sicherheit und Verschlüsselung mit modernen Webtechnologien

## Synopsis
SubtleCrypto ist ein Web-API, das in JavaScript verwendet wird, um kryptografische Operationen durchzuführen und die Sicherheit von Webanwendungen zu erhöhen. Es bietet Funktionen zur Verschlüsselung, Entschlüsselung, Signierung und Verifizierung von Daten.

## Dokumentation

### Zweck
SubtleCrypto ist Teil der Web Cryptography API und ermöglicht Entwicklern, kryptografische Operationen direkt im Browser durchzuführen. Diese API ist wichtig für die Sicherstellung der Datenintegrität und Vertraulichkeit in modernen Webanwendungen.

### Verwendung
SubtleCrypto wird hauptsächlich über das `window.crypto.subtle` Objekt aufgerufen. Die API unterstützt eine Vielzahl von kryptografischen Algorithmen und kann für Aufgaben wie Hashing, Verschlüsselung und digitale Signaturen verwendet werden.

### Details
- **Methoden**: Zu den Hauptmethoden gehören:
  - `encrypt`: Verschlüsselt Daten mit einem angegebenen Algorithmus.
  - `decrypt`: Entschlüsselt verschlüsselte Daten.
  - `sign`: Erstellt eine digitale Signatur für die gegebenen Daten.
  - `verify`: Überprüft die Gültigkeit einer digitalen Signatur.
  - `digest`: Erstellt einen Hash aus den gegebenen Daten.

- **Algorithmen**: Unterstützte Algorithmen umfassen AES, RSA, HMAC und viele mehr. Die Wahl des Algorithmus hängt von den spezifischen Anforderungen der Anwendung ab.

## Beispiele

### Beispiel 1: Hashing von Daten
```javascript
const data = new TextEncoder().encode("Hello, World!");
crypto.subtle.digest("SHA-256", data).then(hash => {
    console.log(new Uint8Array(hash));
});
```

### Beispiel 2: Verschlüsselung und Entschlüsselung
```javascript
const keyMaterial = await crypto.subtle.importKey(
    "raw",
    new TextEncoder().encode("password"),
    "PBKDF2",
    false,
    ["deriveBits", "deriveKey"]
);

const key = await crypto.subtle.deriveKey(
    { name: "PBKDF2", salt: new Uint8Array(16), iterations: 100000, hash: "SHA-256" },
    keyMaterial,
    { name: "AES-GCM", length: 256 },
    false,
    ["encrypt", "decrypt"]
);

// Verschlüsseln
const iv = crypto.getRandomValues(new Uint8Array(12));
const encrypted = await crypto.subtle.encrypt(
    { name: "AES-GCM", iv: iv },
    key,
    new TextEncoder().encode("Geheime Nachricht")
);

// Entschlüsseln
const decrypted = await crypto.subtle.decrypt(
    { name: "AES-GCM", iv: iv },
    key,
    encrypted
);
console.log(new TextDecoder().decode(decrypted));
```

## Erklärung
- **Kompatibilität**: SubtleCrypto ist in den meisten modernen Browsern verfügbar, jedoch nicht in Internet Explorer. Es ist wichtig, die Kompatibilität zu überprüfen, bevor Sie die API verwenden.
- **Sicherheit**: Bei der Verwendung von SubtleCrypto sollten Entwickler sicherstellen, dass sie bewährte Sicherheitspraktiken befolgen, wie z.B. die Verwendung von sicheren Schlüsseln und die richtige Handhabung von Initialisierungsvektoren (IVs).
- **Asynchrone Natur**: Die meisten Methoden von SubtleCrypto sind asynchron und geben ein Promise zurück. Entwickler sollten mit `async/await` oder `then/catch` arbeiten, um die Ergebnisse zu verarbeiten.

## Einzeilensummary
SubtleCrypto ist eine leistungsstarke Web-API in JavaScript, die Entwicklern ermöglicht, sicherheitsrelevante kryptografische Operationen im Browser durchzuführen.