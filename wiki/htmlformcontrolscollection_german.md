<!--
Meta Description: # HTMLFormControlsCollection in JavaScript: Eine umfassende Anleitung ## Synopsis Die `HTMLFormControlsCollection` ist eine wichtige Schnittstelle in ...
Meta Keywords: die, htmlformcontrolscollection, form, steuerelemente, controls
-->

# HTMLFormControlsCollection in JavaScript: Eine umfassende Anleitung

## Synopsis
Die `HTMLFormControlsCollection` ist eine wichtige Schnittstelle in der Webentwicklung mit JavaScript, die eine Sammlung von Formularsteuerelementen in einem HTML-Dokument darstellt. Sie ermöglicht Entwicklern den Zugriff und die Manipulation der Formularelemente innerhalb eines `<form>`-Tags.

## Dokumentation
Die `HTMLFormControlsCollection` ist Teil des DOM (Document Object Model) und wird verwendet, um eine Sammlung von Steuerelementen (wie `<input>`, `<select>`, `<textarea>` usw.) zu repräsentieren, die innerhalb eines Formulars definiert sind. Diese Schnittstelle bietet eine einfache Möglichkeit, auf die verschiedenen Steuerelemente zuzugreifen, sie zu modifizieren oder ihre Werte zu lesen.

### Verwendung
Um auf die `HTMLFormControlsCollection` zuzugreifen, kann der `elements`-Eigenschaft eines Formular-Elements verwendet werden. Hier ist ein Beispiel, wie man auf die Steuerelemente eines Formulars zugreifen kann:

```javascript
const form = document.querySelector('form');
const controls = form.elements;
```

Die `controls`-Variable enthält nun eine `HTMLFormControlsCollection`, die alle Steuerelemente des Formulars umfasst. Sie können auf individuelle Steuerelemente über ihren Namen oder Index zugreifen:

```javascript
const username = controls['username']; // Zugriff über Namen
const firstInput = controls[0]; // Zugriff über Index
```

### Details
Die `HTMLFormControlsCollection` unterstützt verschiedene Methoden und Eigenschaften, die Entwicklern helfen, mit den Formularsteuerelementen zu interagieren. Einige wichtige Methoden sind:

- `item(index)`: Gibt das Steuerelement am angegebenen Index zurück.
- `namedItem(name)`: Gibt das Steuerelement mit dem angegebenen Namen zurück.

Die Sammlung ist "lebendig", was bedeutet, dass sie automatisch aktualisiert wird, wenn Steuerelemente zum Formular hinzugefügt oder daraus entfernt werden.

## Beispiele
Hier sind einige grundlegende Beispiele zur Veranschaulichung der Verwendung von `HTMLFormControlsCollection`:

### Beispiel 1: Zugriff auf Steuerelemente
```html
<form id="myForm">
  <input type="text" name="username" />
  <input type="password" name="password" />
  <button type="submit">Einloggen</button>
</form>

<script>
  const form = document.getElementById('myForm');
  const controls = form.elements;

  console.log(controls['username'].value); // Ausgabe des Wertes des Benutzernamens
</script>
```

### Beispiel 2: Iteration über alle Steuerelemente
```javascript
const form = document.getElementById('myForm');
const controls = form.elements;

for (let i = 0; i < controls.length; i++) {
  console.log(controls[i].name, controls[i].value);
}
```

## Erklärung
Ein häufiger Stolperstein bei der Verwendung von `HTMLFormControlsCollection` ist das Missverständnis bezüglich der Indexierung und der Verwendung von Namen. Es ist wichtig zu beachten, dass die Indizes, die für den Zugriff auf Steuerelemente verwendet werden, nullbasiert sind. Zudem können mehrere Steuerelemente denselben Namen haben, was möglicherweise zu Verwirrung führen kann, wenn Sie versuchen, sie über den Namen abzurufen.

Ein weiterer Punkt ist, dass die `HTMLFormControlsCollection` nicht nur die Eingabefelder, sondern auch andere Steuerelemente wie `<button>` und `<select>` umfasst, die möglicherweise nicht sofort als Teil der Sammlung wahrgenommen werden.

## Ein-Satz-Zusammenfassung
Die `HTMLFormControlsCollection` in JavaScript ermöglicht den Zugriff auf und die Manipulation von Formularsteuerelementen in einem HTML-Dokument, was die Handhabung von Benutzereingaben vereinfacht.