<!--
Meta Description: # JavaScript 的 onselectionchange 事件詳解 ## 簡介 `onselectionchange` 是一個與選擇變更相關的事件，主要用於監聽用戶在文檔或應用程序中的文本選擇變化。這個事件通常與用戶互動相結合，能夠在內容被選擇或取消選擇時觸發。 ## 文檔 ### 目的 `...
Meta Keywords: onselectionchange, document, selection, javascript, function
-->

# JavaScript 的 onselectionchange 事件詳解

## 簡介
`onselectionchange` 是一個與選擇變更相關的事件，主要用於監聽用戶在文檔或應用程序中的文本選擇變化。這個事件通常與用戶互動相結合，能夠在內容被選擇或取消選擇時觸發。

## 文檔
### 目的
`onselectionchange` 事件的主要目的是讓開發者能夠監聽文本選擇的變化，從而執行相應的操作，比如更新 UI、顯示工具欄或進行資料處理。

### 使用方式
要使用 `onselectionchange` 事件，開發者可以將其綁定到 `document` 物件上，並定義一個回調函數來處理事件。以下是基本的使用方式：

```javascript
document.onselectionchange = function() {
    // 處理選擇變化的邏輯
};
```

### 詳細說明
- **事件類型**: `onselectionchange` 是一個自定義事件，並不在所有瀏覽器中都有原生支持。
- **觸發時機**: 該事件在用戶選擇某段文本或取消選擇時會被觸發，這樣開發者可以根據用戶的互動即時更新界面。
- **性能考量**: 由於這個事件可能會頻繁觸發，因此在事件處理函數內應避免執行耗時的操作，建議使用防抖或節流技術來優化性能。

## 範例
### 基本使用範例
以下是 `onselectionchange` 的一個簡單示範，當用戶選擇文本時，會在控制台輸出所選文本的內容。

```javascript
document.onselectionchange = function() {
    const selection = document.getSelection().toString();
    if (selection) {
        console.log("選擇的文本:", selection);
    }
};
```

### 更新 UI 範例
如果需要根據選擇的文本更新 UI，可以這樣做：

```javascript
const output = document.getElementById('output');

document.onselectionchange = function() {
    const selection = document.getSelection().toString();
    output.textContent = selection ? `您選擇的文本是: ${selection}` : '';
};
```

## 解釋
### 常見陷阱
- **瀏覽器兼容性**: 目前 `onselectionchange` 事件的支持並不一致，某些舊版瀏覽器可能不支持這個事件。因此，如果需要在多種瀏覽器上運行，建議查閱相關文檔以確保兼容性。
- **性能問題**: 此事件可能在用戶快速選擇文本時頻繁觸發，因此必須謹慎處理事件，以避免性能下降。

## 總結
`onselectionchange` 是一個強大的事件，能夠讓開發者即時響應用戶的文本選擇行為，是增強用戶互動的重要工具。