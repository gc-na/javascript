<!--
Meta Description: # JavaScript und Krypto: Ein Leitfaden zur Nutzung der Krypto-API ## Synopsis Die Krypto-API in JavaScript bietet Entwicklern eine leistungsstarke Mög...
Meta Keywords: crypto, const, api, von, die
-->

# JavaScript und Krypto: Ein Leitfaden zur Nutzung der Krypto-API

## Synopsis
Die Krypto-API in JavaScript bietet Entwicklern eine leistungsstarke Möglichkeit zur Implementierung kryptografischer Funktionen, einschließlich Hashing, Verschlüsselung und der Generierung von sicheren Zufallszahlen.

## Dokumentation

### Zweck
Die Krypto-API in JavaScript ist ein integraler Bestandteil der Web Crypto-API, die es Entwicklern ermöglicht, kryptografische Operationen direkt im Browser durchzuführen. Diese API bietet Funktionen zur Erzeugung von Schlüsseln, zur Hashing von Daten, zur Verschlüsselung und Entschlüsselung von Informationen sowie zur Erzeugung sicherer Zufallszahlen.

### Verwendung
Die Krypto-API ist in modernen Webbrowsern verfügbar (außer Internet Explorer) und kann über das `window.crypto`-Objekt aufgerufen werden. Um die API zu nutzen, müssen Sie zunächst sicherstellen, dass Ihr Skript im Kontext einer sicheren Umgebung (HTTPS) ausgeführt wird.

### Details
Die Krypto-API umfasst mehrere wichtige Funktionen, darunter:

- **Key Generation**: Erstellen kryptografischer Schlüssel mit `window.crypto.subtle.generateKey()`.
- **Hashing**: Hashen von Daten mit `window.crypto.subtle.digest()`.
- **Verschlüsselung**: Verschlüsseln von Daten mit `window.crypto.subtle.encrypt()`.
- **Entschlüsselung**: Entschlüsseln von Daten mit `window.crypto.subtle.decrypt()`.
- **Zufallszahlen**: Erzeugen sicherer Zufallszahlen mit `window.crypto.getRandomValues()`.

## Beispiele

### Beispiel 1: Hashing von Daten
```javascript
async function hashData(data) {
    const encoder = new TextEncoder();
    const dataBuffer = encoder.encode(data);
    const hashBuffer = await crypto.subtle.digest('SHA-256', dataBuffer);
    const hashArray = Array.from(new Uint8Array(hashBuffer));
    const hashHex = hashArray.map(b => b.toString(16).padStart(2, '0')).join('');
    return hashHex;
}

hashData("Hallo, Welt!").then(console.log); // Beispielausgabe: "a591a6d40bf420404a011733cfb7b190d62c65bf0bcda190e4b8b11d0f600bfb"
```

### Beispiel 2: Erzeugen sicherer Zufallszahlen
```javascript
const array = new Uint32Array(10);
window.crypto.getRandomValues(array);
console.log(array); // Beispielausgabe: [1234567890, 987654321, ...]
```

### Beispiel 3: Verschlüsseln und Entschlüsseln von Daten
```javascript
async function encryptData(data, key) {
    const encoder = new TextEncoder();
    const dataBuffer = encoder.encode(data);
    const iv = window.crypto.getRandomValues(new Uint8Array(12));
    const encryptedData = await crypto.subtle.encrypt(
        { name: "AES-GCM", iv: iv },
        key,
        dataBuffer
    );
    return { iv, encryptedData };
}

// Beispiel zur Verwendung
(async () => {
    const key = await crypto.subtle.generateKey({ name: "AES-GCM", length: 256 }, true, ["encrypt", "decrypt"]);
    const encrypted = await encryptData("Geheime Nachricht", key);
    console.log(encrypted);
})();
```

## Erklärung
Ein häufiger Stolperstein bei der Verwendung der Krypto-API ist das Verständnis der verschiedenen Algorithmen und deren Parameter. Es ist wichtig, den richtigen Algorithmus für Ihre spezifischen Anforderungen auszuwählen. Darüber hinaus müssen Sie bei der Verwendung von asynchronen Funktionen sicherstellen, dass Sie `await` korrekt verwenden, um die Promise-Resultate abzuwarten.

Ein weiterer Punkt ist, dass die API im sicheren Kontext (HTTPS) betrieben werden muss. Andernfalls stehen Ihnen die Funktionen nicht zur Verfügung.

## Ein-Satz-Zusammenfassung
Die Krypto-API in JavaScript ermöglicht Entwicklern, robuste kryptografische Funktionen zur Sicherung von Daten direkt im Browser zu implementieren.