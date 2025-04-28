<!--
Meta Description: # onauxclick in JavaScript: Ein umfassender Leitfaden ## Synopsis `onauxclick` ist ein JavaScript-Event, das ausgelöst wird, wenn eine Maustaste, die ...
Meta Keywords: event, maustaste, die, onauxclick, das
-->

# onauxclick in JavaScript: Ein umfassender Leitfaden

## Synopsis
`onauxclick` ist ein JavaScript-Event, das ausgelöst wird, wenn eine Maustaste, die nicht die linke Maustaste ist (in der Regel die mittlere oder rechte Maustaste), in einem bestimmten Element geklickt wird. Dieses Event ist nützlich, um spezifische Aktionen für alternative Mausklicks zu implementieren.

## Dokumentation
### Zweck
Das `onauxclick`-Event ermöglicht Entwicklern, auf Mausklicks zu reagieren, die nicht mit der linken Maustaste ausgeführt werden. Es ist besonders hilfreich in Anwendungen, bei denen unterschiedliche Benutzerinteraktionen unterschiedliche Ergebnisse hervorrufen sollen.

### Verwendung
Das `onauxclick`-Event wird direkt in HTML-Elementen als Attribut oder in JavaScript über den `addEventListener`-Methodenaufruf definiert. Es ist wichtig zu beachten, dass das Event nur in Browsern unterstützt wird, die es implementiert haben. 

#### Syntax
```javascript
element.onauxclick = function(event) {
    // Ihre Logik hier
};
```

Alternativ:
```javascript
element.addEventListener('auxclick', function(event) {
    // Ihre Logik hier
});
```

### Details
- **Event-Objekt**: Das Event-Objekt, das an die Event-Handler-Funktion übergeben wird, enthält Informationen über den Klick, einschließlich der verwendeten Maustaste.
- **Tastenwerte**: 
  - `0` für die linke Maustaste
  - `1` für die mittlere Maustaste
  - `2` für die rechte Maustaste

Es ist wichtig, die Taste zu prüfen, die den Klick ausgelöst hat, um sicherzustellen, dass die gewünschte Aktion nur für die entsprechenden Tasten ausgeführt wird.

## Beispiele
### Beispiel 1: Einfache Verwendung
```html
<button id="myButton">Klicke mich</button>

<script>
document.getElementById('myButton').onauxclick = function(event) {
    if (event.button === 1) {
        alert('Mittlere Maustaste wurde gedrückt!');
    } else if (event.button === 2) {
        alert('Rechte Maustaste wurde gedrückt!');
    }
};
</script>
```

### Beispiel 2: Verwendung mit addEventListener
```html
<div id="myDiv">Klicke hier mit einer anderen Maustaste!</div>

<script>
document.getElementById('myDiv').addEventListener('auxclick', function(event) {
    switch (event.button) {
        case 1:
            console.log('Mittlere Maustaste');
            break;
        case 2:
            console.log('Rechte Maustaste');
            break;
    }
});
</script>
```

## Erklärung
- **Häufige Fallstricke**: Ein häufiger Fehler besteht darin, nicht zu überprüfen, welche Maustaste gedrückt wurde. Wenn das Event nicht korrekt verarbeitet wird, können unerwünschte Aktionen ausgelöst werden.
- **Browserkompatibilität**: Obwohl die meisten modernen Browser `onauxclick` unterstützen, sollten Entwickler die Unterstützung auf den Zielbrowsern überprüfen, um Probleme zu vermeiden.
- **Verwendung mit anderen Events**: `onauxclick` kann zusammen mit anderen Mausklick-Events wie `onclick` oder `contextmenu` verwendet werden, um eine umfassende Benutzerinteraktion zu ermöglichen. 

## Ein-Satz-Zusammenfassung
`onauxclick` ist ein JavaScript-Event, das es Entwicklern ermöglicht, auf Klicks mit der mittleren oder rechten Maustaste zu reagieren.