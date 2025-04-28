<!--
Meta Description: # HTMLMapElement in JavaScript: Eine umfassende Anleitung ## Synopsis Das `HTMLMapElement` ist ein DOM-Element, das in HTML verwendet wird, um ein Bil...
Meta Keywords: die, html, ein, das, map
-->

# HTMLMapElement in JavaScript: Eine umfassende Anleitung

## Synopsis
Das `HTMLMapElement` ist ein DOM-Element, das in HTML verwendet wird, um ein Bild in verschiedene klickbare Bereiche unterteilen zu können. In JavaScript ermöglicht es Entwicklern, interaktive Bildkarten zu erstellen, die durch das `map`-Tag definiert werden.

## Dokumentation
Das `HTMLMapElement` ist ein Teil der HTML-DOM-Schnittstelle und repräsentiert das `<map>`-Tag, das in HTML verwendet wird. Dieses Element wird verwendet, um die Bereiche eines Bildes zu definieren, die auf Benutzerinteraktionen reagieren. Jedes Bereichselement (`<area>`) innerhalb einer Karte ist mit einer bestimmten URL verknüpft, die beim Klicken auf den jeweiligen Bereich aufgerufen wird.

### Zweck
Der Hauptzweck des `HTMLMapElement` besteht darin, interaktive Bildkarten zu erstellen, die Benutzer auf verschiedene Inhalte oder Seiten weiterleiten können, je nachdem, auf welchen Bereich des Bildes sie klicken.

### Verwendung
Um ein `HTMLMapElement` zu verwenden, müssen Sie zunächst ein `<map>`-Tag in Ihrem HTML-Dokument erstellen und es mit einem `<img>`-Tag verknüpfen. Die Bereiche werden durch `<area>`-Tags definiert, wobei jede Bereichsdefinition Attribute wie `shape`, `coords` und `href` aufweist.

### Details
- **shape**: Definiert die Form des klickbaren Bereichs (z.B. `rect`, `circle`, `poly`).
- **coords**: Gibt die Koordinaten an, die die Form definieren.
- **href**: Die URL, zu der der Benutzer weitergeleitet wird, wenn der Bereich angeklickt wird.

## Beispiele
### Beispiel 1: Einfache Bildkarte
```html
<!DOCTYPE html>
<html lang="de">
<head>
    <meta charset="UTF-8">
    <title>Bildkarte Beispiel</title>
</head>
<body>
    <img src="bild.jpg" usemap="#meineKarte" alt="Ein Beispielbild">
    <map name="meineKarte">
        <area shape="rect" coords="34,44,270,350" href="link1.html" alt="Link 1">
        <area shape="circle" coords="337,300,44" href="link2.html" alt="Link 2">
    </map>
</body>
</html>
```

### Beispiel 2: Bildkarte mit polygonalem Bereich
```html
<!DOCTYPE html>
<html lang="de">
<head>
    <meta charset="UTF-8">
    <title>Bildkarte mit Polygon</title>
</head>
<body>
    <img src="bild2.jpg" usemap="#polygonKarte" alt="Ein weiteres Beispielbild">
    <map name="polygonKarte">
        <area shape="poly" coords="34,44,270,350,200,150" href="link3.html" alt="Link 3">
    </map>
</body>
</html>
```

## Erklärung
Ein häufiges Missverständnis beim Arbeiten mit `HTMLMapElement` ist die richtige Definition der Koordinaten im `coords`-Attribut. Es ist wichtig, die Koordinaten in Pixeln zu bestimmen, basierend auf der Position des Bildes, da falsche Werte dazu führen können, dass die klickbaren Bereiche nicht korrekt angezeigt werden.

Ein weiterer Punkt ist, dass das `usemap`-Attribut des `<img>`-Tags exakt mit dem `name`-Attribut des `<map>`-Tags übereinstimmen muss. Andernfalls wird die Karte nicht funktionieren.

## Ein-Satz-Zusammenfassung
Das `HTMLMapElement` ermöglicht die Erstellung interaktiver Bildkarten in HTML, die mit JavaScript manipuliert werden können, um eine benutzerfreundliche Navigation zu gewährleisten.