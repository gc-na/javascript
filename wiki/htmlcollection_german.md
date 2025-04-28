<!--
Meta Description: # HTMLCollection in JavaScript: Eine umfassende Anleitung ## Synopsis HTMLCollection ist eine Sammlung von DOM-Elementen, die in JavaScript verwendet ...
Meta Keywords: htmlcollection, die, eine, der, ist
-->

# HTMLCollection in JavaScript: Eine umfassende Anleitung

## Synopsis
HTMLCollection ist eine Sammlung von DOM-Elementen, die in JavaScript verwendet wird, um auf Gruppen von HTML-Elementen zuzugreifen und diese zu manipulieren.

## Dokumentation
HTMLCollection ist ein Live-Sammlungsobjekt, das alle Elemente eines bestimmten Typs innerhalb eines Dokuments repräsentiert. Diese Sammlung wird dynamisch aktualisiert, wenn sich die Struktur des Dokuments ändert, was bedeutet, dass Änderungen an den DOM-Elementen in Echtzeit reflektiert werden. HTMLCollection wird häufig in Kombination mit Methoden wie `getElementsByTagName`, `getElementsByClassName` und `children` verwendet.

### Zweck
Der Hauptzweck von HTMLCollection besteht darin, Entwicklern eine einfache Möglichkeit zu bieten, Gruppen von Elementen im DOM zu selektieren und zu bearbeiten.

### Verwendung
HTMLCollection kann durch verschiedene Methoden erstellt werden:
- `document.getElementsByTagName(tagName)`: Gibt eine HTMLCollection aller Elemente mit dem angegebenen Tag zurück.
- `document.getElementsByClassName(className)`: Gibt eine HTMLCollection aller Elemente mit der angegebenen Klasse zurück.
- `element.children`: Gibt eine HTMLCollection aller direkten Kinder eines bestimmten Elements zurück.

### Details
- HTMLCollection ist indiziert, was bedeutet, dass Sie auf die Elemente über ihren Index zugreifen können, ähnlich wie bei einem Array.
- Es enthält keine Array-Methoden wie `forEach`, `map` oder `filter`, obwohl es Array-ähnlich ist.
- Um HTMLCollection in ein echtes Array zu konvertieren, kann die `Array.from()`-Methode oder der Spread-Operator verwendet werden.

## Beispiele
### Beispiel 1: Elemente nach Tagname abrufen
```javascript
let divs = document.getElementsByTagName("div");
console.log(divs.length); // Gibt die Anzahl der <div>-Elemente im Dokument aus
```

### Beispiel 2: Elemente nach Klassenname abrufen
```javascript
let items = document.getElementsByClassName("item");
console.log(items[0].innerHTML); // Gibt den Inhalt des ersten Elements mit der Klasse "item" aus
```

### Beispiel 3: Kinder eines Elements abrufen
```javascript
let parent = document.getElementById("parent");
let children = parent.children;
console.log(children.length); // Gibt die Anzahl der direkten Kinder des Elements mit der ID "parent" aus
```

## Erklärung
Ein häufiger Stolperstein bei der Arbeit mit HTMLCollection ist, dass es sich um eine Live-Sammlung handelt. Änderungen an den DOM-Elementen können dazu führen, dass die Sammlung automatisch aktualisiert wird. Dies kann zu unerwarteten Ergebnissen führen, wenn Sie versuchen, die Sammlung während einer Iteration zu ändern. Ein weiteres wichtiges Detail ist, dass HTMLCollection keine Array-Methoden hat. Wenn Sie diese benötigen, sollten Sie die Sammlung in ein Array umwandeln.

## Zusammenfassung in einem Satz
HTMLCollection ist eine dynamische Sammlung von DOM-Elementen in JavaScript, die Entwicklern die Manipulation und den Zugriff auf Gruppen von HTML-Elementen erleichtert.