<!--
Meta Description: # Länge in JavaScript: Eine umfassende Anleitung ## Synopsis In JavaScript ist die `length`-Eigenschaft ein wichtiges Werkzeug zur Bestimmung der Anza...
Meta Keywords: length, die, eigenschaft, der, arrays
-->

# Länge in JavaScript: Eine umfassende Anleitung

## Synopsis
In JavaScript ist die `length`-Eigenschaft ein wichtiges Werkzeug zur Bestimmung der Anzahl der Elemente in Arrays und der Anzahl der Zeichen in Strings. Sie ermöglicht Entwicklern, dynamisch mit Datenstrukturen zu arbeiten und ihre Längen zu analysieren.

## Dokumentation
Die `length`-Eigenschaft ist ein integriertes Attribut für Arrays und Strings in JavaScript. 

### Zweck
- Bei Arrays gibt `length` die Anzahl der Elemente an, die im Array enthalten sind.
- Bei Strings gibt `length` die Anzahl der Zeichen in einem String zurück.

### Verwendung
- **Arrays**: `array.length`
- **Strings**: `string.length`

### Details
- Die `length`-Eigenschaft ist eine numerische Eigenschaft und kann sowohl gelesen als auch gesetzt werden. 
- Bei Arrays wird die `length`-Eigenschaft automatisch aktualisiert, wenn Elemente hinzugefügt oder entfernt werden.
- Bei Strings ist die `length`-Eigenschaft schreibgeschützt – sie kann nicht verändert werden.

## Beispiele
### Beispiel 1: Verwendung von `length` mit Arrays
```javascript
let fruechte = ['Äpfel', 'Bananen', 'Kirschen'];
console.log(fruechte.length); // Ausgabe: 3
```

### Beispiel 2: Verwendung von `length` mit Strings
```javascript
let nachricht = "Hallo, Welt!";
console.log(nachricht.length); // Ausgabe: 12
```

### Beispiel 3: Dynamische Anpassung der Array-Länge
```javascript
let zahlen = [1, 2, 3];
zahlen.length = 2;
console.log(zahlen); // Ausgabe: [1, 2]
```

## Erklärung
Obwohl die `length`-Eigenschaft in der Regel einfach zu verwenden ist, gibt es einige häufige Fallstricke:

- **Arrays mit Lücken**: Bei Arrays, die Lücken enthalten (d.h. nicht definierte Indizes), zählt die `length`-Eigenschaft nur die definierten Elemente. 
```javascript
let lueckenArray = [1, , 3];
console.log(lueckenArray.length); // Ausgabe: 3
```

- **Strings sind unveränderlich**: Während die `length`-Eigenschaft bei Arrays dynamisch ist, ist sie bei Strings schreibgeschützt. Ein Versuch, die Länge eines Strings zu setzen, wird ignoriert.
```javascript
let text = "Beispiel";
text.length = 10; // Keine Auswirkung
console.log(text.length); // Ausgabe: 7
```

## Ein-Satz-Zusammenfassung
Die `length`-Eigenschaft in JavaScript liefert die Anzahl der Elemente in Arrays und die Anzahl der Zeichen in Strings und ist ein grundlegendes Werkzeug für die Datenmanipulation.