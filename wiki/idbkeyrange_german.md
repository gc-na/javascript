<!--
Meta Description: # IDBKeyRange: Schlüsselbereich für IndexedDB in JavaScript ## Synopsis IDBKeyRange ist ein wichtiges API für die Arbeit mit IndexedDB in JavaScript, ...
Meta Keywords: idbkeyrange, der, von, die, javascript
-->

# IDBKeyRange: Schlüsselbereich für IndexedDB in JavaScript

## Synopsis
IDBKeyRange ist ein wichtiges API für die Arbeit mit IndexedDB in JavaScript, das Entwicklern ermöglicht, Schlüsselbereiche zu definieren und Abfragen innerhalb dieser Bereiche durchzuführen.

## Documentation
### Zweck
IDBKeyRange wird verwendet, um einen Bereich von Schlüsseln in einer IndexedDB-Datenbank zu definieren. Dies ist besonders nützlich, wenn man eine Abfrage durchführen möchte, die nur eine Teilmenge der Daten zurückgibt, die in der Datenbank gespeichert sind.

### Verwendung
IDBKeyRange kann auf verschiedene Weise instanziiert werden, um verschiedene Arten von Schlüsselbereichen zu definieren:

- **IDBKeyRange.only(key)**: Erzeugt einen Schlüsselbereich, der nur den angegebenen Schlüssel enthält.
- **IDBKeyRange.bound(lower, upper[, openLower[, openUpper]])**: Erzeugt einen Schlüsselbereich, der die angegebenen unteren und oberen Grenzen umfasst. Die optionalen Parameter `openLower` und `openUpper` bestimmen, ob die Grenzen offen oder geschlossen sind.
- **IDBKeyRange.lowerBound(lower[, openLower])**: Erzeugt einen Schlüsselbereich, der alle Werte ab einer bestimmten unteren Grenze enthält.
- **IDBKeyRange.upperBound(upper[, openUpper])**: Erzeugt einen Schlüsselbereich, der alle Werte bis zu einer bestimmten oberen Grenze enthält.

### Details
IDBKeyRange ist besonders nützlich bei der Verwendung von Cursor-Operationen oder beim Durchsuchen von Objektspeicher in IndexedDB. Der Schlüsselbereich ermöglicht es Entwicklern, gezielt nach Datensätzen zu suchen, die bestimmten Kriterien entsprechen, und somit die Effizienz von Datenbankoperationen zu erhöhen.

## Examples
Hier sind einige einfache Beispiele zur Verwendung von IDBKeyRange:

### Beispiel 1: Verwendung von `only`
```javascript
let keyRange = IDBKeyRange.only(5);
```

### Beispiel 2: Verwendung von `bound`
```javascript
let keyRange = IDBKeyRange.bound(1, 10);
```

### Beispiel 3: Verwendung von `lowerBound`
```javascript
let keyRange = IDBKeyRange.lowerBound(5);
```

### Beispiel 4: Verwendung von `upperBound`
```javascript
let keyRange = IDBKeyRange.upperBound(10);
```

## Explanation
Ein häufiges Problem beim Arbeiten mit IDBKeyRange ist das Missverständnis über die offenen und geschlossenen Grenzen. Wenn `openLower` oder `openUpper` auf true gesetzt werden, wird der entsprechende Wert nicht in den Bereich einbezogen. Dies kann zu unerwarteten Ergebnissen führen, wenn man denkt, dass der Wert Teil des Bereichs ist. 

Ein weiteres häufiges Problem besteht darin, dass Entwickler nicht erkennen, dass IDBKeyRange nur mit Schlüsselwerten funktioniert, die in der IndexedDB-Instanz definiert sind. Das bedeutet, dass der Schlüsseltyp konsistent sein muss, um fehlerhafte Abfragen zu vermeiden.

## One Line Summary
IDBKeyRange ist ein leistungsfähiges Werkzeug in JavaScript zur Definition von Schlüsselbereichen in IndexedDB, um gezielte Datenabfragen durchzuführen.