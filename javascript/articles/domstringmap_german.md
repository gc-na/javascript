<!--
Meta Description: # DOMStringMap in JavaScript: Ein Leitfaden für Entwickler ## Synopsis DOMStringMap ist ein JavaScript-Objekt, das den Zugriff auf benutzerdefinierte ...
Meta Keywords: data, die, sie, dataset, domstringmap
-->

# DOMStringMap in JavaScript: Ein Leitfaden für Entwickler

## Synopsis
DOMStringMap ist ein JavaScript-Objekt, das den Zugriff auf benutzerdefinierte Datenattribute (data-Attribute) eines HTML-Elements ermöglicht. Es bietet eine einfache Möglichkeit, Daten in HTML zu speichern und auf sie zuzugreifen, ohne die Verwendung von JavaScript-Variablen.

## Documentation
### Zweck
DOMStringMap wird hauptsächlich verwendet, um benutzerdefinierte Datenattribute, die mit dem Präfix `data-` in HTML-Elementen definiert sind, zu verwalten. Diese Attribute sind nützlich, um zusätzliche Informationen in HTML zu speichern, die nicht für den Benutzer sichtbar sind, aber für JavaScript-Operationen benötigt werden.

### Verwendung
Um auf die DOMStringMap eines Elements zuzugreifen, verwenden Sie die `dataset`-Eigenschaft des Elements. Jedes Attribut, das mit `data-` beginnt, wird als Schlüssel in einem DOMStringMap-Objekt dargestellt, wobei das `data-`-Präfix entfernt und der Rest des Attributs in camelCase umgewandelt wird.

#### Beispiel:
```html
<div id="example" data-user-name="Max" data-user-age="30"></div>
```

In JavaScript:
```javascript
const element = document.getElementById('example');
console.log(element.dataset.userName); // Ausgabe: Max
console.log(element.dataset.userAge); // Ausgabe: 30
```

### Details
- **Zugriff**: Die `dataset`-Eigenschaft gibt ein DOMStringMap-Objekt zurück, das alle `data-`-Attribute des Elements enthält.
- **Schreibzugriff**: Sie können neue `data-`-Attribute hinzufügen oder bestehende ändern, indem Sie einfach die Eigenschaften des `dataset`-Objekts anpassen.
- **Konvertierung**: Attributnamen, die Bindestriche enthalten, werden in camelCase umgewandelt (z. B. `data-user-name` wird zu `userName`).

## Examples
### Beispiel 1: Datenattribute lesen
```html
<div id="user" data-role="admin" data-status="active"></div>

<script>
const userDiv = document.getElementById('user');
console.log(userDiv.dataset.role); // Ausgabe: admin
console.log(userDiv.dataset.status); // Ausgabe: active
</script>
```

### Beispiel 2: Datenattribute setzen
```html
<div id="product" data-price="100" data-discount="20"></div>

<script>
const productDiv = document.getElementById('product');
productDiv.dataset.price = "120"; // Preis aktualisieren
console.log(productDiv.dataset.price); // Ausgabe: 120
</script>
```

## Explanation
### Häufige Stolpersteine
- **Schreibweise von Attributen**: Achten Sie darauf, dass Sie die richtigen camelCase-Namen verwenden, wenn Sie auf die `dataset`-Eigenschaften zugreifen. Ein falscher Name führt zu `undefined`.
- **Datenkonvertierung**: Alle Werte werden als Strings behandelt. Wenn Sie mit Zahlen arbeiten möchten, müssen Sie diese manuell konvertieren.
- **Kompatibilität**: DOMStringMap ist in modernen Browsern weit verbreitet, jedoch sollten Sie die Unterstützung in älteren Browsern überprüfen, falls Sie diese ansprechen möchten.

## One Line Summary
DOMStringMap ist eine JavaScript-Schnittstelle, die den Zugriff auf benutzerdefinierte Datenattribute von HTML-Elementen ermöglicht.