<!--
Meta Description: # structuredClone in JavaScript: Eine umfassende Anleitung ## Synopsis `structuredClone` ist eine moderne JavaScript-Funktion zum Erstellen einer tief...
Meta Keywords: structuredclone, kopie, die, javascript, original
-->

# structuredClone in JavaScript: Eine umfassende Anleitung

## Synopsis
`structuredClone` ist eine moderne JavaScript-Funktion zum Erstellen einer tiefen Kopie von Objekten. Sie ermöglicht es Entwicklern, komplexe Datenstrukturen effizient zu kopieren, ohne die typischen Einschränkungen von `JSON.stringify` und `JSON.parse`.

## Dokumentation
### Zweck
Die Funktion `structuredClone` wird verwendet, um eine tiefere Kopie von JavaScript-Objekten zu erstellen. Im Gegensatz zu flachen Kopien, die Referenzen auf die Originalobjekte beibehalten, erstellt `structuredClone` vollständige Kopien aller Werte, einschließlich verschachtelter Objekte, Arrays und sogar Date-Objekte.

### Verwendung
Die Syntax für `structuredClone` ist einfach:

```javascript
let kopie = structuredClone(original);
```

- `original`: Das zu klonende Objekt oder Array.
- `kopie`: Das neu erstellte, tiefe Kopie des ursprünglichen Objekts.

### Details
- Unterstützt die meisten Datentypen wie Objekte, Arrays, Maps, Sets, Date, RegExp und Blob.
- Kann nicht verwendet werden für Funktionen, DOM-Knoten, oder Objekte mit zyklischen Referenzen, da sie zu einem Fehler führen würden.
- Rückgabewert: Ein neues, unabhängiges Objekt, das eine Kopie des Originalobjekts darstellt.

## Beispiele
### Beispiel 1: Einfaches Objekt klonen
```javascript
const original = { name: "Max", alter: 30 };
const kopie = structuredClone(original);

console.log(kopie); // { name: "Max", alter: 30 }
kopie.name = "Julia";
console.log(original.name); // "Max" bleibt unverändert
```

### Beispiel 2: Verschachtelte Objekte klonen
```javascript
const original = { name: "Anna", adresse: { stadt: "Berlin", plz: 10115 } };
const kopie = structuredClone(original);

console.log(kopie.adresse.stadt); // "Berlin"
kopie.adresse.stadt = "München";
console.log(original.adresse.stadt); // "Berlin" bleibt unverändert
```

### Beispiel 3: Klonen von Arrays
```javascript
const originalArray = [1, 2, { a: 3 }];
const kopieArray = structuredClone(originalArray);

console.log(kopieArray[2].a); // 3
kopieArray[2].a = 4;
console.log(originalArray[2].a); // 3 bleibt unverändert
```

## Erklärung
### Häufige Fallstricke
- **Funktionen und DOM-Knoten**: `structuredClone` kann keine Funktionen oder DOM-Knoten klonen. Versuche, diese zu klonen, führen zu einem TypeError.
- **Zyklische Referenzen**: Wenn das Originalobjekt zyklische Referenzen enthält, wird ein Fehler ausgelöst. Es ist wichtig, sicherzustellen, dass die zu klonenden Objekte keine solchen Referenzen haben.
- **Browser-Unterstützung**: Nicht alle Browser unterstützen `structuredClone` vollständig. Zum Zeitpunkt der Erstellung dieses Dokuments ist die Unterstützung in modernen Browsern jedoch weit verbreitet.

## Ein-Satz-Zusammenfassung
`structuredClone` ist eine leistungsstarke JavaScript-Funktion zum Erstellen tiefer Kopien von Objekten und Arrays, die komplexe Datenstrukturen effizient handhabt.