<!--
Meta Description: # encodeURI：JavaScript 中的 URI 編碼函數 ## 概要 `encodeURI` 是一個 JavaScript 函數，用於將不符合 URI 格式的字符串編碼為有效的 URI。此函數在處理 URL 時特別有用，可以確保字符串中的特殊字符不會干擾 URL 的結構。 ## 文件說明...
Meta Keywords: encodeuri, uri, url, javascript, encodeuricomponent
-->

# encodeURI：JavaScript 中的 URI 編碼函數

## 概要
`encodeURI` 是一個 JavaScript 函數，用於將不符合 URI 格式的字符串編碼為有效的 URI。此函數在處理 URL 時特別有用，可以確保字符串中的特殊字符不會干擾 URL 的結構。

## 文件說明
`encodeURI` 函數的主要目的是將一個完整的 URI 編碼，使其可以安全地用於網絡傳輸。此函數會自動處理 URI 中的某些特殊字符，如空格、#、? 和 & 等，但不會編碼已經是有效的 URI 組成部分（例如冒號、斜杠等）。

### 語法
```javascript
encodeURI(uri)
```

### 參數
- **uri**: 需要編碼的字符串，通常是完整的 URL。

### 返回值
返回編碼後的 URI 字符串。

## 示例
以下是 `encodeURI` 的基本使用示例：

```javascript
let url = "https://www.example.com/search?q=你好&lang=zh";
let encodedUrl = encodeURI(url);
console.log(encodedUrl); // 輸出: "https://www.example.com/search?q=%E4%BD%A0%E5%A5%BD&lang=zh"
```

## 解釋
使用 `encodeURI` 時需注意以下幾點：

1. **不會編碼所有字符**: `encodeURI` 不會編碼某些特殊字符，如冒號、斜杠等。這意味著在編碼後，URL 的結構仍然保持有效。
2. **使用 encodeURIComponent**: 若需要編碼 URL 的某些部分（如查詢字符串參數），應使用 `encodeURIComponent` 函數。`encodeURIComponent` 會編碼所有字符，這在處理單一參數時特別有用。
3. **安全性**: 在將用戶輸入的數據添加到 URL 中之前，使用 `encodeURI` 可以降低 XSS 攻擊的風險。

## 一句總結
`encodeURI` 是一個用於將完整 URI 編碼為有效格式的 JavaScript 函數，確保在網絡傳輸時不會出現錯誤。