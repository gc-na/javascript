<!--
Meta Description: # btoa in JavaScript: Base64-Kodierung von Strings ## Synopsis Die `btoa`-Funktion in JavaScript wird verwendet, um einen String in das Base64-Format ...
Meta Keywords: btoa, ascii, javascript, originalstring, zeichen
-->

# btoa in JavaScript: Base64-Kodierung von Strings

## Synopsis
Die `btoa`-Funktion in JavaScript wird verwendet, um einen String in das Base64-Format zu kodieren, was besonders nützlich ist, um Binärdaten in einem ASCII-Format darzustellen.

## Dokumentation
Die `btoa`-Methode ist eine eingebaute Funktion in JavaScript, die einen String als Argument entgegennimmt und ihn in eine Base64-kodierte ASCII-Zeichenkette umwandelt. Diese Methode ist besonders hilfreich, wenn Sie Daten über das Internet übertragen oder in Form von URLs kodieren möchten.

### Verwendung
```javascript
let encodedString = btoa(originalString);
```
- **Parameter**: 
  - `originalString`: Ein String, der kodiert werden soll. Der String muss aus ASCII-Zeichen bestehen.

- **Rückgabewert**: 
  - Gibt eine Base64-kodierte Zeichenkette zurück.

### Details
- `btoa` kann nur mit ASCII-Zeichen arbeiten. Bei Verwendung von nicht-ASCII-Zeichen (z.B. Unicode-Zeichen) kann es zu Fehlern kommen.
- Die Funktion ist in modernen Browsern und Umgebungen wie Node.js verfügbar, jedoch in älteren Browsern möglicherweise nicht.

## Beispiele

### Beispiel 1: Einfache Kodierung
```javascript
let originalString = "Hallo Welt!";
let encodedString = btoa(originalString);
console.log(encodedString); // "SGFsbG8gV2VsdCE="
```

### Beispiel 2: Fehler bei nicht-ASCII-Zeichen
```javascript
try {
    let originalString = "Café";
    let encodedString = btoa(originalString);
} catch (e) {
    console.error(e); // Fehler: The string to be encoded contains characters outside of the Latin1 range.
}
```

## Erklärung
Ein häufiges Problem bei der Verwendung von `btoa` sind nicht-ASCII-Zeichen, die zu einem Fehler führen können, wenn sie versucht werden zu kodieren. Um diese Zeichen korrekt zu kodieren, sollten sie zuerst in einen ASCII-kompatiblen Format konvertiert werden, z.B. durch die Verwendung von `encodeURIComponent` und `unescape`.

Beispiel:
```javascript
let originalString = "Café";
let encodedString = btoa(unescape(encodeURIComponent(originalString)));
console.log(encodedString); // "Q8OpZQ=="
```

## Ein-Satz-Zusammenfassung
Die `btoa`-Funktion in JavaScript kodiert einen ASCII-String in eine Base64-Zeichenkette, ist jedoch empfindlich gegenüber nicht-ASCII-Zeichen.