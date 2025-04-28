<!--
Meta Description: # TextDecoderStream in JavaScript: Efficiently Decoding Text Streams ## Synopsis `TextDecoderStream` is a JavaScript interface that provides a way to ...
Meta Keywords: textdecoderstream, data, streams, javascript, text
-->

# TextDecoderStream in JavaScript: Efficiently Decoding Text Streams

## Synopsis
`TextDecoderStream` is a JavaScript interface that provides a way to decode streams of binary data into text using specified character encodings, enabling seamless handling of various text formats in modern web applications.

## Documentation
`TextDecoderStream` is part of the Encoding API and is used to convert incoming byte streams into string data. This is particularly useful when working with streams of binary data, such as those received from network requests or file reads.

### Purpose
The primary purpose of `TextDecoderStream` is to decode byte streams into readable text format, which can be especially beneficial in scenarios involving large data streams, like fetching text from a remote server.

### Usage
To create a `TextDecoderStream`, you can instantiate it with an optional encoding parameter. If no encoding is specified, it defaults to "utf-8".

#### Syntax
```javascript
const decoderStream = new TextDecoderStream(encoding);
```

- **Parameters:**
  - `encoding` (optional): A string representing the character encoding (e.g., "utf-8", "utf-16", "iso-8859-2").

### Properties
- **ReadableStream**: The stream from which you can read the decoded text.
- **WritableStream**: The stream to which you can write the binary data for decoding.

### Methods
- **getReader()**: Returns a `ReadableStreamDefaultReader` allowing you to read from the stream.

## Examples

### Basic Example
Here is a simple example of how to use `TextDecoderStream` in conjunction with the Fetch API to decode a response:

```javascript
async function fetchAndDecode(url) {
    const response = await fetch(url);
    const reader = response.body
        .pipeThrough(new TextDecoderStream())
        .getReader();

    let result = '';
    let chunk;

    while (!(chunk = await reader.read()).done) {
        result += chunk.value;
    }

    console.log(result);
}

fetchAndDecode('https://example.com/data');
```

### Using Different Encodings
You can specify a different encoding, such as "utf-16":

```javascript
const decoderStream = new TextDecoderStream('utf-16');
```

### Streaming Data
You can also use `TextDecoderStream` with the `ReadableStream` API to process data in chunks:

```javascript
const readableStream = new ReadableStream({
    start(controller) {
        controller.enqueue(new Uint8Array([72, 101, 108, 108, 111])); // Hello in bytes
        controller.close();
    }
});

const decodedStream = readableStream.pipeThrough(new TextDecoderStream());
const reader = decodedStream.getReader();

reader.read().then(({ done, value }) => {
    console.log(value); // Output: Hello
});
```

## Explanation
When using `TextDecoderStream`, it's important to be aware of the following:

- **Stream Management**: Manage the flow of data properly; ensure to close streams when done to avoid memory leaks.
- **Error Handling**: Be mindful of potential decoding errors, especially when dealing with unknown or unsupported encodings.
- **Performance**: Streams are processed in chunks, which can improve performance when handling large datasets compared to processing entire data sets at once.

## One Line Summary
`TextDecoderStream` in JavaScript allows efficient decoding of byte streams into text, facilitating the handling of various character encodings in web applications.