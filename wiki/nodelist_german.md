<!--
Meta Description: # NodeList in JavaScript: Eine umfassende Anleitung ## Synopsis NodeList ist eine Sammlung von Knoten (Nodes) in einem Dokument, die von Methoden wie ...
Meta Keywords: die, nodelist, eine, von, document
-->

# NodeList in JavaScript: Eine umfassende Anleitung

## Synopsis
NodeList ist eine Sammlung von Knoten (Nodes) in einem Dokument, die von Methoden wie `document.querySelectorAll()` zurückgegeben wird. Es ermöglicht Entwicklern den Zugriff auf eine Gruppe von DOM-Elementen, die bestimmten Selektoren entsprechen.

## Dokumentation
### Zweck
NodeList ist ein wichtiges Konzept in der Webentwicklung mit JavaScript, da es es ermöglicht, mehrere DOM-Elemente gleichzeitig zu manipulieren. NodeLists sind oft das Resultat von DOM-Abfragen und bieten eine einfache Möglichkeit, auf alle übereinstimmenden Elemente zuzugreifen.

### Verwendung
NodeLists können auf verschiedene Weisen erstellt werden, typischerweise über die folgenden Methoden:

- `document.querySelectorAll(selector)`: Gibt eine NodeList aller Elemente zurück, die dem angegebenen CSS-Selektor entsprechen.
- `childNodes`: Eine Eigenschaft eines Knotens, die eine NodeList aller Kindknoten zurückgibt.

NodeLists sind **nicht** Arrays, obwohl sie einige ähnliche Eigenschaften aufweisen. Zum Beispiel können sie mit der `length`-Eigenschaft die Anzahl der enthaltenen Knoten zurückgeben. Es ist jedoch wichtig zu beachten, dass NodeLists keine Array-Methoden wie `map`, `forEach` oder `filter` nativ unterstützen.

### Details
NodeLists sind "live" oder "statisch", abhängig von ihrer Quelle. Zum Beispiel gibt `document.getElementsByTagName()` eine "live" NodeList zurück, die sich automatisch aktualisiert, wenn sich das DOM ändert. Im Gegensatz dazu gibt `document.querySelectorAll()` eine statische NodeList zurück, die einmalig erstellt wird und sich nicht mehr ändert, selbst wenn das DOM später verändert wird.

## Beispiele
### Beispiel 1: Verwendung von `document.querySelectorAll()`
```javascript
// Alle <p>-Elemente im Dokument abrufen
const paragraphs = document.querySelectorAll('p');
console.log(paragraphs.length); // Gibt die Anzahl der <p>-Elemente zurück
```

### Beispiel 2: Iteration über eine NodeList
```javascript
const listItems = document.querySelectorAll('li');

// Iteration über die NodeList mit forEach
listItems.forEach(item => {
    console.log(item.textContent); // Gibt den Textinhalt jedes <li>-Elements aus
});
```

### Beispiel 3: Zugriff auf Kindknoten
```javascript
const parentElement = document.getElementById('parent');
const children = parentElement.childNodes;

console.log(children.length); // Gibt die Anzahl der Kindknoten zurück
```

## Erklärung
Ein häufiger Fehler bei der Arbeit mit NodeLists ist die Annahme, dass sie Arrays sind. Dies kann zu unerwarteten Resultaten führen, insbesondere wenn Entwickler versuchen, Array-Methoden direkt darauf anzuwenden. Um eine NodeList in ein Array umzuwandeln, kann die `Array.from()` Methode oder der Spread-Operator (`...`) verwendet werden:

```javascript
const itemsArray = Array.from(listItems); // NodeList in ein Array umwandeln
// oder
const itemsArray = [...listItems]; // NodeList in ein Array umwandeln
```

Ein weiterer Punkt ist, dass live NodeLists (wie die von `getElementsByTagName`) dynamisch sind. Änderungen am DOM (z.B. das Hinzufügen oder Entfernen von Knoten) können dazu führen, dass sich die NodeList unerwartet ändert, was zu Verwirrung führen kann.

## Ein Satz Zusammenfassung
NodeList ist eine Sammlung von DOM-Knoten, die über Methoden wie `document.querySelectorAll()` abgerufen wird und es Entwicklern ermöglicht, mehrere Elemente gleichzeitig zu bearbeiten.