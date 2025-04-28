<!--
Meta Description: # setInterval：JavaScript 定時器的使用指南 ## 概述 `setInterval` 是 JavaScript 中的一個全局函數，用於定時重複執行指定的函數或代碼塊。這個函數非常適合用於需要定期更新的應用程式，例如動畫效果、數據刷新等。 ## 文檔 ### 目的 `setInt...
Meta Keywords: setinterval, javascript, intervalid, console, log
-->

# setInterval：JavaScript 定時器的使用指南

## 概述
`setInterval` 是 JavaScript 中的一個全局函數，用於定時重複執行指定的函數或代碼塊。這個函數非常適合用於需要定期更新的應用程式，例如動畫效果、數據刷新等。

## 文檔
### 目的
`setInterval` 允許開發者設定一個時間間隔，並在每次間隔到達時執行特定的操作。這使得在網頁上創建定時任務變得更加簡單。

### 語法
```javascript
setInterval(function, milliseconds);
```

### 參數
- **function**：要執行的函數或代碼塊。
- **milliseconds**：兩次執行之間的時間間隔，以毫秒為單位。

### 返回值
`setInterval` 返回一個唯一的識別符，可用於清除該定時器。

### 清除定時器
要停止 `setInterval` 的執行，可以使用 `clearInterval()` 函數，傳入 `setInterval` 返回的識別符。

## 範例
### 基本使用
```javascript
// 每隔一秒打印一次 "Hello, World!"
const intervalId = setInterval(() => {
    console.log("Hello, World!");
}, 1000);

// 停止定時器
setTimeout(() => {
    clearInterval(intervalId);
    console.log("定時器已停止");
}, 5000);
```

### 使用具名函數
```javascript
function greet() {
    console.log("你好！");
}

const intervalId = setInterval(greet, 2000);

// 停止定時器
setTimeout(() => {
    clearInterval(intervalId);
    console.log("定時器已停止");
}, 10000);
```

## 解釋
在使用 `setInterval` 時，需要注意以下幾點：
- **精確度**：`setInterval` 的時間精確度受環境影響，實際執行的間隔可能比設置的時間長，特別是在繁重的計算或其他阻塞操作存在的情況下。
- **內存洩漏**：如果不清除定時器，可能導致內存洩漏，特別是在動態創建的應用中。
- **多重定時器**：如果不小心創建多個定時器，可能導致性能問題。始終檢查定時器是否已存在，或在創建新定時器之前清除現有定時器。

## 一句總結
`setInterval` 是 JavaScript 中用於定時重複執行函數的強大工具，適合用於各種需要時間控制的功能。