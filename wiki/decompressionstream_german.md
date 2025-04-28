<!--
Meta Description: # DecompressionStream in JavaScript: Entpacken von Datenströmen ## Synopsis Der `DecompressionStream` in JavaScript ist eine Schnittstelle zur Dekompr...
Meta Keywords: decompressionstream, der, die, const, javascript
-->

# DecompressionStream in JavaScript: Entpacken von Datenströmen

## Synopsis
Der `DecompressionStream` in JavaScript ist eine Schnittstelle zur Dekompression von komprimierten Datenströmen. Es ermöglicht Entwicklern, Daten, die in Formaten wie Gzip oder Brotli komprimiert sind, effizient zu entpacken und zu verarbeiten.

## Documentation
### Zweck
Der `DecompressionStream` wird verwendet, um komprimierte Datenströme zu dekomprimieren. Dies ist besonders nützlich in Anwendungen, die große Datenmengen verarbeiten, die zur Reduzierung der Bandbreite komprimiert wurden.

### Verwendung
Um einen `DecompressionStream` zu nutzen, müssen Sie die `ReadableStream`-Schnittstelle bereitstellen, die komprimierte Daten enthält. Der `DecompressionStream` erstellt dann einen neuen lesbaren Stream, der die dekomprimierten Daten bereitstellt.

### Details
- **Syntax**: 
  ```javascript
  const decompressionStream = new DecompressionStream(format);
  ```
  - `format`: Der Komprimierungsformattyp, z.B. `'gzip'` oder `'brotli'`.

- **Integration**: Der `DecompressionStream` kann mit Fetch-API oder anderen Stream-APIs verwendet werden, um Daten während des Empfangs zu dekomprimieren.

## Examples
### Beispiel 1: Verwendung mit Fetch-API
```javascript
fetch('data.json.gz')
  .then(response => {
    const reader = response.body
      .pipeThrough(new DecompressionStream('gzip'))
      .getReader();

    return reader.read();
  })
  .then(({ done, value }) => {
    if (!done) {
      const text = new TextDecoder().decode(value);
      console.log(text);
    }
  });
```

### Beispiel 2: Dekompression eines Blob
```javascript
const blob = new Blob([compressedData], { type: 'application/gzip' });
const stream = blob.stream();
const decompressedStream = stream.pipeThrough(new DecompressionStream('gzip'));

const reader = decompressedStream.getReader();
reader.read().then(({ done, value }) => {
  const text = new TextDecoder().decode(value);
  console.log(text);
});
```

## Explanation
Ein häufiger Fehler besteht darin, den `DecompressionStream` mit unpassenden oder nicht unterstützten Komprimierungsformaten zu verwenden. Stellen Sie sicher, dass Sie den richtigen Typ angeben, um Fehler bei der Dekompression zu vermeiden. 

Ein weiterer Punkt ist, dass der `DecompressionStream` nur mit `ReadableStream`-Daten funktioniert. Achten Sie darauf, dass die Quelldaten tatsächlich komprimiert sind. Andernfalls kann der Stream nicht korrekt verarbeitet werden.

## One Line Summary
Der `DecompressionStream` in JavaScript ermöglicht die effiziente Dekompression von komprimierten Datenströmen wie Gzip oder Brotli.