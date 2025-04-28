<!--
Meta Description: # TextDecoderStream：JavaScript中的文字解碼串流 ## 概述 `TextDecoderStream` 是一個用於解碼字節串流的 JavaScript API，允許開發者在處理二進制數據時，將字節轉換為可讀的文本格式。此功能對於處理來自網絡流或檔案的數據尤為重要。 ## 文...
Meta Keywords: textdecoderstream, const, controller, utf, new
-->

# TextDecoderStream：JavaScript中的文字解碼串流

## 概述
`TextDecoderStream` 是一個用於解碼字節串流的 JavaScript API，允許開發者在處理二進制數據時，將字節轉換為可讀的文本格式。此功能對於處理來自網絡流或檔案的數據尤為重要。

## 文件說明
`TextDecoderStream` 是一個可用於解碼 `Uint8Array` 或其他類型的二進制數據的串流 API。它的主要目的是提供一種高效且簡化的方式來將字節流轉換為字符串，支援多種字符編碼（如 UTF-8、UTF-16等）。

### 用法
要使用 `TextDecoderStream`，首先需要創建一個新的實例，然後將其用作可讀串流的解碼器。

```javascript
const decoder = new TextDecoderStream(encoding);
```

在此，`encoding` 是一個可選的參數，預設為 `"utf-8"`。接下來，你可以將 `TextDecoderStream` 與 `ReadableStream` 結合使用。

```javascript
const readableStream = new ReadableStream({
    start(controller) {
        // 將二進制數據推送到控制器中
        controller.enqueue(new Uint8Array([/* byte data */]));
        controller.close();
    }
});

const decodedStream = readableStream.pipeThrough(decoder);
```

### 主要特點
- **支援多種編碼**：能夠處理多種字符編碼，包括 UTF-8、UTF-16 等。
- **串流處理**：能夠按需解碼資料，避免一次性讀取大量數據。

## 範例
以下是使用 `TextDecoderStream` 的基本範例：

```javascript
const { ReadableStream, TextDecoderStream } = require('stream/web');

const byteStream = new ReadableStream({
    start(controller) {
        controller.enqueue(new Uint8Array([72, 101, 108, 108, 111])); // "Hello" 的字節
        controller.close();
    }
});

const decoder = new TextDecoderStream('utf-8');
const textStream = byteStream.pipeThrough(decoder);

const reader = textStream.getReader();
reader.read().then(({ done, value }) => {
    console.log(value); // 輸出 "Hello"
});
```

## 解釋
在使用 `TextDecoderStream` 時，需要注意以下幾點：

- **編碼問題**：確保使用正確的編碼格式，否則可能導致解碼失敗或結果不正確。
- **流的關閉**：在推送數據後，記得調用 `controller.close()` 來關閉流。
- **性能考量**：雖然串流處理可以減少內存使用，但在大量數據處理時，仍需考慮性能影響。

## 總結
`TextDecoderStream` 是 JavaScript 中一個強大的 API，用於有效地解碼字節流為文本，支援多種字符編碼，適合在處理網絡數據時使用。