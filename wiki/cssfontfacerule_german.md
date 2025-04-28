<!--
Meta Description: # CSSFontFaceRule in JavaScript: Eine umfassende Anleitung ## Synopsis Die `CSSFontFaceRule` ist eine wichtige Schnittstelle in der JavaScript-API, di...
Meta Keywords: die, der, cssfontfacerule, font, schriftart
-->

# CSSFontFaceRule in JavaScript: Eine umfassende Anleitung

## Synopsis
Die `CSSFontFaceRule` ist eine wichtige Schnittstelle in der JavaScript-API, die es Entwicklern ermöglicht, Schriftarten in CSS über das DOM zu verwalten. Sie ist Teil der CSS Object Model (CSSOM) und wird verwendet, um Regeldefinitionen für benutzerdefinierte Schriftarten zu erstellen und zu modifizieren.

## Dokumentation

### Zweck
Die `CSSFontFaceRule` dient dazu, Schriftarten zu definieren, die in einer Website verwendet werden können. Sie ermöglicht es Entwicklern, Schriftarten programmatisch hinzuzufügen, zu ändern oder zu entfernen und dabei die Eigenschaften wie Schriftfamilie, Quelle, Stil und Gewicht zu steuern.

### Verwendung
Um eine `CSSFontFaceRule` zu verwenden, muss sie zunächst Teil einer CSS-Regel sein, die in einem Stylesheet definiert ist. Sie kann über die `cssRules`-Eigenschaft eines Stylesheets abgerufen werden. Hier ist ein typisches Beispiel für die Struktur einer `@font-face`-Regel:

```css
@font-face {
  font-family: 'MyCustomFont';
  src: url('mycustomfont.woff2') format('woff2');
  font-weight: normal;
  font-style: normal;
}
```

In JavaScript kann diese Regel durch den Zugriff auf das Stylesheet und das Filtern der Regeln manipuliert werden.

### Details
Die `CSSFontFaceRule` hat mehrere Eigenschaften, die für die Definition einer Schriftart verwendet werden:

- **style**: Ein CSSStyleDeclaration-Objekt, das die Schriftarteigenschaften enthält.
- **fontFamily**: Der Name der Schriftart.
- **src**: Die Quelle der Schriftart, typischerweise eine URL zu einer .woff oder .ttf Datei.
- **fontWeight**: Das Gewicht der Schriftart (z.B. normal, bold).
- **fontStyle**: Der Stil der Schriftart (z.B. normal, italic).

## Beispiele

### Beispiel 1: Hinzufügen einer Schriftart

```javascript
const styleSheet = document.styleSheets[0];
styleSheet.insertRule(`
  @font-face {
    font-family: 'MyCustomFont';
    src: url('mycustomfont.woff2') format('woff2');
    font-weight: normal;
    font-style: normal;
  }
`, styleSheet.cssRules.length);
```

### Beispiel 2: Ändern einer bestehenden Schriftart

```javascript
const styleSheet = document.styleSheets[0];
const fontFaceRule = Array.from(styleSheet.cssRules).find(rule => rule instanceof CSSFontFaceRule && rule.style.fontFamily === 'MyCustomFont');

if (fontFaceRule) {
  fontFaceRule.style.fontWeight = 'bold'; // Ändert das Gewicht der Schriftart
}
```

## Erklärung
Ein häufiges Problem beim Arbeiten mit `CSSFontFaceRule` ist, dass die Schriftart möglicherweise nicht korrekt geladen wird, wenn die URL falsch ist oder die Schriftartdatei nicht im richtigen Format vorliegt. Achten Sie darauf, kompatible Schriftformate zu verwenden und die URLs zu testen.

Ein weiteres häufiges Missverständnis besteht darin, dass Änderungen an der `CSSFontFaceRule` nicht sofort sichtbar sind. Da Schriftarten oft im Cache gespeichert werden, kann es einige Zeit dauern, bis Änderungen wirksam werden.

## Zusammenfassung in einem Satz
Die `CSSFontFaceRule` ermöglicht die programmatische Definition und Verwaltung von benutzerdefinierten Schriftarten in CSS über JavaScript, was Entwicklern Flexibilität und Kontrolle über das Schriftarten-Management auf ihrer Website gibt.