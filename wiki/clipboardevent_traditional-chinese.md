<!--
Meta Description: # ClipboardEvent：JavaScript 中的剪貼簿事件 ## 概述 `ClipboardEvent` 是一個用於處理剪貼簿操作的事件，主要用於捕捉用戶在剪貼簿上進行的操作，例如複製、剪切和粘貼。透過此事件，開發者可以實現更互動的網頁應用程式。 ## 文檔 `ClipboardEven...
Meta Keywords: event, clipboardevent, document, addeventlistener, function
-->

# ClipboardEvent：JavaScript 中的剪貼簿事件

## 概述
`ClipboardEvent` 是一個用於處理剪貼簿操作的事件，主要用於捕捉用戶在剪貼簿上進行的操作，例如複製、剪切和粘貼。透過此事件，開發者可以實現更互動的網頁應用程式。

## 文檔
`ClipboardEvent` 是一種事件對象，當使用者在文檔中進行剪貼簿操作時（例如，按下 Ctrl+C 或 Ctrl+V 鍵），會觸發此事件。此事件特別適用於需要自定義剪貼簿行為的應用程式，並能夠提供操作的內容。

### 事件屬性
- `clipboardData`：此屬性返回一個 `DataTransfer` 對象，包含剪貼簿中的資料。開發者可以使用這個對象來讀取或寫入剪貼簿的內容。
- `type`：事件的類型，例如 `"copy"`、`"cut"` 或 `"paste"`。

### 用法
要使用 `ClipboardEvent`，您需要在相關的 DOM 元素上添加事件監聽器。以下是常見的操作：

```javascript
document.addEventListener('copy', function(event) {
    // 自定義複製行為
});

document.addEventListener('cut', function(event) {
    // 自定義剪切行為
});

document.addEventListener('paste', function(event) {
    // 自定義粘貼行為
});
```

## 示例
以下是如何使用 `ClipboardEvent` 的基本範例：

### 示例 1：監聽複製事件
```javascript
document.addEventListener('copy', function(event) {
    const textToCopy = "這是要複製的文字";
    event.clipboardData.setData('text/plain', textToCopy);
    event.preventDefault(); // 防止默認行為
});
```

### 示例 2：監聽粘貼事件
```javascript
document.addEventListener('paste', function(event) {
    const pastedData = event.clipboardData.getData('text/plain');
    console.log('粘貼的資料:', pastedData);
});
```

## 說明
使用 `ClipboardEvent` 時，開發者應注意以下幾點：

- **安全性**：某些瀏覽器可能會限制剪貼簿的訪問，特別是在未經用戶交互的情況下。因此，確保事件監聽器是在用戶交互後觸發的。
- **跨瀏覽器差異**：不同瀏覽器對於剪貼簿事件的實現可能存在差異，尤其是在處理 MIME 類型和資料格式時。建議進行充分測試。
- **事件預設行為**：在攔截剪貼簿事件時，通常需要調用 `event.preventDefault()`，以防止瀏覽器執行默認的複製或粘貼行為。

## 一句話總結
`ClipboardEvent` 使開發者能夠自定義和處理用戶的剪貼簿操作，如複製、剪切和粘貼。