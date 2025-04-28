<!--
Meta Description: # 外部 (External) 在 JavaScript 中的應用與特性 ## 簡介 在 JavaScript 中，「外部」一詞通常指的是外部檔案或資源，特別是在引入 JavaScript 檔案時的相關概念。這種方式可以幫助開發者更好地組織代碼，增強網站的可維護性和性能。 ## 文檔 外部 Java...
Meta Keywords: javascript, html, script, src, body
-->

# 外部 (External) 在 JavaScript 中的應用與特性

## 簡介
在 JavaScript 中，「外部」一詞通常指的是外部檔案或資源，特別是在引入 JavaScript 檔案時的相關概念。這種方式可以幫助開發者更好地組織代碼，增強網站的可維護性和性能。

## 文檔
外部 JavaScript 檔案是以 `.js` 為副檔名的文檔，這些檔案包含 JavaScript 代碼，可以通過 HTML 文件中的 `<script>` 標籤進行引入。使用外部檔案的主要目的是將 JavaScript 代碼與 HTML 分離，這樣不僅可以提高代碼的可讀性，還可以促進代碼的重用。

### 使用方法
要在 HTML 文件中引入外部 JavaScript 檔案，可以使用以下語法：

```html
<script src="path/to/your/script.js"></script>
```

- `src` 屬性指定了 JavaScript 檔案的位置。
- 通常，建議將 `<script>` 標籤放在 HTML 文件的結尾，這樣可以確保在 DOM 完全加載後再執行 JavaScript 代碼。

## 範例
以下是一個基本的範例，展示如何在 HTML 中引入外部 JavaScript 檔案：

**index.html**
```html
<!DOCTYPE html>
<html lang="zh-HK">
<head>
    <meta charset="UTF-8">
    <title>外部 JavaScript 範例</title>
</head>
<body>
    <h1>歡迎來到我的網站</h1>
    <script src="script.js"></script>
</body>
</html>
```

**script.js**
```javascript
console.log("這是從外部檔案加載的 JavaScript!");
```

在加載此 HTML 文件時，控制台將顯示來自 `script.js` 的訊息。

## 解釋
使用外部 JavaScript 檔案有幾個常見的注意事項：

1. **檔案路徑**：確保 `src` 屬性中的路徑正確，否則瀏覽器將無法加載該檔案。
2. **加載順序**：將 `<script>` 標籤放在 `<body>` 的結尾可以避免 DOM 尚未加載完畢時 JavaScript 代碼執行的問題。
3. **緩存**：外部 JavaScript 檔案通常會被瀏覽器緩存，因此在開發過程中，可能需要清除瀏覽器緩存以查看代碼的更新結果。

## 簡單總結
在 JavaScript 中，「外部」指的是通過 `<script>` 標籤引入的外部 JavaScript 檔案，這有助於提高代碼的可維護性和性能。