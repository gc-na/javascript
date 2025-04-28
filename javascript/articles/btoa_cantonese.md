<!--
Meta Description: # JavaScript 中的 btoa 函數：將字串編碼為 Base64 ## 概述 `btoa` 是一個 JavaScript 函數，用於將字串轉換為 Base64 編碼。這種編碼方式常用於在網絡上安全傳輸數據，特別是在 HTTP 請求中。 ## 文檔 `btoa` 函數的主要目的在於將二進制資...
Meta Keywords: btoa, base64, ascii, javascript, let
-->

# JavaScript 中的 btoa 函數：將字串編碼為 Base64

## 概述
`btoa` 是一個 JavaScript 函數，用於將字串轉換為 Base64 編碼。這種編碼方式常用於在網絡上安全傳輸數據，特別是在 HTTP 請求中。

## 文檔
`btoa` 函數的主要目的在於將二進制資料轉換為 ASCII 字串，這樣可以方便地在網絡中傳輸。該函數接受一個字串作為參數，並返回相應的 Base64 編碼字串。

### 使用方法
```javascript
let encodedString = btoa(string);
```

- **參數**:
  - `string`：需要進行 Base64 編碼的字串，必須是有效的 ASCII 字符串。
  
- **返回值**:
  - 返回編碼後的 Base64 字串。

### 注意事項
- `btoa` 僅能處理有效的 ASCII 字符串，對於包含 Unicode 字符的字串，需要先進行轉換。
- 如果輸入字串包含非 ASCII 字符，將引發 `DOMException` 錯誤。

## 範例
### 基本用法
```javascript
let originalString = "Hello World!";
let encodedString = btoa(originalString);
console.log(encodedString); // SGVsbG8gV29ybGQh
```

### 對於包含 Unicode 字符的字串
在使用 `btoa` 處理包含非 ASCII 字符的字串時，應先轉換為 UTF-8 格式：
```javascript
function toBase64(str) {
    return btoa(unescape(encodeURIComponent(str)));
}

let unicodeString = "你好，世界！";
let encodedUnicode = toBase64(unicodeString);
console.log(encodedUnicode); // 5L2g5aSx5LqG5aSx
```

## 解釋
### 常見陷阱
1. **非 ASCII 字符**：如前所述，`btoa` 不支持非 ASCII 字符。使用時必須確保字串中不包含這類字元，否則會引發錯誤。
2. **字串長度限制**：雖然大多數瀏覽器支持長字串，但在某些情況下，過長的字串可能會導致性能問題或錯誤。

### 附加提示
- 當需要將 Base64 字串解碼回原始字串時，可以使用 `atob` 函數。
- Base64 編碼的用途包括將圖片編碼為字串以便嵌入 HTML 或用於 JSON 數據傳輸。

## 一句總結
`btoa` 是 JavaScript 中用於將 ASCII 字串編碼為 Base64 的簡單函數，適合在網絡傳輸中使用。