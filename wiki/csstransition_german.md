<!--
Meta Description: # CSSTransition in JavaScript: Ein Leitfaden zur Anwendung in React ## Synopsis CSSTransition ist ein leistungsfähiges Werkzeug in der React-Bibliothe...
Meta Keywords: die, csstransition, react, css, transition
-->

# CSSTransition in JavaScript: Ein Leitfaden zur Anwendung in React

## Synopsis
CSSTransition ist ein leistungsfähiges Werkzeug in der React-Bibliothek, das Entwicklern ermöglicht, CSS-Übergänge beim Ein- und Ausblenden von Komponenten zu steuern. Es verbessert die Benutzeroberfläche durch sanfte Animationen und erleichtert die Handhabung von CSS-Transitions in React-Anwendungen.

## Dokumentation
CSSTransition gehört zur React-Transition-Group und wird verwendet, um CSS-Transitionen für React-Komponenten zu implementieren. Es ermöglicht Entwicklern, Animationen für Komponenten zu definieren, die in den DOM eingefügt oder daraus entfernt werden. Die Hauptfunktion von CSSTransition besteht darin, CSS-Klassen zu den Phasen einer Transition hinzuzufügen und zu entfernen, wodurch visuelle Effekte erzeugt werden.

### Zweck
Der Hauptzweck von CSSTransition ist es, die Benutzererfahrung durch Animationen zu verbessern und gleichzeitig die Kontrolle über die Animationen zu behalten, die während des Lebenszyklus von React-Komponenten stattfinden.

### Verwendung
Um CSSTransition zu verwenden, müssen Sie die React-Transition-Group-Bibliothek in Ihr Projekt einbinden. Installieren Sie die Bibliothek mit npm oder yarn:

```bash
npm install react-transition-group
```
oder
```bash
yarn add react-transition-group
```

Nach der Installation können Sie CSSTransition in Ihrer Komponente importieren:

```javascript
import { CSSTransition } from 'react-transition-group';
```

### Eigenschaften
- **in**: (boolean) Steuert, ob die Komponente sichtbar ist.
- **timeout**: (number|object) Legt die Dauer der Transition fest.
- **classNames**: (string) Definiert die Basisklasse für die CSS-Transition.
- **onEnter**: (function) Callback, der bei Eintritt der Komponente aufgerufen wird.
- **onExited**: (function) Callback, der aufgerufen wird, nachdem die Komponente ausgeblendet wurde.

## Beispiele
Hier sind einige einfache Beispiele zur Verwendung von CSSTransition:

### Beispiel 1: Einfache CSSTransition

```javascript
import React, { useState } from 'react';
import { CSSTransition } from 'react-transition-group';
import './styles.css'; // Importieren Sie Ihre CSS-Datei

const Example = () => {
  const [show, setShow] = useState(false);

  return (
    <div>
      <button onClick={() => setShow(!show)}>
        {show ? 'Verstecken' : 'Anzeigen'}
      </button>
      <CSSTransition
        in={show}
        timeout={300}
        classNames="fade"
        unmountOnExit
      >
        <div className="fade">Hallo Welt!</div>
      </CSSTransition>
    </div>
  );
};

export default Example;
```

### Beispiel 2: CSSTransition mit benutzerdefinierten Klassen

```javascript
import React, { useState } from 'react';
import { CSSTransition } from 'react-transition-group';
import './styles.css';

const CustomTransitionExample = () => {
  const [show, setShow] = useState(false);

  return (
    <div>
      <button onClick={() => setShow(!show)}>
        {show ? 'Verstecken' : 'Anzeigen'}
      </button>
      <CSSTransition
        in={show}
        timeout={500}
        classNames="custom"
        unmountOnExit
      >
        <div className="custom">Animate me!</div>
      </CSSTransition>
    </div>
  );
};

export default CustomTransitionExample;
```

## Erklärung
Ein häufiger Stolperstein bei der Verwendung von CSSTransition ist die korrekte Handhabung der CSS-Klassen. Stellen Sie sicher, dass die CSS-Klassen, die Sie für die Animationen definieren, mit den von CSSTransition generierten Klassen übereinstimmen (z.B. `fade-enter`, `fade-enter-active`, `fade-exit`, `fade-exit-active`). Unzureichende oder falsch benannte Klassen können dazu führen, dass die Animationen nicht wie erwartet funktionieren.

Darüber hinaus ist es wichtig, den `timeout`-Wert korrekt einzustellen, um sicherzustellen, dass die Animationen synchronisiert sind. Ein zu kurzer oder zu langer Wert kann dazu führen, dass Animationen flackern oder nicht ordnungsgemäß ausgeführt werden.

## Eine Zeile Zusammenfassung
CSSTransition ist ein React-Komponentenwerkzeug zur Implementierung von CSS-Übergängen, das die Benutzeroberfläche mit sanften Animationen verbessert.