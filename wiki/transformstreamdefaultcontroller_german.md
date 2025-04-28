<!--
Meta Description: # TransformStreamDefaultController in JavaScript: Eine umfassende Anleitung ## Synopsis Der `TransformStreamDefaultController` ist ein zentraler Besta...
Meta Keywords: der, und, controller, den, const
-->

# TransformStreamDefaultController in JavaScript: Eine umfassende Anleitung

## Synopsis
Der `TransformStreamDefaultController` ist ein zentraler Bestandteil der Web Streams API in JavaScript, der es Entwicklern ermöglicht, Transformationsoperationen auf Datenströme durchzuführen. Er wird verwendet, um Daten zwischen dem lesbaren und dem schreibbaren Teil eines `TransformStream` zu steuern.

## Dokumentation
Der `TransformStreamDefaultController` ist eine interne Schnittstelle, die von der Web Streams API bereitgestellt wird. Diese Schnittstelle wird automatisch erstellt, wenn ein `TransformStream` instanziiert wird. Der Controller bietet Methoden und Eigenschaften, um Daten zu verarbeiten und zu transformieren.

### Zweck
Der Hauptzweck des `TransformStreamDefaultController` ist es, Entwicklern zu ermöglichen, Daten in einem Strom zu transformieren, während sie zwischen dem eingehenden und dem ausgehenden Teil des Streams fließen. Dies ist besonders nützlich, wenn es darum geht, Daten zu konvertieren, zu filtern oder anderweitig zu bearbeiten, bevor sie vom Verbraucher verarbeitet werden.

### Verwendung
Um den `TransformStreamDefaultController` zu verwenden, müssen Sie ein `TransformStream` erstellen und dabei eine Transformationsfunktion definieren. Diese Funktion erhält den Controller als Argument, mit dem Sie die Ausgabe des Streams steuern können.

```javascript
const transformStream = new TransformStream({
  transform(chunk, controller) {
    // Transformieren des Datenchunks
    const transformedChunk = chunk.toUpperCase();
    controller.enqueue(transformedChunk);
  }
});
```

### Methoden und Eigenschaften
- **enqueue(chunk)**: Fügt einen Datenchunk zum Ausgabestream hinzu.
- **terminate()**: Beendet den Transformationsprozess und signalisiert, dass keine weiteren Daten verarbeitet werden.

## Beispiele
Hier sind einige grundlegende Beispiele zur Verwendung des `TransformStreamDefaultController`:

### Beispiel 1: Einfache Transformation
In diesem Beispiel wird jeder empfangene Textchunk in Großbuchstaben umgewandelt.

```javascript
const { readable, writable } = new TransformStream({
  transform(chunk, controller) {
    controller.enqueue(chunk.toUpperCase());
  }
});

// Schreiben in den Stream
const writer = writable.getWriter();
writer.write('hello');
writer.write('world');
writer.close();

// Lesen vom Stream
const reader = readable.getReader();
reader.read().then(({ done, value }) => {
  console.log(value); // Ausgabe: HELLO
});
```

### Beispiel 2: Mehrere Transformationen
In diesem Beispiel werden Daten transformiert und anschließend eine bestimmte Bedingung geprüft.

```javascript
const { readable, writable } = new TransformStream({
  transform(chunk, controller) {
    const transformedChunk = chunk.trim();
    if (transformedChunk) {
      controller.enqueue(transformedChunk);
    }
  }
});

// Schreiben in den Stream
const writer = writable.getWriter();
writer.write('  hello  ');
writer.write('   world   ');
writer.close();

// Lesen vom Stream
const reader = readable.getReader();
reader.read().then(({ done, value }) => {
  console.log(value); // Ausgabe: "hello"
});
```

## Erklärung
Ein häufiger Stolperstein bei der Verwendung des `TransformStreamDefaultController` ist das Vergessen, die Methode `enqueue()` aufzurufen, um die transformierten Daten in den Ausgabestream einzufügen. Wenn Sie dies nicht tun, wird der transformierte Chunk verworfen und nicht an den Verbraucher weitergegeben.

Ein weiterer Punkt ist, dass der Controller keine Möglichkeit bietet, Fehler zu behandeln. Falls ein Fehler während der Transformation auftritt, müssen Sie sicherstellen, dass Sie den Fehler ordnungsgemäß an den Verbraucher weiterleiten.

## Einzeiliger Überblick
Der `TransformStreamDefaultController` ermöglicht die einfache Transformation von Datenströmen in JavaScript durch das Steuern der Ausgabe innerhalb eines `TransformStream`.