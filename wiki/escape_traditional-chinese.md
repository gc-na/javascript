<!--
Meta Description: # JavaScript 中的 escape 函數：用於編碼 URI 的關鍵工具 ## 摘要 `escape` 是 JavaScript 中的一個全域函數，用於對字符串進行編碼，將非 ASCII 字符轉換為百分比編碼格式。儘管它在某些情況下仍有用，但已不再推薦使用，取而代之的是 `encodeURI...
Meta Keywords: escape, javascript, const, ascii, encodeuricomponent
-->

# JavaScript 中的 escape 函數：用於編碼 URI 的關鍵工具

## 摘要
`escape` 是 JavaScript 中的一個全域函數，用於對字符串進行編碼，將非 ASCII 字符轉換為百分比編碼格式。儘管它在某些情況下仍有用，但已不再推薦使用，取而代之的是 `encodeURIComponent` 和 `encodeURI`。

## 文檔
### 目的
`escape` 函數主要用於將字符串中的非 ASCII 字符轉換為可以在 URL 中安全傳輸的格式。這有助於避免因特殊字符導致的 URL 錯誤。

### 使用方法
函數語法如下：
```javascript
escape(str)
```
- **參數**：`str` - 要編碼的字符串。
- **回傳值**：返回編碼後的字符串，所有非 ASCII 字符都將轉換為 `%xx` 格式。

### 詳細說明
`escape` 函數會將以下字符進行編碼：
- ASCII 字符以外的字符
- 特殊字符，如空格、問號、井號等

然而，這個函數並不會對所有的字符進行編碼，例如英文字母、數字和某些特殊字符（如 `! * ' ( )`）將保持不變。由於 `escape` 的某些行為可能導致不預期的結果，因此不建議在新的程式碼中使用。

## 範例
以下是 `escape` 函數的一些基本用法範例：

### 範例 1：基本字符串編碼
```javascript
const originalString = "Hello World!";
const encodedString = escape(originalString);
console.log(encodedString); // 輸出: "Hello%20World%21"
```

### 範例 2：包含中文字符的字符串
```javascript
const chineseString = "你好，世界！";
const encodedChineseString = escape(chineseString);
console.log(encodedChineseString); // 輸出: "%E4%BD%A0%E5%A5%BD%EF%BC%8C%E4%B8%96%E7%95%8C%EF%BC%81"
```

### 範例 3：URL 中的特殊字符
```javascript
const urlString = "https://example.com/?name=John Doe&age=30";
const encodedURL = escape(urlString);
console.log(encodedURL); // 輸出: "https%3A//example.com/%3Fname%3DJohn%20Doe%26age%3D30"
```

## 解釋
使用 `escape` 函數時，開發者需要注意以下幾點：
- **不推薦使用**：`escape` 函數在 ECMAScript 3 中被引入，但已被標記為過時。應使用 `encodeURIComponent` 或 `encodeURI` 來替代。
- **不完整的編碼**：`escape` 不會對所有字符進行編碼，某些字符仍會保持不變，這可能導致在某些情況下出現錯誤。
- **可能的安全風險**：使用過時的編碼方法可能導致安全漏洞或不必要的錯誤。

## 簡單總結
`escape` 函數用於編碼字符串，雖然有其用途，但不再建議使用，應使用更新的方法如 `encodeURIComponent` 和 `encodeURI`。