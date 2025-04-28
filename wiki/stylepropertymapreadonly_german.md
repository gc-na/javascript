<!--
Meta Description: # StylePropertyMapReadOnly in JavaScript: Eine umfassende Anleitung ## Synopsis Die `StylePropertyMapReadOnly` Schnittstelle in JavaScript ermöglicht ...
Meta Keywords: die, css, element, stylepropertymapreadonly, stile
-->

# StylePropertyMapReadOnly in JavaScript: Eine umfassende Anleitung

## Synopsis
Die `StylePropertyMapReadOnly` Schnittstelle in JavaScript ermöglicht den Zugriff auf die CSS-Stile einer HTML-Element-Instanz, ohne die Möglichkeit, diese zu ändern. Sie ist besonders nützlich, um aktuelle Stile zu lesen und stilbezogene Abfragen durchzuführen.

## Dokumentation
Die `StylePropertyMapReadOnly` ist Teil der CSS Typed Object Model API und stellt eine Sammlung von CSS-Eigenschaften dar, die für ein bestimmtes Element gelten. Diese Schnittstelle bietet eine strukturierte Möglichkeit, auf CSS-Eigenschaften zuzugreifen, die auf ein Element angewendet wurden.

### Zweck
`StylePropertyMapReadOnly` wird verwendet, um CSS-Stile eines Elements in einem lesbaren Format zu erhalten. Dies ermöglicht Entwicklern, die aktuellen Stilwerte eines Elements zu überprüfen, ohne diese zu verändern.

### Verwendung
Die `StylePropertyMapReadOnly` Schnittstelle wird normalerweise in Verbindung mit der `Element.computedStyleMap()` Methode verwendet. Diese Methode gibt eine Instanz von `StylePropertyMapReadOnly` zurück, die alle aktuell angewendeten CSS-Eigenschaften des Elements enthält.

### Details
- **Zugriffsart**: Die `StylePropertyMapReadOnly` ist schreibgeschützt, was bedeutet, dass Sie die Werte nicht ändern können.
- **Methoden**: Zu den häufig verwendeten Methoden gehören `get()`, um den Wert einer bestimmten CSS-Eigenschaft abzurufen, sowie `forEach()`, um über alle Eigenschaften zu iterieren.

## Beispiele

### Beispiel 1: Zugriff auf CSS-Stile
```javascript
const element = document.querySelector('.mein-element');
const styles = window.getComputedStyle(element);

console.log(styles.getPropertyValue('color')); // Gibt die aktuelle Textfarbe des Elements zurück
```

### Beispiel 2: Verwendung von `computedStyleMap()`
```javascript
const element = document.querySelector('.mein-element');
const styleMap = element.computedStyleMap();

styleMap.forEach((style) => {
    console.log(`${style[0]}: ${style[1]}`); // Gibt jede CSS-Eigenschaft und ihren Wert aus
});
```

## Erklärung
Ein häufiger Stolperstein beim Arbeiten mit `StylePropertyMapReadOnly` ist das Missverständnis über den Unterschied zwischen `getComputedStyle()` und `computedStyleMap()`. Während `getComputedStyle()` ein CSSStyleDeclaration-Objekt zurückgibt, bietet `computedStyleMap()` eine detailliertere und strukturiertere Sicht auf die Stile. 

Außerdem sollte man beachten, dass `StylePropertyMapReadOnly` nur für die Abfrage von Stilen gedacht ist. Um Stile zu ändern, sollte man die CSS-Eigenschaften direkt über `element.style` oder durch Klassenzuweisungen anpassen.

## Einzeilige Zusammenfassung
Die `StylePropertyMapReadOnly` Schnittstelle ermöglicht es Entwicklern, die aktuellen CSS-Stile eines Elements in JavaScript zu lesen, ohne diese zu ändern.