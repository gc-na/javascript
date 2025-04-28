<!--
Meta Description: # JavaScript 中的 Frames：深入探討與應用 ## 簡介 在網頁開發中，"frames" 是一個重要的概念，通常用於將多個 HTML 文件同時顯示在單一網頁中。雖然這種技術在現代網頁設計中不再廣泛使用，但了解其運作仍然對於學習 JavaScript 和網頁結構是有幫助的。 ## 文檔...
Meta Keywords: html, frames, frameset, frame, javascript
-->

# JavaScript 中的 Frames：深入探討與應用

## 簡介
在網頁開發中，"frames" 是一個重要的概念，通常用於將多個 HTML 文件同時顯示在單一網頁中。雖然這種技術在現代網頁設計中不再廣泛使用，但了解其運作仍然對於學習 JavaScript 和網頁結構是有幫助的。

## 文檔
### 目的
Frames 主要用於在同一窗口中顯示多個網頁內容。這一技術最早的用途是為了創建多層結構的網站，讓用戶能夠在不重新載入整個頁面的情況下查看不同的內容。

### 使用方式
在 HTML 中，frames 通常使用 `<frameset>` 和 `<frame>` 標籤定義。以下是基本的語法：

```html
<frameset cols="50%,50%">
    <frame src="page1.html" name="frame1">
    <frame src="page2.html" name="frame2">
</frameset>
```
這段代碼將顯示兩個並排的 frames，分別加載 `page1.html` 和 `page2.html`。

### 詳細說明
- **Frameset**: 用於定義 frames 的容器，取代了 `<body>` 標籤。這種方式不再被 HTML5 支持。
- **Frame**: 定義一個獨立的網頁區域，並指定其來源 URL。
- **name**: 為 frame 指定一個名稱，以便在 JavaScript 中進行操作和引用。

## 範例
以下是一個簡單的 frameset 示例：

```html
<!DOCTYPE html>
<html>
<head>
    <title>Frames Example</title>
</head>
<frameset rows="50%,50%">
    <frame src="header.html" name="headerFrame">
    <frame src="content.html" name="contentFrame">
</frameset>
</html>
```

在這個示例中，頁面被分為上下兩個部分，分別加載了 `header.html` 和 `content.html`。

## 解釋
### 常見問題
- **SEO 影響**: 使用 frames 可能會對網站的 SEO 造成負面影響，因為搜索引擎可能無法正確索引 frames 中的內容。
- **用戶體驗**: Frames 可能會使瀏覽器的導航變得複雜，因為它們不會更新地址欄的 URL。
- **瀏覽器兼容性**: 現在的許多瀏覽器對 frames 的支持越來越弱，這使得它們在現代網頁設計中不再理想。

### 注意事項
隨著 HTML5 的普及，框架技術已經逐漸被 CSS 和 JavaScript 的佈局方式所取代，如 Flexbox 和 Grid。對於新項目，建議使用這些現代技術來實現相似的功能。

## 一句總結
JavaScript 中的 frames 是一種過時的技術，用於在單一頁面中顯示多個網頁，但在現代網頁開發中已不再推薦使用。