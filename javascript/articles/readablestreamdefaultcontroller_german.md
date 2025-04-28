<!--
Meta Description: # ReadableStreamDefaultController in JavaScript: Ein umfassender Leitfaden ## Synopsis Die `ReadableStreamDefaultController` ist eine Schnittstelle in...
Meta Keywords: stream, controller, die, ein, readablestream
-->

# ReadableStreamDefaultController in JavaScript: Ein umfassender Leitfaden

## Synopsis
Die `ReadableStreamDefaultController` ist eine Schnittstelle in JavaScript, die zur Steuerung von `ReadableStream`-Instanzen verwendet wird. Sie ermöglicht das Hinzufügen, Entfernen und Verwalten von Datenströmen in einer asynchronen Umgebung.

## Dokumentation
Die `ReadableStreamDefaultController` ist ein wichtiger Bestandteil der Streams-API in JavaScript. Sie wird verwendet, um die Daten, die von einem `ReadableStream` bereitgestellt werden, zu steuern und zu manipulieren. Diese Schnittstelle stellt Methoden zur Verfügung, mit denen Sie Daten in den Stream einfügen oder die Leseposition verwalten können, was eine effiziente Handhabung von Datenströmen ermöglicht.

### Zweck
Der Hauptzweck der `ReadableStreamDefaultController` besteht darin, die Kontrolle über den Lesevorgang eines Streams zu ermöglichen. Sie wird automatisch erstellt, wenn Sie einen neuen `ReadableStream` erstellen und kann nicht direkt instanziiert werden.

### Nutzung
Um `ReadableStreamDefaultController` zu nutzen, müssen Sie einen `ReadableStream` erstellen und einen `start`-Callback bereitstellen, in dem Sie auf den Controller zugreifen können. Hier ist ein einfaches Beispiel:

```javascript
const stream = new ReadableStream({
  start(controller) {
    controller.enqueue('Hello, ');
    controller.enqueue('World!');
    controller.close();
  }
});
```

In diesem Beispiel wird der `start`-Callback verwendet, um Daten in den Stream hinzuzufügen und den Stream zu schließen.

### Methoden
- **enqueue(chunk)**: Fügt einen Chunk von Daten in den Stream ein.
- **close()**: Schließt den Stream, wenn keine weiteren Daten mehr gesendet werden.
- **error(e)**: Signalisiert einen Fehler im Stream.

## Beispiele

### Beispiel 1: Einfacher Datenstrom
```javascript
const stream = new ReadableStream({
  start(controller) {
    controller.enqueue('Data chunk 1');
    controller.enqueue('Data chunk 2');
    controller.close();
  }
});

const reader = stream.getReader();
reader.read().then(({ done, value }) => {
  console.log(value); // "Data chunk 1"
});
```

### Beispiel 2: Stream mit Fehlerbehandlung
```javascript
const stream = new ReadableStream({
  start(controller) {
    controller.enqueue('Chunk 1');
    controller.error('An error occurred'); // Signalisiert einen Fehler
  }
});

const reader = stream.getReader();
reader.read().catch(err => {
  console.error(err); // "An error occurred"
});
```

## Erklärung
Ein häufiges Missverständnis im Umgang mit `ReadableStreamDefaultController` ist, dass man die Methoden `enqueue`, `close` und `error` auch außerhalb des `start`-Callbacks verwenden kann. Diese Methoden sind jedoch nur im Kontext des Controllers gültig. Ein weiterer Fallstrick ist das Verständnis des Stream-Zustands – nachdem ein Stream geschlossen wurde, kann er nicht mehr verwendet werden.

## Ein-Satz-Zusammenfassung
Die `ReadableStreamDefaultController` ermöglicht eine präzise Steuerung von `ReadableStream`-Instanzen in JavaScript, einschließlich Datenverwaltung und Fehlerbehandlung.