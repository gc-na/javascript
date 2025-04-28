<!--
Meta Description: # JavaScript 中的 "self" 關鍵字：概念與應用 ## 簡介 在 JavaScript 中，"self" 是一個常見的關鍵字，它通常用於表示當前的全局上下文或當前執行的環境。這個概念對於理解 JavaScript 的作用域和上下文變化至關重要。 ## 文檔 ### 目的 "self"...
Meta Keywords: self, javascript, worker, web, window
-->

# JavaScript 中的 "self" 關鍵字：概念與應用

## 簡介
在 JavaScript 中，"self" 是一個常見的關鍵字，它通常用於表示當前的全局上下文或當前執行的環境。這個概念對於理解 JavaScript 的作用域和上下文變化至關重要。

## 文檔
### 目的
"self" 在 JavaScript 中通常用於指代全局物件，特別是在 Web 瀏覽器環境中，它指向 `window` 物件。這使得開發者能夠在不同的上下文中獲取全局範圍的引用。

### 使用
在 JavaScript 的上下文中，"self" 作為全局物件的簡寫，能夠幫助開發者在函數或方法內部清晰地獲取全局變數。

### 詳細說明
- 在瀏覽器中，"self" 是 `window` 的別名，因此可以用來訪問全局變數和函數。
- 在 Web Worker 中，"self" 也用來指代當前的 Worker 環境。
  
```javascript
console.log(self === window); // true
```

這樣使用 "self" 的好處是，它能夠保持代碼的一致性，無論在何種上下文中都能正確引用全局物件。

## 範例
### 基本用法
```javascript
// 獲取全局變數
var globalVar = "Hello, World!";
console.log(self.globalVar); // 輸出: Hello, World!
```

### 在 Web Worker 中
```javascript
// worker.js
self.onmessage = function(event) {
    self.postMessage('Received: ' + event.data);
};
```

這裡的 `self` 用來處理來自主線程的消息，並回覆消息。

## 解釋
### 常見問題與注意事項
- **作用域問題**：在某些情況下，"self" 可能會引起混淆，特別是在函數內部使用時，開發者可能更偏好使用 `this`。因此，理解上下文是非常重要的。
- **跨環境**：在不同環境（如 Node.js 與瀏覽器）中，"self" 的行為可能不同。在 Node.js 中，並不存在 `self`，而是使用 `global` 來獲取全域作用域。

## 一句話總結
在 JavaScript 中，"self" 是全局物件的引用，提供了一種簡單的方式來訪問當前執行環境的全域變數和函數。