<!--
Meta Description: # FinalizationRegistry in JavaScript: Ein umfassender Leitfaden ## Synopsis Der `FinalizationRegistry` ist ein nützliches JavaScript-Feature, das es E...
Meta Keywords: der, finalizationregistry, wird, die, ist
-->

# FinalizationRegistry in JavaScript: Ein umfassender Leitfaden

## Synopsis
Der `FinalizationRegistry` ist ein nützliches JavaScript-Feature, das es Entwicklern ermöglicht, Ressourcen zu verwalten, die nach der Garbage Collection von Objekten freigegeben werden. Dies ist besonders hilfreich, um sicherzustellen, dass bestimmte Aufräumoperationen ausgeführt werden, wenn ein Objekt nicht mehr benötigt wird.

## Dokumentation
Der `FinalizationRegistry` ist eine eingebaute JavaScript-Klasse, die eine Möglichkeit bietet, Callbacks zu registrieren, die aufgerufen werden, wenn ein bestimmtes Objekt von der Garbage Collection gesammelt wird. Diese Funktionalität ist besonders wertvoll in Situationen, in denen es notwendig ist, Aufräumarbeiten durchzuführen, wie das Freigeben von Ressourcen oder das Entfernen von Event-Listener.

### Zweck
Der `FinalizationRegistry` ermöglicht es Entwicklern, sich um Objekte zu kümmern, die aufgrund der Garbage Collection nicht mehr existieren, und dabei sicherzustellen, dass bestimmte Logik ausgeführt wird, wenn diese Objekte entfernt werden.

### Verwendung
Der `FinalizationRegistry` wird mit dem Konstruktor `new FinalizationRegistry(cleanupCallback)` erstellt, wobei `cleanupCallback` eine Funktion ist, die aufgerufen wird, wenn das registrierte Zielobjekt gesammelt wird.

#### Syntax
```javascript
const registry = new FinalizationRegistry((heldValue) => {
    // Cleanup-Logik hier
});
```

### Registrierung eines Objekts
Um ein Objekt zu registrieren, verwenden Sie die Methode `register(target, heldValue)`, wobei `target` das zu überwachende Objekt ist und `heldValue` ein Wert, der an den Callback übergeben wird, wenn das Zielobjekt gesammelt wird.

```javascript
registry.register(obj, "Information über das Objekt");
```

## Beispiele
### Beispiel 1: Grundlegende Verwendung
```javascript
const registry = new FinalizationRegistry((heldValue) => {
    console.log(`Aufräumarbeiten für: ${heldValue}`);
});

let obj = { name: "Beispiel" };
registry.register(obj, "Beispielobjekt");

// Löschen des Referenzobjekts
obj = null; // Das Objekt wird jetzt von der Garbage Collection gesammelt
```

### Beispiel 2: Aufräumarbeiten bei Objekten
```javascript
class Resource {
    constructor(name) {
        this.name = name;
        registry.register(this, `Ressource ${name} wird aufgeräumt`);
    }
}

let resource = new Resource("Datenbankverbindung");
resource = null; // Die Verbindung wird nun gesammelt
```

## Erklärung
### Häufige Fallstricke
- **Timing der Garbage Collection**: Es gibt keine Garantie, wann die Garbage Collection stattfindet. Der Callback könnte also verzögert oder möglicherweise nie aufgerufen werden, wenn die Anwendung nicht viel Speicher benötigt.
- **Weak References**: Der `FinalizationRegistry` ist nicht der beste Ansatz für alle Situationen. Wenn Sie eine starke Referenz auf ein Objekt benötigen, sollten Sie alternative Muster in Betracht ziehen.
- **Leistung**: Übermäßige oder ineffiziente Verwendung des `FinalizationRegistry` kann zu Performance-Problemen führen, da Callbacks bei der Garbage Collection ausgeführt werden.

## Zusammenfassung in einem Satz
Der `FinalizationRegistry` in JavaScript ist ein leistungsstarkes Werkzeug zur Verwaltung und Aufräumung von Ressourcen, die nach der Garbage Collection von Objekten benötigt werden.