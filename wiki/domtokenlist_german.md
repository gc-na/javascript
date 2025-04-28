<!--
Meta Description: # DOMTokenList in JavaScript: Eine umfassende Anleitung ## Synopsis DOMTokenList ist ein wichtiges JavaScript-Objekt, das eine Sammlung von Zeichenfol...
Meta Keywords: token, element, classlist, ein, die
-->

# DOMTokenList in JavaScript: Eine umfassende Anleitung

## Synopsis
DOMTokenList ist ein wichtiges JavaScript-Objekt, das eine Sammlung von Zeichenfolgen darstellt, die als Token (z. B. Klassen- oder Attributnamen) in HTML-Elementen verwendet werden. Es ermöglicht das einfache Hinzufügen, Entfernen und Überprüfen von Klassen und Attributen in DOM-Elementen.

## Dokumentation
### Zweck
DOMTokenList wird hauptsächlich verwendet, um mit der `classList`-Eigenschaft von HTML-Elementen zu interagieren. Es bietet Methoden zum Manipulieren von Klassen, ohne direkt mit Strings arbeiten zu müssen.

### Verwendung
Ein DOMTokenList-Objekt wird automatisch erstellt, wenn Sie auf die `classList`-Eigenschaft eines DOM-Elements zugreifen. Es bietet die folgenden Hauptmethoden:

- **add(token)**: Fügt einen oder mehrere Token zur Liste hinzu.
- **remove(token)**: Entfernt einen oder mehrere Token aus der Liste.
- **toggle(token)**: Schaltet einen Token ein oder aus, je nachdem, ob er bereits vorhanden ist oder nicht.
- **contains(token)**: Überprüft, ob ein bestimmter Token in der Liste vorhanden ist.
- **item(index)**: Gibt den Token an der angegebenen Position zurück.
- **length**: Gibt die Anzahl der Token in der Liste zurück.

### Beispiel
Hier sind einige grundlegende Beispiele zur Verwendung von DOMTokenList:

```javascript
// Zugriff auf ein DOM-Element
const element = document.getElementById('meinElement');

// Hinzufügen einer Klasse
element.classList.add('aktiv');

// Entfernen einer Klasse
element.classList.remove('inaktiv');

// Überprüfen, ob eine Klasse vorhanden ist
if (element.classList.contains('aktiv')) {
    console.log('Das Element ist aktiv.');
}

// Umschalten einer Klasse
element.classList.toggle('sichtbar');

// Zugriff auf einen Token
console.log(element.classList.item(0)); // Gibt die erste Klasse zurück
```

## Erklärung
Ein häufiger Stolperstein bei der Verwendung von DOMTokenList ist das Missverständnis über die Methoden `add`, `remove` und `toggle`, insbesondere wenn mehrere Token hinzugefügt oder entfernt werden. Um mehrere Klassen in einem einzigen Aufruf hinzuzufügen oder zu entfernen, müssen Sie die Token durch Kommas trennen:

```javascript
element.classList.add('klasse1', 'klasse2'); // Fügt klasse1 und klasse2 hinzu
element.classList.remove('klasse1', 'klasse2'); // Entfernt klasse1 und klasse2
```

Ein weiteres wichtiges Detail ist, dass die `toggle`-Methode einen zweiten Parameter akzeptiert, der angibt, ob die Klasse hinzugefügt oder entfernt werden soll:

```javascript
element.classList.toggle('sichtbar', false); // Entfernt 'sichtbar' falls vorhanden
```

## Ein-Satz-Zusammenfassung
DOMTokenList ist ein nützliches JavaScript-Objekt zur einfachen Verwaltung von Klassen und Attributen in HTML-DOM-Elementen.