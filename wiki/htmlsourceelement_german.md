<!--
Meta Description: # HTMLSourceElement in JavaScript: Verwendung, Beispiele und häufige Fallen ## Synopsis Das `HTMLSourceElement` ist ein JavaScript-Objekt, das mit dem...
Meta Keywords: das, die, video, htmlsourceelement, ist
-->

# HTMLSourceElement in JavaScript: Verwendung, Beispiele und häufige Fallen

## Synopsis
Das `HTMLSourceElement` ist ein JavaScript-Objekt, das mit dem `<source>`-Tag in HTML verbunden ist. Es wird verwendet, um verschiedene Medienquellen für Audio- und Video-Elemente bereitzustellen, um die Kompatibilität in verschiedenen Browsern zu gewährleisten.

## Documentation
### Zweck
Das `HTMLSourceElement` ermöglicht es Webentwicklern, mehrere Quellen für Medieninhalte anzugeben. Dies verbessert die Benutzererfahrung, indem sichergestellt wird, dass das Medium in verschiedenen Browsern abgespielt werden kann. Es wird typischerweise in Verbindung mit `<audio>` und `<video>`-Elementen verwendet.

### Verwendung
Das `HTMLSourceElement` wird in HTML durch das `<source>`-Tag erstellt. In JavaScript kann auf das Element über das DOM (Document Object Model) zugegriffen werden. Hier sind einige wichtige Attribute des `HTMLSourceElement`:

- `src`: Gibt die URL der Medienquelle an.
- `type`: Definiert den MIME-Typ der Quelle, um dem Browser zu helfen, die Kompatibilität zu überprüfen.

### Details
Das `HTMLSourceElement` ist nicht direkt instanziierbar, sondern wird typischerweise durch das Parsen von HTML-Dokumenten erstellt. Entwickler können jedoch auf die Eigenschaften und Methoden des Elements über JavaScript zugreifen, um dynamisch die Quellen zu ändern oder zusätzliche Quellen hinzuzufügen.

## Examples
### Grundlegende Verwendung
Hier ist ein einfaches Beispiel, das zeigt, wie das `HTMLSourceElement` in HTML und JavaScript verwendet wird:

```html
<video controls>
  <source src="video.mp4" type="video/mp4">
  <source src="video.webm" type="video/webm">
  Ihr Browser unterstützt das Video-Tag nicht.
</video>

<script>
  const videoElement = document.querySelector('video');
  const sourceElement = document.createElement('source');
  sourceElement.src = 'video.ogg';
  sourceElement.type = 'video/ogg';

  videoElement.appendChild(sourceElement);
  videoElement.load(); // Lädt die neuen Quellen
</script>
```

## Explanation
### Häufige Fallen
1. **Falscher MIME-Typ**: Stellen Sie sicher, dass der angegebene `type` korrekt ist. Ein falscher MIME-Typ kann dazu führen, dass das Medium nicht abgespielt wird, auch wenn die Quelle korrekt ist.
  
2. **Browserkompatibilität**: Nicht alle Browser unterstützen alle Formate. Es ist ratsam, mehrere Quellen in verschiedenen Formaten anzugeben, um sicherzustellen, dass das Medium in allen gängigen Browsern funktioniert.

3. **Reihenfolge der Quellen**: Die Reihenfolge der `<source>`-Elemente kann die Wiedergabe beeinflussen. Der Browser versucht, die erste funktionierende Quelle abzuspielen.

### Zusätzliche Hinweise
- Das `HTMLSourceElement` ist Teil der HTML Living Standard-Spezifikation und wird von den meisten modernen Browsern unterstützt.
- Verwenden Sie das `load()`-Methode des `<video>` oder `<audio>`-Elements, um die Medienquelle nach dem Hinzufügen eines neuen `<source>`-Tags neu zu laden.

## One Line Summary
Das `HTMLSourceElement` ermöglicht die Angabe mehrerer Medienquellen in HTML, um die Kompatibilität und Benutzererfahrung in JavaScript-basierten Anwendungen zu verbessern.