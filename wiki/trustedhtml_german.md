<!--
Meta Description: # TrustedHTML in JavaScript: Sicheres Einfügen von HTML-Inhalten ## Synopsis TrustedHTML ist ein Typ in JavaScript, der dazu verwendet wird, HTML-Inha...
Meta Keywords: trustedhtml, von, die, sie, html
-->

# TrustedHTML in JavaScript: Sicheres Einfügen von HTML-Inhalten

## Synopsis
TrustedHTML ist ein Typ in JavaScript, der dazu verwendet wird, HTML-Inhalte sicher zu handhaben und einzufügen, um XSS-Angriffe (Cross-Site Scripting) zu verhindern.

## Documentation
TrustedHTML ist Teil der Web-Sicherheitsstandards und wird verwendet, um sicherzustellen, dass dynamisch generierte HTML-Inhalte nicht schädlich sind. Es wird hauptsächlich in Verbindung mit der API `Trusted Types` verwendet, die entwickelt wurde, um die Risiken von XSS-Angriffen zu minimieren.

### Zweck
Der Hauptzweck von TrustedHTML ist es, Entwicklern zu helfen, das Risiko von XSS-Angriffen zu verringern, indem sie nur vertrauenswürdige HTML-Inhalte in ihre Anwendungen einfügen.

### Verwendung
Um TrustedHTML zu verwenden, müssen Sie die `Trusted Types` API aktivieren und definieren, wie und wo HTML-Inhalte in Ihrer Anwendung eingefügt werden. Hier ist ein einfacher Ablauf:

1. Aktivieren Sie Trusted Types in Ihrer Anwendung.
2. Definieren Sie eine `create`-Methode, die TrustedHTML zurückgibt.
3. Verwenden Sie die TrustedHTML-Instanz in Ihren DOM-Manipulationen.

### Details
- **Sicherheit:** TrustedHTML ist ein sicherer Weg, um HTML-Inhalte zu handhaben, da es sicherstellt, dass nur HTML-Inhalte, die durch die definierten Trusted Types erstellt wurden, verwendet werden.
- **Kompatibilität:** Trusted Types werden von modernen Browsern unterstützt, aber Entwickler sollten die Browserkompatibilität überprüfen, bevor sie diese Funktion in Produktionsumgebungen verwenden.

## Beispiele
Hier sind einige grundlegende Beispiele zur Verwendung von TrustedHTML:

### Beispiel 1: Erstellen von TrustedHTML
```javascript
// Aktivierung von Trusted Types
if (window.TrustedTypes) {
  TrustedTypes.createPolicy('default', {
    createHTML: (input) => {
      return input; // Hier sollten Sie eine Validierung einfügen
    }
  });
}

// Verwendung von TrustedHTML
const safeHTML = TrustedTypes.getPolicy('default').createHTML('<div>Inhalt</div>');
document.body.innerHTML = safeHTML;
```

### Beispiel 2: Einfügen von TrustedHTML in das DOM
```javascript
const safeHTML = TrustedTypes.getPolicy('default').createHTML('<p>Willkommen!</p>');
document.querySelector('#container').innerHTML = safeHTML;
```

## Explanation
Ein häufiger Fehler ist, dass Entwickler vergessen, die Trusted Types-Policy korrekt zu definieren, wodurch sie anfällig für XSS-Angriffe werden. Stellen Sie sicher, dass alle Eingaben validiert werden, bevor Sie TrustedHTML verwenden. 

Ein weiterer Punkt ist, dass TrustedHTML nicht automatisch alle HTML-Inhalte sicher macht. Es liegt in der Verantwortung des Entwicklers, sicherzustellen, dass nur vertrauenswürdige und geprüfte Inhalte in die Anwendung eingefügt werden.

## One Line Summary
TrustedHTML ist ein sicherer Typ in JavaScript zur Handhabung von HTML-Inhalten, der XSS-Angriffe verhindert.