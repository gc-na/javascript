<!--
Meta Description: # AbortController：JavaScript 中的請求管理器 ## 簡介 `AbortController` 是 JavaScript 的一個內建物件，主要用於管理和中止網絡請求。它在處理異步操作時特別有用，特別是當需要取消某些請求時，可以提高應用程序的性能和用戶體驗。 ## 文檔 ##...
Meta Keywords: abortcontroller, signal, then, response, javascript
-->

# AbortController：JavaScript 中的請求管理器

## 簡介
`AbortController` 是 JavaScript 的一個內建物件，主要用於管理和中止網絡請求。它在處理異步操作時特別有用，特別是當需要取消某些請求時，可以提高應用程序的性能和用戶體驗。

## 文檔
### 目的
`AbortController` 提供了一種簡單的方式來取消一個或多個網絡請求。這在處理長時間運行的請求時非常重要，可以避免不必要的請求執行。

### 使用方法
要使用 `AbortController`，您需要創建一個新的 `AbortController` 實例，然後將其 `signal` 屬性傳遞給需要控制的請求。當需要中止請求時，只需調用 `abort()` 方法。

#### 語法
```javascript
const controller = new AbortController();
const signal = controller.signal;

// 使用 Fetch API 進行請求
fetch(url, { signal })
  .then(response => {
    // 處理響應
  })
  .catch(err => {
    if (err.name === 'AbortError') {
      console.log('請求已被中止');
    } else {
      console.log('其他錯誤:', err);
    }
  });

// 中止請求
controller.abort();
```

## 範例
以下是使用 `AbortController` 的基本範例：

### 範例 1：基本請求
```javascript
const controller = new AbortController();
const signal = controller.signal;

fetch('https://jsonplaceholder.typicode.com/posts', { signal })
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(err => {
    if (err.name === 'AbortError') {
      console.log('請求已被中止');
    }
  });

// 中止請求
setTimeout(() => controller.abort(), 100); // 100 毫秒後中止請求
```

### 範例 2：多個請求
```javascript
const controller1 = new AbortController();
const controller2 = new AbortController();

fetch('https://jsonplaceholder.typicode.com/posts/1', { signal: controller1.signal })
  .then(response => response.json())
  .then(data => console.log('請求 1:', data));

fetch('https://jsonplaceholder.typicode.com/posts/2', { signal: controller2.signal })
  .then(response => response.json())
  .then(data => console.log('請求 2:', data));

// 中止請求 1
setTimeout(() => controller1.abort(), 50); // 50 毫秒後中止請求 1
```

## 解釋
使用 `AbortController` 時，有幾個常見的陷阱和注意事項：

1. **請求狀態**：當請求被中止時，會拋出一個 `AbortError`。這需要在 `catch` 塊中進行處理，以避免未捕獲的錯誤。
2. **多重請求**：每個請求應有自己的 `AbortController` 實例，否則中止一個請求可能會影響其他請求。
3. **信號傳遞**：確保在發送請求時正確傳遞 `signal` 屬性，否則無法控制請求的中止。

## 一句總結
`AbortController` 是 JavaScript 中用於控制和中止網絡請求的重要工具，可提高應用程序的性能和穩定性。