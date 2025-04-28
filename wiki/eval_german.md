<!--
Meta Description: # eval in JavaScript: So funktioniert der Befehl zur Ausführung von Code ## Synopsis Der `eval`-Befehl in JavaScript ist eine Funktion, die es ermögli...
Meta Keywords: eval, der, javascript, code, die
-->

# eval in JavaScript: So funktioniert der Befehl zur Ausführung von Code

## Synopsis
Der `eval`-Befehl in JavaScript ist eine Funktion, die es ermöglicht, einen String als JavaScript-Code auszuführen. Diese Funktion kann nützlich sein, birgt jedoch auch Sicherheitsrisiken und Performance-Probleme.

## Dokumentation

### Zweck
Der `eval`-Befehl wird verwendet, um JavaScript-Code, der in Form eines Strings vorliegt, zur Laufzeit auszuführen. Dies kann hilfreich sein, wenn Code dynamisch generiert werden muss oder wenn man mit Benutzereingaben arbeiten möchte.

### Verwendung
Die Verwendung des `eval`-Befehls erfolgt durch den Aufruf der Funktion mit einem String als Argument:

```javascript
eval(string);
```

Hierbei wird der übergebene String als JavaScript-Code interpretiert und ausgeführt.

### Details
- **Rückgabewert**: Der Rückgabewert von `eval` ist der Wert des letzten Ausdrucks, der im übergebenen String ausgeführt wurde. Falls der String keinen Ausdruck enthält, wird `undefined` zurückgegeben.
- **Gültigkeitsbereich**: Der Code, der durch `eval` ausgeführt wird, hat Zugriff auf den aktuellen Gültigkeitsbereich, was bedeutet, dass Variablen und Funktionen, die außerhalb von `eval` definiert sind, innerhalb des evaluierten Codes verwendet werden können.
- **Sicherheitsrisiken**: Die Verwendung von `eval` kann zu Sicherheitsanfälligkeiten führen, insbesondere wenn Benutzereingaben ohne Validierung ausgeführt werden. Dies kann zu Code-Injection-Angriffen führen.

## Beispiele

### Einfaches Beispiel
```javascript
let x = 10;
let result = eval("x + 5");
console.log(result); // Ausgabe: 15
```

### Funktion definieren
```javascript
let code = "function add(a, b) { return a + b; } add(2, 3);";
let sum = eval(code);
console.log(sum); // Ausgabe: 5
```

### Dynamische Variablen
```javascript
let varName = "dynamicVar";
eval(varName + " = 20;");
console.log(dynamicVar); // Ausgabe: 20
```

## Erklärung

### Häufige Fallstricke
- **Sicherheitsprobleme**: Die Ausführung von untrusted Input durch `eval` kann zu schwerwiegenden Sicherheitslücken führen. Es ist ratsam, `eval` zu vermeiden, wenn dies möglich ist.
- **Performance**: `eval` kann die Ausführungszeit des Codes erhöhen, da der JavaScript-Interpreter nicht optimieren kann, was durch `eval` ausgeführt wird.
- **Debugging**: Der Debugging-Prozess kann erschwert werden, da Fehler, die durch `eval` verursacht werden, schwer zu lokalisieren sind.

### Zusätzliche Hinweise
- `eval` kann in `strict mode` verwendet werden, jedoch sind die Gültigkeitsbereichsregeln anders.
- In vielen Fällen gibt es sicherere Alternativen zu `eval`, wie die Verwendung von Funktionen oder der `Function`-Konstruktor.

## Ein-Satz-Zusammenfassung
Der `eval`-Befehl in JavaScript ermöglicht die Ausführung von Code, der als String vorliegt, sollte jedoch wegen der damit verbundenen Sicherheits- und Performanceprobleme mit Vorsicht verwendet werden.