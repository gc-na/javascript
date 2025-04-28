<!--
Meta Description: # JavaScript 的 btoa 函數：將字串編碼為 Base64 ## 簡介 `btoa` 是 JavaScript 中的一個內建函數，用於將字串進行 Base64 編碼。這種編碼格式常用於將二進制數據轉換為 ASCII 字符串，以便於傳輸和存儲。 ## 文件說明 `btoa` 函數的主要目...
Meta Keywords: btoa, ascii, javascript, base64, let
-->

# JavaScript 的 btoa 函數：將字串編碼為 Base64

## 簡介
`btoa` 是 JavaScript 中的一個內建函數，用於將字串進行 Base64 編碼。這種編碼格式常用於將二進制數據轉換為 ASCII 字符串，以便於傳輸和存儲。

## 文件說明
`btoa` 函數的主要目的是將一個字串轉換為 Base64 編碼的格式。此函數僅接受一個參數，即需要編碼的字串。需要注意的是，`btoa` 僅能處理 ASCII 字符，如果輸入包含非 ASCII 字符，將會導致錯誤。

### 語法
```javascript
btoa(string)
```

### 參數
- `string`: 需要編碼的字串，必須是 ASCII 字符。

### 返回值
返回經過 Base64 編碼的字串。

## 範例
### 基本用法
```javascript
let originalString = "Hello, World!";
let encodedString = btoa(originalString);
console.log(encodedString); // "SGVsbG8sIFdvcmxkIQ=="
```

### 編碼包含空格的字串
```javascript
let stringWithSpaces = "JavaScript 是一種強大的語言";
let encodedSpaces = btoa(stringWithSpaces);
console.log(encodedSpaces); // 可能會導致錯誤
```
> 注意：上述範例會產生錯誤，因為 `btoa` 不能處理非 ASCII 字符。

## 解釋
當使用 `btoa` 時，有幾個常見的陷阱需要注意：

1. **非 ASCII 字符**：`btoa` 僅支援 ASCII 字符。如果試圖編碼包含非 ASCII 字符的字串，例如中文、日文或其他語言的字符，將會引發 `InvalidCharacterError`。為了解決這個問題，可以先將字串轉換為 UTF-8 格式。
   
   示例：
   ```javascript
   function utf8ToB64(str) {
       return btoa(unescape(encodeURIComponent(str)));
   }
   console.log(utf8ToB64("JavaScript 是一種強大的語言")); // "SmF2YVN0cmlwdCDkuIrkuJrmnKzkuI3lm57lm7Tlm57lm7TnqI3nqI3n"
   ```

2. **長度限制**：某些環境中，`btoa` 可能對輸入字串的長度有限制，因此在處理非常大的字串時要特別小心。

3. **安全性問題**：在處理敏感數據時，僅使用 Base64 編碼並不安全，因為 Base64 只是編碼，而非加密。對於需要保護的數據，應考慮使用更安全的加密方法。

## 總結
`btoa` 函數是 JavaScript 中一個方便的工具，用於將 ASCII 字串編碼為 Base64 格式，但在使用時必須注意其對非 ASCII 字符的限制和潛在的安全性問題。