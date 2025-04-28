<!--
Meta Description: # TextEncoderStream：JavaScript 中的文本編碼流 ## 概述 TextEncoderStream 是一個 JavaScript 的內建 API，提供了一個流式的方式來將文本數據編碼成二進制格式。此功能非常適合需要處理大量文本數據並轉換為可發送或存儲的格式的應用程式。 ##...
Meta Keywords: textencoderstream, const, encoderstream, writer, reader
-->

# TextEncoderStream：JavaScript 中的文本編碼流

## 概述
TextEncoderStream 是一個 JavaScript 的內建 API，提供了一個流式的方式來將文本數據編碼成二進制格式。此功能非常適合需要處理大量文本數據並轉換為可發送或存儲的格式的應用程式。

## 文檔
TextEncoderStream 的主要目的是提供一個可讀取和可寫入的流，以便將 UTF-8 編碼的文本轉換為 Uint8Array 格式的二進制數據。這對於網絡傳輸或文件存儲特別有用，因為二進制格式通常比文本格式更高效。

### 使用方式
要使用 TextEncoderStream，您可以通過以下步驟進行操作：

1. 創建一個 TextEncoderStream 的實例。
2. 使用它的 writable 端口來寫入文本數據。
3. 從 readable 端口讀取編碼後的二進制數據。

### 基本語法
```javascript
const encoderStream = new TextEncoderStream();
const writer = encoderStream.writable.getWriter();

// 寫入文本數據
writer.write("Hello, World!");

// 完成寫入
writer.close();

// 讀取編碼後的二進制數據
const reader = encoderStream.readable.getReader();
reader.read().then(({ done, value }) => {
    if (!done) {
        console.log(value); // Uint8Array 格式的二進制數據
    }
});
```

## 示例
以下是使用 TextEncoderStream 的基本示例：

### 示例 1：編碼簡單文本
```javascript
const encoderStream = new TextEncoderStream();
const writer = encoderStream.writable.getWriter();

writer.write("Cantonese Hello");
writer.close();

const reader = encoderStream.readable.getReader();
reader.read().then(({ done, value }) => {
    console.log(value); // 會輸出編碼後的 Uint8Array
});
```

### 示例 2：處理多行文本
```javascript
const encoderStream = new TextEncoderStream();
const writer = encoderStream.writable.getWriter();

const textLines = ["第一行", "第二行", "第三行"];
textLines.forEach(line => writer.write(line + "\n"));

writer.close();

const reader = encoderStream.readable.getReader();
reader.read().then(({ done, value }) => {
    console.log(value); // 會輸出編碼後的 Uint8Array
});
```

## 解釋
使用 TextEncoderStream 時，開發者應注意以下幾點：

- **流的關閉**：在完成所有寫入後，務必調用 `close()` 方法，以確保流的正確結束。
- **異步操作**：讀取和寫入都是異步的，請確保適當處理 Promise 和 `reader.read()` 的結果。
- **編碼格式**：TextEncoderStream 默認使用 UTF-8 編碼，若需其他編碼格式，則需使用其他方法或庫。

## 一行摘要
TextEncoderStream 是一個 JavaScript API，允許將文本數據流式編碼為二進制格式，簡化了文本處理和傳輸過程。