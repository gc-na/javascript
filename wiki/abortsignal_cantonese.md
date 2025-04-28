<!--
Meta Description: # AbortSignal：JavaScript 中的中止信號 ## 簡介 AbortSignal 是一個用於控制異步操作中止的接口，通常與 Fetch API 和其他異步操作一起使用，幫助開發者管理請求的取消。 ## 文檔 ### 目的 AbortSignal 主要用於提供一種方式，讓開發者可以在...
Meta Keywords: abortsignal, signal, abort, controller, data
-->

# AbortSignal：JavaScript 中的中止信號

## 簡介
AbortSignal 是一個用於控制異步操作中止的接口，通常與 Fetch API 和其他異步操作一起使用，幫助開發者管理請求的取消。

## 文檔
### 目的
AbortSignal 主要用於提供一種方式，讓開發者可以在需要時中止一個異步操作，例如網絡請求。這對於提升應用性能和用戶體驗至關重要，特別是在處理大量請求或用戶交互時。

### 使用方法
使用 AbortSignal 時，通常需要創建一個 AbortController 實例，然後通過該實例獲取 AbortSignal。當需要中止請求時，只需調用 AbortController 的 abort 方法。

### 詳細說明
- **AbortController**：創建 AbortSignal 的實例。
- **AbortSignal**：用於監聽中止事件的信號。
- **abort() 方法**：用來觸發中止操作。
- **onabort 事件**：當信號被中止時觸發的事件。

### 結構範例
```javascript
const controller = new AbortController();
const signal = controller.signal;

fetch('https://api.example.com/data', { signal })
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(err => {
    if (err.name === 'AbortError') {
      console.log('請求已被中止');
    } else {
      console.error('發生錯誤:', err);
    }
  });

// 中止請求
controller.abort();
```

## 範例
### 基本使用
在這個範例中，我們創建了一個 Fetch 請求，並在需要時中止它。

```javascript
const controller = new AbortController();
const signal = controller.signal;

signal.addEventListener('abort', () => {
  console.log('請求已中止');
});

// 發送請求
fetch('https://api.example.com/data', { signal })
  .then(response => response.json())
  .then(data => console.log(data));

// 在 1 秒後中止請求
setTimeout(() => {
  controller.abort();
}, 1000);
```

## 解釋
### 常見陷阱
- **未檢查中止狀態**：在發送請求後，必須檢查是否有中止請求的可能性，否則會導致不必要的錯誤。
- **多次中止**：中止操作只能執行一次，重複調用 `abort()` 不會有任何效果。
- **事件處理**：確保在正確的時機添加事件監聽器，以避免因中止而導致的未捕獲錯誤。

### 附加說明
AbortSignal 是現代 web 開發中一個重要的工具，特別是在需要管理大量並發請求時。正確使用它能夠顯著提升應用性能和用戶體驗。

## 一句總結
AbortSignal 是 JavaScript 中用於控制異步操作中止的接口，幫助開發者有效管理網絡請求。