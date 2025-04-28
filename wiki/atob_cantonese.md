<!--
Meta Description: # JavaScript atob 函數：解碼 Base64 字串的完整指南 ## 概要 `atob` 是一個 JavaScript 函數，用於將 Base64 編碼的字串解碼為原始的二進位資料。 ## 文檔 ### 目的 `atob` 函數的主要目的是將 Base64 格式的字串轉換回原始的 AS...
Meta Keywords: base64, atob, javascript, ascii, let
-->

# JavaScript atob 函數：解碼 Base64 字串的完整指南

## 概要
`atob` 是一個 JavaScript 函數，用於將 Base64 編碼的字串解碼為原始的二進位資料。

## 文檔
### 目的
`atob` 函數的主要目的是將 Base64 格式的字串轉換回原始的 ASCII 字串。這在處理網絡請求或數據傳輸時非常有用，因為 Base64 編碼能夠安全地傳遞二進位資料。

### 用法
`atob(encodedString)`：此函數接受一個參數 `encodedString`，該參數必須是有效的 Base64 編碼的字串。

### 詳細說明
- **參數**：
  - `encodedString`：要解碼的 Base64 字串。該字串必須符合 Base64 編碼的標準，否則會拋出異常。
  
- **返回值**：
  - 返回解碼後的 ASCII 字串。
  
- **例外情況**：
  - 如果輸入的字串不是有效的 Base64 編碼，`atob` 會拋出 `DOMException`。

## 示例
### 基本用法
```javascript
// 將 Base64 字串解碼
let base64String = "SGVsbG8gd29ybGQ="; // "Hello world"
let decodedString = atob(base64String);
console.log(decodedString); // 輸出: Hello world
```

### 錯誤處理
```javascript
try {
    let invalidBase64 = "InvalidBase64@";
    let result = atob(invalidBase64);
} catch (e) {
    console.error("解碼錯誤:", e);
}
```

## 解釋
- **常見陷阱**：
  - 確保提供的字串是有效的 Base64 編碼，否則會拋出異常。
  - 注意 `atob` 只適用於 ASCII 字符。如果需要解碼包含非 ASCII 字符的字串，建議先進行適當的處理，例如使用 `encodeURIComponent` 和 `decodeURIComponent`。

- **額外說明**：
  - `atob` 是一個全局函數，無需引入任何庫即可使用。
  - 在處理大數據或性能要求較高的應用時，考慮使用其他解碼方法以提高效能。

## 總結
`atob` 函數用於將 Base64 編碼的字串解碼為原始的 ASCII 字串，是 JavaScript 中處理數據解碼的重要工具。