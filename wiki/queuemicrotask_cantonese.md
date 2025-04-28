<!--
Meta Description: # JavaScript 嘅 queueMicrotask：非阻塞微任務處理 ## 概述 `queueMicrotask` 係一個 JavaScript 方法，佢用嚟將微任務排入事件循環嘅微任務隊列中，確保佢哋可以喺當前任務完成後、下一個事件循環開始之前執行。呢個方法對處理異步操作特別有用。 ## ...
Meta Keywords: queuemicrotask, promise, javascript, console, log
-->

# JavaScript 嘅 queueMicrotask：非阻塞微任務處理

## 概述
`queueMicrotask` 係一個 JavaScript 方法，佢用嚟將微任務排入事件循環嘅微任務隊列中，確保佢哋可以喺當前任務完成後、下一個事件循環開始之前執行。呢個方法對處理異步操作特別有用。

## 文檔
### 目的
`queueMicrotask` 提供咗一個非阻塞嘅方式，讓開發者可以安排微任務，確保佢哋喺執行其他代碼之後立即執行。微任務通常用嚟處理 Promise 的回調函數，或者其他需要快速執行但唔想阻塞主執行線嘅任務。

### 用法
```javascript
queueMicrotask(callback);
```
- **callback**：一個函數，當前任務完成後會被調用。

### 詳細說明
- 微任務會喺當前任務結束後立即執行，且會先於事件循環中嘅任何其他任務執行。
- `queueMicrotask` 係 ECMAScript 2015（ES6）嘅一部分，並且喺大多數現代瀏覽器都得到支持。
- 使用 `queueMicrotask` 可以避免使用 `setTimeout` 等方法造成嘅額外延遲，因為 `setTimeout` 會將任務放入宏任務隊列中，可能會影響性能。

## 範例
### 基本用法
```javascript
console.log('第一行');

queueMicrotask(() => {
    console.log('微任務執行');
});

console.log('第二行');
```
輸出：
```
第一行
第二行
微任務執行
```

### 處理 Promise 的回調
```javascript
const promise = new Promise((resolve) => {
    resolve('Promise 完成');
});

promise.then((result) => {
    queueMicrotask(() => {
        console.log(result);
    });
});

console.log('主執行線結束');
```
輸出：
```
主執行線結束
Promise 完成
```

## 解釋
### 常見陷阱
- **不支援老舊瀏覽器**：某些非常舊嘅瀏覽器可能唔支持 `queueMicrotask`，所以喺開發時要注意。
- **不會拋出異常**：如果 `callback` 函數內發生異常，佢唔會影響事件循環，但會導致未處理的 Promise 拋出異常，因此需要做好錯誤處理。
- **執行時序**：要注意 `queueMicrotask` 嘅執行時序，因為佢會在當前任務之後立即執行，但喺任何宏任務之前。

## 一句總結
`queueMicrotask` 係用於安排微任務執行嘅一個有效方法，確保非阻塞性嘅異步處理。