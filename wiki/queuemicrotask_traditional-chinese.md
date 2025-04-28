<!--
Meta Description: # queueMicrotask：JavaScript 的微任務佇列 ## 概要 `queueMicrotask` 是 JavaScript 中一個重要的 API，用於將一個函數排入微任務佇列，這樣它可以在當前事件循環的結束時執行。這個特性對於處理非同步操作非常有用，特別是當你需要確保某個任務在 D...
Meta Keywords: queuemicrotask, promise, javascript, console, log
-->

# queueMicrotask：JavaScript 的微任務佇列

## 概要
`queueMicrotask` 是 JavaScript 中一個重要的 API，用於將一個函數排入微任務佇列，這樣它可以在當前事件循環的結束時執行。這個特性對於處理非同步操作非常有用，特別是當你需要確保某個任務在 DOM 更新之前執行時。

## 文檔
### 目的
`queueMicrotask` 旨在提供一種簡單的方法來安排微任務，這樣可以在當前的運行上下文中完成所有的宏任務之後，立即執行這些微任務。微任務的執行優先於瀏覽器的重新繪製和其他宏任務。

### 語法
```javascript
queueMicrotask(callback);
```

### 參數
- `callback`: 一個函數，將在微任務佇列中執行。這個函數不接受任何參數。

### 使用方式
使用 `queueMicrotask` 可以確保特定的任務在當前上下文中完成後立即執行，這在處理 Promise、async/await 或其他非同步操作時特別有用。

## 範例
### 基本使用
```javascript
console.log('開始');

queueMicrotask(() => {
    console.log('微任務執行中');
});

console.log('結束');
```
#### 輸出：
```
開始
結束
微任務執行中
```

### 結合 Promise 使用
```javascript
Promise.resolve().then(() => {
    console.log('Promise 任務執行中');
});

queueMicrotask(() => {
    console.log('微任務執行中');
});
```
#### 輸出：
```
微任務執行中
Promise 任務執行中
```

## 解釋
### 常見陷阱與注意事項
1. **執行順序**：微任務的執行順序是在當前宏任務之後，但在任何瀏覽器繪製之前，這意味著如果你將大量微任務排入佇列，可能會導致性能問題。
2. **錯誤處理**：如果微任務內部發生錯誤，這可能會導致整個 Promise 鏈的失敗，請務必使用錯誤處理機制來捕獲這些錯誤。
3. **無法取消**：一旦微任務被排入佇列，就無法取消或移除，因此要謹慎使用。

## 一句總結
`queueMicrotask` 允許開發者將函數排入微任務佇列，以確保其在當前事件循環結束時優先執行。