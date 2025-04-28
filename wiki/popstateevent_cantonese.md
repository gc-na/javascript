<!--
Meta Description: # PopStateEvent：JavaScript 中的歷史狀態事件 ## Synopsis PopStateEvent 是一個與瀏覽器歷史記錄管理相關的事件，當用戶通過瀏覽器的前進或後退按鈕導航時，會觸發此事件。它是單頁應用程式（SPA）中處理歷史狀態變化的重要工具。 ## Documentat...
Meta Keywords: event, history, page, state, popstateevent
-->

# PopStateEvent：JavaScript 中的歷史狀態事件

## Synopsis
PopStateEvent 是一個與瀏覽器歷史記錄管理相關的事件，當用戶通過瀏覽器的前進或後退按鈕導航時，會觸發此事件。它是單頁應用程式（SPA）中處理歷史狀態變化的重要工具。

## Documentation
### 目的
PopStateEvent 主要用於監聽瀏覽器歷史記錄的變化。當用戶通過前進或後退按鈕改變歷史狀態時，該事件會被觸發，並允許開發者相應地更新應用程式的狀態。

### 使用方法
要使用 PopStateEvent，開發者需要在 window 對象上添加一個事件監聽器。這可以通過以下方式實現：

```javascript
window.addEventListener('popstate', function(event) {
    // event.state 包含與當前狀態相關的數據
    console.log(event.state);
});
```

### 詳細資訊
- **event.state**：此屬性包含與當前歷史條目相關的狀態對象。當使用 `history.pushState()` 或 `history.replaceState()` 方法修改歷史狀態時，可以傳遞狀態對象。
- **觸發時機**：PopStateEvent 僅在用戶使用瀏覽器的前進或後退按鈕時觸發，不會在調用 `history.pushState()` 或 `history.replaceState()` 時觸發。

## Examples
### 基本用法
以下是如何使用 PopStateEvent 監聽歷史狀態改變的基本例子：

```javascript
// 假設有一個初始化狀態
history.pushState({ page: 1 }, "title 1", "?page=1");

window.addEventListener('popstate', function(event) {
    if (event.state) {
        console.log('當前狀態: ', event.state.page);
    } else {
        console.log('無狀態');
    }
});

// 用戶點擊瀏覽器的後退按鈕將觸發上述事件
```

### 多個狀態的示例
可以推送多個狀態到歷史記錄中：

```javascript
history.pushState({ page: 1 }, "title 1", "?page=1");
history.pushState({ page: 2 }, "title 2", "?page=2");
history.pushState({ page: 3 }, "title 3", "?page=3");

window.addEventListener('popstate', function(event) {
    if (event.state) {
        console.log('當前狀態: ', event.state.page);
    }
});
```

## Explanation
### 常見問題
- **PopStateEvent 何時觸發？** 
  只有在用戶使用前進或後退按鈕時才會觸發，但不會在使用 `history.pushState()` 或 `history.replaceState()` 時自動觸發。

- **event.state 可能是空的嗎？**
  是的，當歷史條目是初始狀態（即頁面加載時）時，`event.state` 會返回 `null`。

- **如何避免多次觸發？**
  確保在事件處理函數中進行狀態檢查，以避免重複執行不必要的操作。

## One Line Summary
PopStateEvent 是一個用於監聽瀏覽器歷史狀態變化的事件，對於單頁應用程式至關重要。