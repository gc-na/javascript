<!--
Meta Description: # JavaScript 的 onbeforeprint 事件：用於列印前的處理 ## 概要 `onbeforeprint` 是一個 JavaScript 事件，用於在用戶開始列印網頁之前觸發特定的行為或功能。這個事件讓開發者能夠在列印操作前調整頁面樣式或內容，以改善列印輸出的效果。 ## 文檔 #...
Meta Keywords: onbeforeprint, javascript, window, document, style
-->

# JavaScript 的 onbeforeprint 事件：用於列印前的處理

## 概要
`onbeforeprint` 是一個 JavaScript 事件，用於在用戶開始列印網頁之前觸發特定的行為或功能。這個事件讓開發者能夠在列印操作前調整頁面樣式或內容，以改善列印輸出的效果。

## 文檔
### 目的
`onbeforeprint` 事件的主要目的是在列印之前執行某些操作，例如隱藏不必要的元素、調整樣式或顯示額外訊息，來確保列印的內容更符合需求。

### 使用方法
`onbeforeprint` 事件可以通過 JavaScript 的事件監聽器來設置。通常，這個事件會與 `window` 物件一起使用。當用戶選擇列印時，此事件會被觸發，並執行相應的回調函數。

#### 語法範例：
```javascript
window.onbeforeprint = function() {
    // 在這裡執行列印前的操作
};
```

### 詳細說明
- **事件觸發**：當用戶選擇列印（例如按下 Ctrl + P 或選擇列印選項）時，`onbeforeprint` 事件會被觸發。
- **事件回調**：開發者可以定義一個函數，該函數會在事件觸發時執行。這個函數可以進行任何必要的 DOM 操作或樣式變更。
- **與 onafterprint 的搭配**：開發者通常會同時使用 `onbeforeprint` 和 `onafterprint` 事件，後者用於在列印完成後恢復頁面狀態。

## 範例
以下是 `onbeforeprint` 的基本使用範例：

```javascript
window.onbeforeprint = function() {
    document.getElementById("non-printable").style.display = "none";
    document.body.style.backgroundColor = "#fff";
};

window.onafterprint = function() {
    document.getElementById("non-printable").style.display = "block";
    document.body.style.backgroundColor = "";
};
```

在這個範例中，當用戶開始列印時，ID 為 `non-printable` 的元素會被隱藏，並且頁面的背景顏色將設置為白色。列印結束後，這些變更會被撤回。

## 解釋
### 常見問題
- **兼容性**：`onbeforeprint` 事件在大多數現代瀏覽器中都得到支持，但在某些舊版瀏覽器中可能無法正常運作。
- **性能考量**：在 `onbeforeprint` 中進行大量的 DOM 操作可能會導致性能問題，因此應謹慎使用。
- **CSS 媒體查詢**：結合 CSS 的媒體查詢（例如 `@media print`）可以更加靈活地控制列印樣式，而不僅僅依賴 JavaScript。

## 一句總結
`onbeforeprint` 事件允許開發者在列印之前進行頁面調整，以改善列印輸出效果。