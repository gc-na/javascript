<!--
Meta Description: # JavaScript 中的「self」：用法與特性 ## 概述 在 JavaScript 中，「self」 是一個全局對象，通常用於指向當前的全局上下文。這個術語在 Web 環境中特別重要，因為它有助於在不同的上下文中引用全局對象，尤其是在使用 Web Workers 和 iframe 等情況下...
Meta Keywords: self, web, worker, javascript, workers
-->

# JavaScript 中的「self」：用法與特性

## 概述
在 JavaScript 中，「self」 是一個全局對象，通常用於指向當前的全局上下文。這個術語在 Web 環境中特別重要，因為它有助於在不同的上下文中引用全局對象，尤其是在使用 Web Workers 和 iframe 等情況下。

## 文件說明
「self」 代表當前的全局對象。在瀏覽器環境中，它等同於「window」對象，而在 Web Worker 中，則是 Worker 的全局上下文。這使得「self」 成為一個理想的選擇，因為它不會受到執行上下文的影響，並且可以確保始終正確地引用全局對象。

### 用法
- 在瀏覽器中，使用「self」可以方便地訪問全局範圍的變數和函數。
- 在 Web Workers 中，則可以使用「self」來訪問 Worker 的全局範圍。

### 詳細說明
「self」 是一個全局變量，無需進行任何特殊的聲明或初始化。它可以用來替代「window」或「globalThis」，特別是在需要獲取當前上下文的情況下。由於其在不同上下文中的一致性，開發者可以使用「self」來編寫更具可移植性的代碼。

## 範例
### 基本用法
```javascript
// 在瀏覽器中
console.log(self === window); // 顯示 true

// 在 Web Worker 中
self.onmessage = function(event) {
    console.log('Received message:', event.data);
};
```

## 解釋
使用「self」時，開發者應注意以下幾點：
- 在瀏覽器中，「self」和「window」是相同的，因此用於全局作用域的時候，可以互換使用。
- 在使用 Web Workers 時，「self」提供了對 Worker 內部的唯一參考，這在處理多線程時特別重要。
- 在某些情況下，使用「self」可以避免命名衝突，特別是在嵌套作用域中。

## 一句總結
「self」 是 JavaScript 中的一個全局對象，用於引用當前上下文的全局範圍，特別是在瀏覽器和 Web Workers 中。