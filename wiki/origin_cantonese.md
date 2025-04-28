<!--
Meta Description: # JavaScript 中的 "origin"：了解來源（Origin） ## 概要 在 JavaScript 中，"origin" 是一個重要的概念，涉及到網頁的安全性和跨域請求。它定義了文檔的來源，包括協議、主機名和端口號，這對於瀏覽器的同源政策（Same-Origin Policy）至關重要...
Meta Keywords: origin, javascript, 包括協議, 主機名和端口號, window
-->

# JavaScript 中的 "origin"：了解來源（Origin）

## 概要
在 JavaScript 中，"origin" 是一個重要的概念，涉及到網頁的安全性和跨域請求。它定義了文檔的來源，包括協議、主機名和端口號，這對於瀏覽器的同源政策（Same-Origin Policy）至關重要。

## 文檔
### 目的
"origin" 用於確定資源的來源，主要是為了保護用戶的數據安全，防止跨站腳本攻擊（XSS）和其他安全問題。

### 用法
在 JavaScript 中，可以通過 `window.location.origin` 獲取當前文檔的來源。這個屬性返回一個字符串，包括協議、主機名和端口號（如果有的話）。

### 詳細說明
- **格式**：`origin` 的格式為 `protocol + '//' + hostname + (':' + port)`。
- **協議**：通常是 `http` 或 `https`。
- **主機名**：即網站的域名或 IP 地址。
- **端口號**：如果使用非標準端口（如 8080），則會顯示；如果使用標準端口（如 80 或 443），則不會顯示。

## 示例
```javascript
// 獲取當前文檔的來源
const currentOrigin = window.location.origin;
console.log(currentOrigin); // 例如：'https://www.example.com'
```

## 解釋
- **常見陷阱**：有時候，開發者可能會混淆 "origin" 和 "URL" 的概念。"origin" 只關注於協議、主機名和端口，而 "URL" 包含了完整的網址，包括路徑和查詢字符串。
- **安全注意事項**：在處理跨域請求時，確保對方的 "origin" 是可信的，以避免潛在的安全風險。

## 總結
"origin" 在 JavaScript 中是用來確定當前文檔的來源，對於網頁安全至關重要。