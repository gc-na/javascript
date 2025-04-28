<!--
Meta Description: # JavaScript 中的 location 物件詳解 ## 摘要 `location` 物件是 JavaScript 中的全局物件，提供了用於獲取和操作當前文檔的 URL 的屬性和方法。 ## 文檔 `location` 物件是 `window` 物件的一部分，允許開發者訪問當前頁面的 URL...
Meta Keywords: url, location, javascript, www, example
-->

# JavaScript 中的 location 物件詳解

## 摘要
`location` 物件是 JavaScript 中的全局物件，提供了用於獲取和操作當前文檔的 URL 的屬性和方法。

## 文檔
`location` 物件是 `window` 物件的一部分，允許開發者訪問當前頁面的 URL 各個組成部分。它的主要用途包括讀取當前 URL、重定向頁面以及改變頁面的 URL。

### 主要屬性
- **href**: 返回當前頁面的完整 URL。
- **protocol**: 返回當前 URL 的協議（例如，`http:` 或 `https:`）。
- **host**: 包含主機名和端口號（例如，`www.example.com:80`）。
- **hostname**: 返回主機名（例如，`www.example.com`）。
- **port**: 返回連接的端口號（例如，`80`）。
- **pathname**: 返回 URL 的路徑部分（例如，`/path/to/resource`）。
- **search**: 返回 URL 的查詢字符串部分（例如，`?id=123`）。
- **hash**: 返回 URL 的片段識別符（例如，`#section1`）。

### 主要方法
- **assign(url)**: 將當前頁面重定向到指定的 URL。
- **reload()**: 重新加載當前頁面。
- **replace(url)**: 將當前頁面替換為指定的 URL，並且不會在歷史記錄中保留當前頁面的記錄。

## 示例
```javascript
// 獲取當前頁面的完整 URL
console.log(location.href);

// 將頁面重定向到新的 URL
location.assign('https://www.example.com');

// 重新加載當前頁面
location.reload();

// 替換當前頁面的 URL
location.replace('https://www.example.com');
```

## 解釋
在使用 `location` 物件時，需要注意以下幾點：

1. **跨域問題**: 當你嘗試訪問某個不同來源的 `location` 物件時，瀏覽器會因為同源政策而拋出錯誤。
2. **歷史記錄**: 使用 `replace()` 方法可以避免在瀏覽器歷史記錄中留下當前頁面的記錄，這在處理登入或跳轉後的頁面時特別有用。
3. **重定向影響**: 使用 `assign()` 和 `reload()` 會使瀏覽器的歷史記錄增加一條記錄，而 `replace()` 則不會。

## 單句總結
`location` 物件是 JavaScript 中用於操作當前 URL 的強大工具，方便開發者進行頁面重定向和 URL 管理。