<!--
Meta Description: # JavaScript 的 TextEncoder：編碼字符串的強大工具 ## 概述 `TextEncoder` 是 JavaScript 中的一個內建物件，主要用來將字符串編碼為 `Uint8Array`，使其能夠以 UTF-8 格式進行處理。這對於處理網絡請求、文件上傳及數據存儲非常有用。 #...
Meta Keywords: textencoder, const, encoder, javascript, uint8array
-->

# JavaScript 的 TextEncoder：編碼字符串的強大工具

## 概述
`TextEncoder` 是 JavaScript 中的一個內建物件，主要用來將字符串編碼為 `Uint8Array`，使其能夠以 UTF-8 格式進行處理。這對於處理網絡請求、文件上傳及數據存儲非常有用。

## 文檔
`TextEncoder` 的主要目的是提供一種簡單的方式來將文本字符串轉換為字節數組（`Uint8Array`），通常用於數據傳輸或存儲。這個物件在 Web API 中普遍可用，並在多數現代瀏覽器中得到支持。

### 使用方法
要使用 `TextEncoder`，您可以按以下步驟進行：

1. 創建 `TextEncoder` 的實例。
2. 使用 `encode()` 方法將字符串轉換為 `Uint8Array`。

### 語法
```javascript
const encoder = new TextEncoder();
const byteArray = encoder.encode("您的字符串");
```

### 參數
- `input`：需要編碼的字符串。

### 返回值
- 返回一個 `Uint8Array`，包含編碼後的字節數據。

## 範例
以下是一些基本用法的範例：

### 範例 1：基本字符串編碼
```javascript
const encoder = new TextEncoder();
const byteArray = encoder.encode("Hello, 世界！");
console.log(byteArray); // 輸出：Uint8Array(13) [72, 101, 108, 108, 111, 44, 32, 228, 184, 150, 229, 155, 189]
```

### 範例 2：編碼空字符串
```javascript
const encoder = new TextEncoder();
const byteArray = encoder.encode("");
console.log(byteArray); // 輸出：Uint8Array(0) []
```

### 範例 3：處理不同編碼
```javascript
const encoder = new TextEncoder("utf-16"); // 注意：默認為 "utf-8"
const byteArray = encoder.encode("Hello");
console.log(byteArray); // 輸出：Uint8Array(10) [72, 0, 101, 0, 108, 0, 108, 0, 111, 0]
```

## 解釋
### 常見陷阱和注意事項
- **默認編碼**：`TextEncoder` 默認使用 UTF-8 編碼，若需要使用其他編碼格式，需在實例化時指定。
- **非字元數據**：`TextEncoder` 僅支持字符串輸入，傳入非字符串類型（例如數字或物件）會導致錯誤。
- **環境支持**：在某些舊版瀏覽器或環境中，`TextEncoder` 可能不被支持，需檢查兼容性。

## 一句總結
`TextEncoder` 是 JavaScript 中一個強大的工具，用於將字符串編碼為 UTF-8 格式的字節數組，便於數據的傳輸和存儲。