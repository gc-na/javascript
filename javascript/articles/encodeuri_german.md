<!--
Meta Description: # encodeURI in JavaScript: Eine umfassende Anleitung zur URL-Kodierung ## Synopsis Die `encodeURI`-Funktion in JavaScript dient der Kodierung von URI ...
Meta Keywords: die, encodeuri, uri, werden, funktion
-->

# encodeURI in JavaScript: Eine umfassende Anleitung zur URL-Kodierung

## Synopsis
Die `encodeURI`-Funktion in JavaScript dient der Kodierung von URI (Uniform Resource Identifier)-Komponenten, um sicherzustellen, dass sie in URLs korrekt übertragen werden. Diese Funktion konvertiert bestimmte Zeichen in ihre entsprechenden UTF-8-Codierungen, um die Integrität von URLs zu gewährleisten.

## Documentation
### Zweck
Die `encodeURI`-Funktion wird verwendet, um sicherzustellen, dass URIs (Uniform Resource Identifiers) korrekt und sicher über das Internet übertragen werden. Sie wandelt Zeichen, die in URIs eine spezielle Bedeutung haben, in eine kodierte Form um. Dies ist wichtig, um Probleme mit der Interpretation von URIs zu vermeiden.

### Verwendung
Die Syntax der `encodeURI`-Funktion ist wie folgt:

```javascript
encodeURI(uri)
```

#### Parameter
- **uri** (string): Der zu kodierende URI als Zeichenfolge.

#### Rückgabewert
Die Funktion gibt eine kodierte URI zurück, wobei bestimmte Zeichen in Prozentkodierung umgewandelt werden.

### Details
- `encodeURI` kodiert keine Zeichen, die für die Struktur einer URI wichtig sind, wie `:`, `/`, `?`, `#`, `&` und `=`. Diese bleiben unverändert, um die korrekte Struktur der URI zu bewahren.
- Um individuelle Komponenten einer URI zu kodieren, wie z.B. den Query-String oder den Pfad, sollte die Funktion `encodeURIComponent` verwendet werden.

## Examples
Hier sind einige grundlegende Beispiele zur Verwendung von `encodeURI`:

```javascript
// Beispiel 1: Kodierung einer einfachen URL
let url = "https://www.example.com/über uns";
let encodedUrl = encodeURI(url);
console.log(encodedUrl); // Ausgabe: https://www.example.com/%C3%BCber%20uns

// Beispiel 2: Kodierung einer URL mit Query-Parametern
let queryUrl = "https://www.example.com/suche?name=Max Mustermann&stadt=München";
let encodedQueryUrl = encodeURI(queryUrl);
console.log(encodedQueryUrl); // Ausgabe: https://www.example.com/suche?name=Max%20Mustermann&stadt=M%C3%BCnchen
```

## Explanation
Ein häufiger Fehler ist die Verwendung von `encodeURI` anstelle von `encodeURIComponent` für die Kodierung von URI-Komponenten wie Parametern oder Fragmenten. `encodeURIComponent` kodiert auch Zeichen wie `&`, `=`, `?`, und `/`, die in diesen Kontexten wichtig sein können.

Zusätzlich wird manchmal übersehen, dass `encodeURI` keine Kodierung für Leerzeichen vornimmt; diese werden als `%20` kodiert. Das ist zwar korrekt, aber manchmal können Leerzeichen auch durch `+` ersetzt werden, wenn sie in einem URL-Query-Parameter verwendet werden, was `encodeURIComponent` erledigt.

## One Line Summary
Die `encodeURI`-Funktion in JavaScript kodiert URIs, um sicherzustellen, dass sie korrekt über das Internet übertragen werden, ohne die Struktur der URI zu verändern.