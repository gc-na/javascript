<!--
Meta Description: # JavaScript 中的 Frames：使用框架進行網頁布局 ## 概述 在 JavaScript 中，"frames" 是指一種網頁布局技術，通常用於將多個 HTML 頁面嵌入到同一個瀏覽器窗口中。雖然這項技術曾經十分流行，但隨著現代網頁設計的進步，使用框架的方式已經逐漸被更先進的技術所取代...
Meta Keywords: html, frameset, frame, src, javascript
-->

# JavaScript 中的 Frames：使用框架進行網頁布局

## 概述
在 JavaScript 中，"frames" 是指一種網頁布局技術，通常用於將多個 HTML 頁面嵌入到同一個瀏覽器窗口中。雖然這項技術曾經十分流行，但隨著現代網頁設計的進步，使用框架的方式已經逐漸被更先進的技術所取代。

## 文檔
### 目的
框架 (Frames) 使開發者能夠將多個文檔並排顯示，從而在一個瀏覽器窗口內同時展示不同內容。這在早期的網頁設計中非常流行，特別是用於導航和內容分隔。

### 使用
框架主要通過 `<frameset>` 和 `<frame>` 標籤來實現。這些標籤在 HTML 中定義了框架的結構和內容。儘管 HTML5 已經不再支持這些標籤，對於舊式網站仍然存在一定的參考價值。

```html
<frameset cols="50%,50%">
    <frame src="frame_a.html">
    <frame src="frame_b.html">
</frameset>
```

### 詳細說明
- **<frameset>**：用於定義框架的集合，可以指定行或列的數量。
- **<frame>**：用於定義每個框架的內容，通過 `src` 屬性指定要顯示的網頁。
- **<noframes>**：提供在不支持框架的瀏覽器中展示的替代內容。

雖然框架提供了便利的布局選擇，但它們的使用會影響 SEO 和可訪問性，因為搜尋引擎和輔助技術可能無法正確解析框架內的內容。

## 示例
### 基本用法
```html
<!DOCTYPE html>
<html>
<head>
    <title>框架示例</title>
</head>
<frameset rows="*,*">
    <frame src="header.html" name="headerFrame">
    <frame src="content.html" name="contentFrame">
</frameset>
<noframes>
    <body>
        你的瀏覽器不支持框架。
    </body>
</noframes>
</html>
```

在這個示例中，名為 `headerFrame` 和 `contentFrame` 的兩個框架被創建，以方便同時顯示頁眉和內容。

## 解釋
### 常見問題
1. **SEO 影響**：使用框架可能對網站的搜尋引擎排名造成負面影響，因為搜尋引擎無法完全索引框架內的內容。
2. **可訪問性問題**：對於依賴輔助技術的用戶，框架可能會造成困難，因為它們無法輕易理解框架的結構。
3. **不支持的問題**：隨著 HTML5 的普及，許多現代瀏覽器已經不再支持框架的使用。

### 附加說明
考慮使用 CSS Flexbox 或 Grid 來創建複雜的網頁布局，這些技術不僅更具靈活性，還更符合現代網頁設計的標準。

## 一句總結
JavaScript 中的框架技術允許同時顯示多個 HTML 文件，但隨著技術的進步，現已不再建議使用。