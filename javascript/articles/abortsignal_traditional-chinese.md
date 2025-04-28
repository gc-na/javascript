<!--
Meta Description: # AbortSignal：JavaScript 中的中止信號 ## 簡介 `AbortSignal` 是一個用於取消異步操作的信號對象，尤其在使用 `fetch` API 或其他長時間運行的操作時非常有用。它允許用戶在需要時中止請求，從而提高了應用程序的效率和控制能力。 ## 文檔 ### 目的 ...
Meta Keywords: abortsignal, signal, abortcontroller, controller, fetch
-->

# AbortSignal：JavaScript 中的中止信號

## 簡介
`AbortSignal` 是一個用於取消異步操作的信號對象，尤其在使用 `fetch` API 或其他長時間運行的操作時非常有用。它允許用戶在需要時中止請求，從而提高了應用程序的效率和控制能力。

## 文檔
### 目的
`AbortSignal` 主要用於與 `AbortController` 一起工作，提供一種標準化的方式來取消異步操作。當一個操作被中止時，`AbortSignal` 會觸發事件，讓開發者能夠做出相應的處理。

### 使用方式
1. **創建 AbortController**:
   每個 `AbortSignal` 都是由 `AbortController` 創建的，使用 `new AbortController()` 來實例化。

2. **獲取信號**:
   藉由 `controller.signal` 獲取 `AbortSignal`。

3. **將信號傳遞給異步操作**:
   當執行一個可以被中止的操作，比如 `fetch` 請求時，可以將信號作為選項傳遞。

4. **中止操作**:
   當需要中止操作時，調用 `controller.abort()`。

### 詳細說明
`AbortSignal` 具有以下特性：
- **事件監聽**：可以通過 `signal.addEventListener('abort', callback)` 註冊中止事件的回調函數。
- **檢查狀態**：可以使用 `signal.aborted` 屬性來檢查操作是否已經被中止。

## 範例
以下是 `AbortSignal` 的基本用法示例：

```javascript
// 創建 AbortController
const controller = new AbortController();
const signal = controller.signal;

// 發送 fetch 請求並傳遞信號
fetch('https://api.example.com/data', { signal })
  .then(response => {
    if (!response.ok) {
      throw new Error('Network response was not ok');
    }
    return response.json();
  })
  .then(data => console.log(data))
  .catch(err => {
    if (signal.aborted) {
      console.log('請求已被中止');
    } else {
      console.log('發生錯誤:', err);
    }
  });

// 在適當的時候中止請求
controller.abort();
```

## 解釋
### 常見陷阱與注意事項
- **信號未傳遞**：確保在執行異步操作時正確地傳遞 `AbortSignal`，否則無法中止操作。
- **多次中止**：調用 `abort()` 方法會觸發多次的中止事件，但僅有第一次有效，之後的中止不會有任何影響。
- **未處理的異常**：在中止請求後，應妥善處理可能產生的異常，以避免應用程序崩潰。

## 一句話總結
`AbortSignal` 是 JavaScript 中用於控制異步操作取消的信號對象，提升了開發者對請求的控制能力。