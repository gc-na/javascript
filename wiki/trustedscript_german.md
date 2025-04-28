<!--
Meta Description: # TrustedScript in JavaScript: Sicheres Arbeiten mit vertrauenswürdigen Skripten ## Synopsis TrustedScript ist eine Sicherheitsfunktion in JavaScript,...
Meta Keywords: trustedscript, die, ist, script, const
-->

# TrustedScript in JavaScript: Sicheres Arbeiten mit vertrauenswürdigen Skripten

## Synopsis
TrustedScript ist eine Sicherheitsfunktion in JavaScript, die es Entwicklern ermöglicht, Skripte als "vertrauenswürdig" zu kennzeichnen, um potenzielle Angriffe wie Cross-Site Scripting (XSS) zu verhindern.

## Dokumentation
### Zweck
TrustedScript wurde entwickelt, um die Sicherheit von Webanwendungen zu erhöhen. Es ermöglicht Webentwicklern, Skripte zu erstellen, die nur aus vertrauenswürdigen Quellen ausgeführt werden, wodurch das Risiko, dass bösartiger Code ausgeführt wird, erheblich reduziert wird.

### Verwendung
Um TrustedScript zu verwenden, müssen Entwickler sicherstellen, dass sie Skripte nur dann als vertrauenswürdig kennzeichnen, wenn sie sicher sind, dass sie aus einer sicheren Quelle stammen. TrustedScript ist Teil der Trusted Types API, die in modernen Browsern implementiert ist. 

Hier ist ein einfaches Beispiel zur Erstellung eines TrustedScript:

```javascript
// Erstellen eines TrustedScript
const trustedScript = TrustedTypes.createPolicy('myPolicy', {
    createScript: (script) => {
        // Überprüfen des Skripts auf Sicherheit
        return script; // Rückgabe des Skripts als vertrauenswürdig
    }
});

// Verwendung des TrustedScript
const script = trustedScript.createScript('console.log("Hallo, Welt!");');
eval(script); // Sicheres Ausführen des Skripts
```

## Beispiele
### Basisbeispiel
```javascript
const policy = TrustedTypes.createPolicy('examplePolicy', {
    createScript: (script) => script
});

const safeScript = policy.createScript('alert("Sicheres Skript!");');
eval(safeScript); // Sicheres Ausführen des Skripts
```

### Verwendung in einer Anwendung
```javascript
const myPolicy = TrustedTypes.createPolicy('appPolicy', {
    createScript: (script) => {
        // Hier könnte eine Überprüfung der Skriptinhalte stattfinden
        return script;
    }
});

const userInput = "alert('Benutzerinput!');";
const trustedUserScript = myPolicy.createScript(userInput);
eval(trustedUserScript); // Sicheres Ausführen des Skripts
```

## Erklärung
### Häufige Fallstricke
- **Fehlende Validierung:** Wenn Skripte nicht gründlich validiert werden, können Angreifer dennoch bösartigen Code einschleusen. Es ist wichtig, die Eingaben zu überprüfen, bevor sie als vertrauenswürdig eingestuft werden.
- **Verwendung von eval():** Das Verwenden von `eval()` kann riskant sein, wenn nicht sichergestellt ist, dass die übergebenen Skripte vertrauenswürdig sind.
- **Browser-Kompatibilität:** TrustedScript ist möglicherweise nicht in allen Browsern verfügbar, was die Verwendung in bestimmten Umgebungen einschränken kann.

### Zusätzliche Hinweise
Die Verwendung von TrustedScript sollte Teil einer umfassenden Sicherheitsstrategie sein, die auch andere Mechanismen wie Content Security Policy (CSP) und sichere Codierungspraktiken umfasst.

## Ein-Satz-Zusammenfassung
TrustedScript ist eine Sicherheitsfunktion in JavaScript, die es ermöglicht, Skripte als vertrauenswürdig zu kennzeichnen, um das Risiko von XSS-Angriffen zu minimieren.