<!--
Meta Description: # WeakMap in JavaScript: Ein umfassender Leitfaden ## Synopsis WeakMap ist eine spezielle Art von Map in JavaScript, die es ermöglicht, Schlüssel-Obje...
Meta Keywords: weakmap, schlüssel, die, ist, der
-->

# WeakMap in JavaScript: Ein umfassender Leitfaden

## Synopsis
WeakMap ist eine spezielle Art von Map in JavaScript, die es ermöglicht, Schlüssel-Objekte und deren zugehörige Werte zu speichern, ohne dass diese eine starke Referenz auf die Schlüssel behalten. Dadurch wird die Garbage Collection erleichtert und Speicherlecks vermieden.

## Dokumentation

### Zweck
WeakMap ist eine Sammlung von Schlüssel-Wert-Paaren, bei der die Schlüssel schwache Referenzen sind. Dies bedeutet, dass, wenn es keine anderen Referenzen auf einen Schlüssel gibt, dieser vom Garbage Collector entfernt werden kann, selbst wenn er in einer WeakMap gespeichert ist. Dies ist besonders nützlich, wenn Sie Objekte als Schlüssel verwenden und sicherstellen möchten, dass sie automatisch entfernt werden, wenn sie nicht mehr benötigt werden.

### Verwendung
WeakMap wird wie folgt erstellt:

```javascript
const weakMap = new WeakMap();
```

#### Methoden
- **set(key, value)**: Fügt ein Schlüssel-Wert-Paar zur WeakMap hinzu.
- **get(key)**: Gibt den Wert zurück, der dem Schlüssel zugeordnet ist, oder `undefined`, wenn der Schlüssel nicht existiert.
- **has(key)**: Prüft, ob ein Schlüssel in der WeakMap vorhanden ist.
- **delete(key)**: Entfernt das Schlüssel-Wert-Paar aus der WeakMap.

### Details
- **Schlüsselspeicher**: Die Schlüssel in einer WeakMap müssen Objekte sein. Primitive Datentypen wie Zahlen, Strings oder Booleans können nicht als Schlüssel verwendet werden.
- **Garbage Collection**: Wenn der Schlüssel aus der WeakMap entfernt wird (z.B. durch das Löschen der Referenz auf das Objekt), wird der Speicherplatz, den er belegt hat, sofort freigegeben, falls keine anderen Referenzen mehr bestehen.
- **Iterierbarkeit**: WeakMap ist nicht iterierbar. Es gibt keine Methoden wie `forEach`, die auf WeakMap angewendet werden können, da die Schlüssel schwach sind und nicht dauerhaft sind.

## Beispiele

### Beispiel 1: Grundlegende Verwendung von WeakMap

```javascript
let obj = {};
let weakMap = new WeakMap();

weakMap.set(obj, "Wert für das Objekt");

console.log(weakMap.get(obj)); // Ausgabe: "Wert für das Objekt"
```

### Beispiel 2: Verwendung von WeakMap zur Vermeidung von Speicherlecks

```javascript
class Beispiel {
    constructor() {
        this.privat = new WeakMap();
    }
    
    setWert(obj, wert) {
        this.privat.set(obj, wert);
    }
    
    getWert(obj) {
        return this.privat.get(obj);
    }
}

let beispiel = new Beispiel();
let obj1 = {};
beispiel.setWert(obj1, "Geheime Information");

console.log(beispiel.getWert(obj1)); // Ausgabe: "Geheime Information"
```

## Erklärung
Ein häufiger Fehler beim Arbeiten mit WeakMap ist die Annahme, dass sie wie normale Maps funktionieren. Da die Schlüssel schwache Referenzen sind, können sie jederzeit vom Garbage Collector entfernt werden, was zu unerwartetem Verhalten führen kann, wenn versucht wird, auf einen nicht mehr vorhandenen Schlüssel zuzugreifen. Außerdem sollten Sie sicherstellen, dass alle Schlüssel, die Sie in einer WeakMap speichern, Objekte sind, da primitive Datentypen nicht erlaubt sind.

## Einzeiler Zusammenfassung
WeakMap ist eine Map-ähnliche Datenstruktur in JavaScript, die schwache Referenzen auf Schlüssel verwendet, um Speicherlecks zu verhindern und die Garbage Collection zu unterstützen.