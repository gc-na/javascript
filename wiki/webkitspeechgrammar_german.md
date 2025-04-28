<!--
Meta Description: # webkitSpeechGrammar: Sprachgrammatik in JavaScript für Spracherkennung ## Synopsis `webkitSpeechGrammar` ist eine Schnittstelle in JavaScript, die e...
Meta Keywords: die, webkitspeechgrammar, const, grammar, recognition
-->

# webkitSpeechGrammar: Sprachgrammatik in JavaScript für Spracherkennung

## Synopsis
`webkitSpeechGrammar` ist eine Schnittstelle in JavaScript, die es Entwicklern ermöglicht, grammatikbasierte Spracherkennung in Webanwendungen zu implementieren. Sie wird häufig in Kombination mit der `SpeechRecognition`-API verwendet, um spezifische Sprachbefehle und -muster zu definieren.

## Documentation
### Zweck
`webkitSpeechGrammar` dient der Definition von Grammatikregeln für die Spracherkennung in Webanwendungen. Mit dieser Schnittstelle können Entwickler benutzerdefinierte Sprachbefehle festlegen, die die Erkennung von Sprache durch den Browser verbessern.

### Verwendung
Um `webkitSpeechGrammar` zu verwenden, muss die `SpeechRecognition`-API aktiviert sein. Diese API ermöglicht es Entwicklern, Spracherkennung in ihren Anwendungen zu integrieren. Die Grammatik wird in Form von BNF (Backus-Naur-Form) definiert und kann als Teil der `SpeechRecognition`-Instanz hinzugefügt werden.

### Details
- **Syntax**: 
  ```javascript
  const grammar = '#JSGF V1.0; grammar commands; public <command> = start | stop | pause ;';
  const speechGrammar = new webkitSpeechGrammar(grammar);
  ```
- **Einschränkungen**: `webkitSpeechGrammar` wird derzeit hauptsächlich in WebKit-basierten Browsern wie Chrome unterstützt.

## Examples
### Beispiel 1: Einfache Sprachgrammatik
```javascript
const recognition = new webkitSpeechRecognition();
const grammar = '#JSGF V1.0; grammar commands; public <command> = hello | bye | help ;';
const speechGrammar = new webkitSpeechGrammar(grammar);

recognition.grammars = speechGrammar;

recognition.onresult = function(event) {
  const spokenCommand = event.results[0][0].transcript;
  console.log('Erkannter Befehl: ', spokenCommand);
};

recognition.start();
```

### Beispiel 2: Erweiterte Sprachgrammatik
```javascript
const recognition = new webkitSpeechRecognition();
const grammar = '#JSGF V1.0; grammar commands; public <action> = play | pause | stop ;';
const speechGrammar = new webkitSpeechGrammar(grammar);

recognition.grammars = speechGrammar;

recognition.onresult = function(event) {
  const spokenAction = event.results[0][0].transcript;
  console.log('Aktion erkannt: ', spokenAction);
};

recognition.start();
```

## Explanation
Bei der Verwendung von `webkitSpeechGrammar` sollten Entwickler darauf achten, dass die Grammatik korrekt definiert ist, da Fehler in der Grammatik zu unerwarteten Ergebnissen führen können. Außerdem ist die Unterstützung für `webkitSpeechGrammar` auf bestimmte Browser beschränkt, was die Interoperabilität beeinträchtigen kann. Nutzer sollten auch sicherstellen, dass sie die richtigen Berechtigungen für die Spracherkennung in ihrer Anwendung anfordern, um eine reibungslose Benutzererfahrung zu gewährleisten.

## One Line Summary
`webkitSpeechGrammar` ermöglicht die Definition benutzerdefinierter Sprachbefehle in JavaScript, um die Spracherkennung in Webanwendungen zu verbessern.