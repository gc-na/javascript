<!--
Meta Description: # HTMLBaseElement：JavaScript中的基本HTML元素 ## 概述 HTMLBaseElement是一個用於在HTML文檔中定義基本URL的元素。這個元素通常用於指定文檔中相對URL的基準，從而影響後續的鏈接和資源加載。 ## 文檔 HTMLBaseElement 是一個 HT...
Meta Keywords: url, base, html, htmlbaseelement, head
-->

# HTMLBaseElement：JavaScript中的基本HTML元素

## 概述
HTMLBaseElement是一個用於在HTML文檔中定義基本URL的元素。這個元素通常用於指定文檔中相對URL的基準，從而影響後續的鏈接和資源加載。

## 文檔
HTMLBaseElement 是一個 HTML 元素，主要用於設置文檔基礎 URL 的 `<base>` 標籤。當文檔中包含相對 URL 時，這些 URL 將根據 `<base>` 標籤所指定的 URL 解析。這在多頁應用程序和相對路徑的資源加載中非常有用。

### 用法
`<base>` 標籤通常放置在 `<head>` 部分，且其屬性包括：
- `href`：指定基礎 URL，所有相對 URL 將基於此 URL 解析。
- `target`：指定新文檔打開的方式（例如，在新窗口中打開）。

### 詳細信息
HTMLBaseElement 是一個 HTML 元素的接口，可以通過 JavaScript 來訪問和操作。這使得開發者能夠在運行時動態改變基準 URL。以下是一些重要屬性和方法：
- `href`：返回或設置當前基本 URL。
- `target`：返回或設置當前的目標屬性。

## 示例
以下是使用 `<base>` 標籤的基本示例：

```html
<!DOCTYPE html>
<html>
<head>
    <base href="https://www.example.com/" target="_blank">
    <title>範例頁面</title>
</head>
<body>
    <a href="page.html">前往新頁面</a>
    <img src="images/photo.jpg" alt="範例圖片">
</body>
</html>
```

在上面的範例中，`<base>` 標籤設置了基礎 URL 為 `https://www.example.com/`，因此 `<a>` 和 `<img>` 的相對路徑將從此 URL 開始解析。

## 解釋
在使用 HTMLBaseElement 時，開發者應注意幾個常見的陷阱：
- 如果未設置 `<base>` 標籤，所有相對 URL 將默認基於文檔的當前 URL。
- `<base>` 標籤只能在 `<head>` 部分出現，放置在 `<body>` 內將無效。
- 使用 `<base>` 標籤時，需考慮到對 SEO 的影響，因為不正確的設置可能導致搜索引擎錯誤索引頁面。

## 一句總結
HTMLBaseElement 是一個用於定義文檔基礎 URL 的 HTML 元素，對相對 URL 的解析至關重要。