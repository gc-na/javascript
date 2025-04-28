<!--
Meta Description: # NamedNodeMap in JavaScript: Eine umfassende Übersicht ## Synopsis NamedNodeMap ist ein wichtiges Interface in JavaScript, das eine Sammlung von Attr...
Meta Keywords: namednodemap, die, attribute, element, eines
-->

# NamedNodeMap in JavaScript: Eine umfassende Übersicht

## Synopsis
NamedNodeMap ist ein wichtiges Interface in JavaScript, das eine Sammlung von Attributen eines XML- oder HTML-Elements repräsentiert. Es ermöglicht Entwicklern den Zugriff auf die Attribute eines Elements über ihren Namen.

## Dokumentation
### Zweck
NamedNodeMap ist ein Interface, das in der DOM (Document Object Model) API verwendet wird. Es wird hauptsächlich verwendet, um die Attribute eines Elements in einem XML- oder HTML-Dokument zu verwalten. Jede Instanz von NamedNodeMap enthält eine Liste von Attributen, die als NamedNode (benannte Knoten) bezeichnet werden.

### Verwendung
NamedNodeMap wird in der Regel durch den Zugriff auf die `attributes`-Eigenschaft eines Elements erhalten. Hier ist ein einfaches Beispiel:

```javascript
let element = document.getElementById("meinElement");
let attributeMap = element.attributes;
```

### Details
- **Indexzugriff**: Sie können auf Attribute entweder durch ihren Namen oder durch ihren Index zugreifen.
- **Länge**: Die Anzahl der Attribute kann über die `length`-Eigenschaft abgerufen werden.
- **Iteration**: NamedNodeMap ist iterable, was bedeutet, dass Sie die Attribute mit einer Schleife durchlaufen können.
- **Mutable**: Sie können neue Attribute hinzufügen, vorhandene ändern oder löschen.

## Beispiele
### Beispiel 1: Zugriff auf Attribute
```javascript
let element = document.getElementById("meinElement");
let attributeMap = element.attributes;

for (let i = 0; i < attributeMap.length; i++) {
    console.log(attributeMap[i].name + ": " + attributeMap[i].value);
}
```

### Beispiel 2: Hinzufügen eines neuen Attributs
```javascript
let element = document.getElementById("meinElement");
element.setAttribute("neuesAttribut", "wert");
console.log(element.attributes.length); // Ausgabe: Anzahl der Attribute + 1
```

### Beispiel 3: Löschen eines Attributs
```javascript
let element = document.getElementById("meinElement");
element.removeAttribute("zuEntfernen");
console.log(element.attributes.length); // Ausgabe: Anzahl der Attribute - 1
```

## Erklärung
Ein häufiger Stolperstein beim Arbeiten mit NamedNodeMap ist die Unterscheidung zwischen `getAttribute()` und dem direkten Zugriff auf die NamedNodeMap. Während `getAttribute()` den Wert eines Attributs zurückgibt, erlaubt der Zugriff auf NamedNodeMap eine direkte Manipulation der Attribute. 

Zudem ist es wichtig zu beachten, dass die `NamedNodeMap`-Instanz dynamisch ist. Das bedeutet, dass Änderungen an den Attributen eines Elements sofort in der NamedNodeMap reflektiert werden.

## One Line Summary
NamedNodeMap ist ein Interface in JavaScript, das den Zugriff und die Manipulation von Attributen eines DOM-Elements ermöglicht.