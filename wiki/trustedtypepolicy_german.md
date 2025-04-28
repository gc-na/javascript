<!--
Meta Description: # TrustedTypePolicy in JavaScript: Sicherheit für dynamische Inhalte ## Synopsis TrustedTypePolicy ist eine JavaScript-Schnittstelle, die entwickelt w...
Meta Keywords: die, von, trustedtypepolicy, createhtml, input
-->

# TrustedTypePolicy in JavaScript: Sicherheit für dynamische Inhalte

## Synopsis
TrustedTypePolicy ist eine JavaScript-Schnittstelle, die entwickelt wurde, um das Risiko von Cross-Site-Scripting (XSS) bei der dynamischen Erstellung von HTML-Inhalten zu minimieren. Sie bietet eine Möglichkeit, vertrauenswürdige Typen für die Verarbeitung von Zeichenfolgen zu definieren und zu verwenden.

## Dokumentation

### Zweck
TrustedTypePolicy wurde eingeführt, um Entwicklern zu helfen, sichere Webanwendungen zu erstellen, indem sie sicherstellen, dass nur vertrauenswürdige Inhalte in das DOM eingefügt werden. Es ermöglicht die Definition von Richtlinien für die Verarbeitung von HTML-Elementen und -Attributen, wodurch die Gefahr von XSS-Angriffen verringert wird.

### Verwendung
Um TrustedTypePolicy zu verwenden, müssen Entwickler eine Instanz von TrustedTypePolicy erstellen und definieren, welche Arten von Inhalten als vertrauenswürdig angesehen werden. Hier sind die grundlegenden Schritte zur Implementierung:

1. **Erstellen einer TrustedTypePolicy**:
   ```javascript
   const policy = trustedTypes.createPolicy('meineRichtlinie', {
       createHTML: (input) => {
           return input; // Hier können Sie zusätzliche Validierungen vornehmen
       }
   });
   ```

2. **Verwendung der Richtlinie**:
   Verwenden Sie die Richtlinie, um HTML-Inhalte sicher zu erzeugen:
   ```javascript
   const sichererHTML = policy.createHTML('<div>Hallo Welt</div>');
   document.body.innerHTML = sichererHTML;
   ```

### Details
- **createPolicy(name, { createHTML })**: Diese Methode erstellt eine neue Richtlinie mit dem angegebenen Namen und einer Funktion, die die Eingabe validiert und in einen vertrauenswürdigen Typ konvertiert.
- **createHTML(input)**: Diese Methode nimmt eine Zeichenfolge als Eingabe und gibt eine vertrauenswürdige HTML-Zeichenfolge zurück.
- **trustedTypes**: Ein globales Objekt, das die Trusted Types API bereitstellt.

## Beispiele

### Beispiel 1: Grundlegende Verwendung
```javascript
const policy = trustedTypes.createPolicy('sicher', {
    createHTML: (input) => input // Einfaches Beispiel ohne Validierung
});

const sichererHTML = policy.createHTML('<p>Willkommen!</p>');
document.body.innerHTML = sichererHTML;
```

### Beispiel 2: Mit Validierung
```javascript
const policy = trustedTypes.createPolicy('sicher', {
    createHTML: (input) => {
        // Validierung der Eingabe
        if (typeof input !== 'string') {
            throw new Error('Ungültige Eingabe');
        }
        return input;
    }
});

try {
    const sichererHTML = policy.createHTML('<p>Willkommen!</p>');
    document.body.innerHTML = sichererHTML;
} catch (e) {
    console.error(e.message);
}
```

## Erklärung
Ein häufiges Problem bei der Verwendung von TrustedTypePolicy ist das Missverständnis über die Notwendigkeit der Validierung von Eingaben. Es ist wichtig, sicherzustellen, dass die Eingaben vor der Rückgabe als vertrauenswürdige Typen überprüft werden. Andernfalls können Sicherheitsrisiken entstehen. Ein weiterer Punkt ist, dass nicht alle Browser Trusted Types unterstützen. Daher sollte die Kompatibilität vor der Implementierung überprüft werden.

## Ein-Satz-Zusammenfassung
TrustedTypePolicy ist eine JavaScript-Schnittstelle, die Entwicklern hilft, XSS-Risiken zu minimieren, indem sie vertrauenswürdige Typen für die dynamische Erstellung von HTML-Inhalten definiert.