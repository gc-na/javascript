<!--
Meta Description: # XMLHttpRequest in JavaScript: Eine umfassende Anleitung ## Synopsis XMLHttpRequest ist ein JavaScript-Objekt, das verwendet wird, um HTTP-Anfragen a...
Meta Keywords: xhr, die, xmlhttprequest, sie, ist
-->

# XMLHttpRequest in JavaScript: Eine umfassende Anleitung

## Synopsis
XMLHttpRequest ist ein JavaScript-Objekt, das verwendet wird, um HTTP-Anfragen an Server zu senden und Antworten zu empfangen, ohne die Webseite neu zu laden. Es ermöglicht datengetriebenes Arbeiten und ist ein zentraler Bestandteil des AJAX-Konzepts.

## Dokumentation
### Zweck
XMLHttpRequest (XHR) wird verwendet, um asynchrone HTTP-Anfragen zu stellen. Dies ermöglicht Entwicklern, Daten im Hintergrund von einem Server abzurufen oder zu senden und die Benutzeroberfläche dynamisch zu aktualisieren, ohne die gesamte Seite neu laden zu müssen.

### Verwendung
Um XMLHttpRequest zu verwenden, müssen Sie ein neues XHR-Objekt erstellen und dann die gewünschten HTTP-Methoden wie `GET`, `POST`, `PUT` oder `DELETE` verwenden. Der Prozess umfasst mehrere Schritte:

1. Erstellen Sie ein neues XMLHttpRequest-Objekt.
2. Konfigurieren Sie die Anfrage mit der Methode und der URL.
3. Fügen Sie einen Event-Listener für den `onreadystatechange`-Event hinzu, um die Antwort zu verarbeiten.
4. Senden Sie die Anfrage mit der Methode `send()`.

### Details
- **Methoden**: `open(method, url, async, user, password)`, `send(data)`, `setRequestHeader(header, value)`.
- **Eigenschaften**: `readyState`, `status`, `responseText`, `responseXML`.
- **Zustände**: Der `readyState` kann Werte von 0 (UNSENT) bis 4 (DONE) annehmen, was den Status der Anfrage angibt.

## Beispiele
### Beispiel 1: Einfache GET-Anfrage
```javascript
let xhr = new XMLHttpRequest();
xhr.open("GET", "https://api.example.com/data", true);
xhr.onreadystatechange = function() {
    if (xhr.readyState === 4 && xhr.status === 200) {
        console.log(xhr.responseText);
    }
};
xhr.send();
```

### Beispiel 2: POST-Anfrage mit Daten
```javascript
let xhr = new XMLHttpRequest();
xhr.open("POST", "https://api.example.com/submit", true);
xhr.setRequestHeader("Content-Type", "application/json;charset=UTF-8");
xhr.onreadystatechange = function() {
    if (xhr.readyState === 4 && xhr.status === 201) {
        console.log("Daten erfolgreich gesendet!");
    }
};
xhr.send(JSON.stringify({ name: "Max", alter: 30 }));
```

## Erklärung
**Häufige Fallstricke**:
- **CORS-Probleme**: Bei Anfragen an eine andere Domain können Cross-Origin Resource Sharing (CORS)-Fehler auftreten, wenn der Server nicht richtig konfiguriert ist.
- **Asynchrone Verarbeitung**: Wenn Sie nicht darauf achten, dass die Anfrage asynchron ist, können Sie versuchen, auf die Antwort zuzugreifen, bevor sie verfügbar ist.
- **Statuscodes**: Es ist wichtig, die HTTP-Statuscodes zu überprüfen, um sicherzustellen, dass die Anfrage erfolgreich war.

**Zusätzliche Hinweise**:
- In modernen Webanwendungen wird häufig die Fetch API bevorzugt, da sie eine einfachere und intuitivere Syntax bietet. Dennoch bleibt XMLHttpRequest weit verbreitet und ist in vielen bestehenden Anwendungen zu finden.

## Ein-Satz-Zusammenfassung
XMLHttpRequest ist ein JavaScript-Objekt für asynchrone HTTP-Anfragen, das die dynamische Interaktion mit Servern ermöglicht, ohne die Webseite neu laden zu müssen.