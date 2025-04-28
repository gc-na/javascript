<!--
Meta Description: # TextDecoderStream：JavaScript 中的文本解碼流 ## 簡介 `TextDecoderStream` 是一個用於在 JavaScript 中解碼字節流的 API，允許開發者將二進制數據流轉換為可讀的文本。它在處理流式資料時特別有用，尤其是當數據來自網絡或其他非結構化來源。...
Meta Keywords: textdecoderstream, readablestream, javascript, const, new
-->

# TextDecoderStream：JavaScript 中的文本解碼流

## 簡介
`TextDecoderStream` 是一個用於在 JavaScript 中解碼字節流的 API，允許開發者將二進制數據流轉換為可讀的文本。它在處理流式資料時特別有用，尤其是當數據來自網絡或其他非結構化來源。

## 文檔
### 目的
`TextDecoderStream` 使開發者能夠在接收字節數據的同時，逐步解碼這些數據為字符串，這在處理大型數據或流式數據時非常高效。

### 用法
要使用 `TextDecoderStream`，你需要創建一個新的實例，並將其與 `ReadableStream` 一起使用。以下是基本語法：

```javascript
const textDecoderStream = new TextDecoderStream(encoding);
```

- **encoding**：這是可選的參數，指定解碼的字符編碼方式，預設為 "utf-8"。

### 例子
以下是一個使用 `TextDecoderStream` 的基本示例：

```javascript
// 創建一個 ReadableStream，模擬字節數據流
const byteStream = new ReadableStream({
  start(controller) {
    controller.enqueue(new Uint8Array([72, 101, 108, 108, 111])); // "Hello" 的 ASCII 值
    controller.close();
  }
});

// 創建 TextDecoderStream
const textDecoderStream = new TextDecoderStream();

// 將 byteStream 通過 textDecoderStream 解碼
const readableStream = byteStream.pipeThrough(textDecoderStream);

// 讀取解碼後的文本
const reader = readableStream.getReader();

reader.read().then(({ done, value }) => {
  console.log(value); // 輸出: "Hello"
});
```

## 解釋
在使用 `TextDecoderStream` 時，有一些常見的問題和注意事項：

1. **字符編碼**：確保你使用的字符編碼與數據流的編碼相匹配，否則可能會出現解碼錯誤或無法顯示正確的文本。
  
2. **流的結束**：當 `ReadableStream` 完成時，確保調用 `controller.close()`，以正確結束解碼流。

3. **性能考量**：在處理大量數據時，使用流式解碼可以有效減少內存使用並提高性能，因為不需要將整個數據加載到內存中再進行解碼。

## 總結
`TextDecoderStream` 是一個強大的工具，可以在 JavaScript 中高效地解碼字節流為文本，特別適合流式數據處理。