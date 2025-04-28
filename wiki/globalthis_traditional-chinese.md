<!--
Meta Description: # globalThis：JavaScript 中的全局對象 ## 摘要 `globalThis` 是 JavaScript 中一個重要的全局對象，提供了一種統一的方式來訪問全局範圍，無論是在瀏覽器環境還是 Node.js 環境中。 ## 文檔 `globalThis` 是 ECMAScript 2...
Meta Keywords: globalthis, javascript, console, log, global
-->

# globalThis：JavaScript 中的全局對象

## 摘要
`globalThis` 是 JavaScript 中一個重要的全局對象，提供了一種統一的方式來訪問全局範圍，無論是在瀏覽器環境還是 Node.js 環境中。

## 文檔
`globalThis` 是 ECMAScript 2020 (ES11) 中引入的標準，旨在解決不同執行環境中全局對象的訪問問題。在瀏覽器中，`globalThis` 指向 `window` 對象，而在 Node.js 環境中則指向 `global` 對象。這使得開發者可以使用統一的方式來訪問全局對象，而不需要考慮當前的執行環境。

### 用途
- 提供一種訪問全局對象的統一方法。
- 使跨環境的代碼更具可移植性。

### 使用方法
使用 `globalThis` 時，開發者可以直接調用它來訪問全局範圍中的變量和函數。例如：

```javascript
globalThis.myGlobalVar = "Hello, World!";
console.log(globalThis.myGlobalVar); // 輸出：Hello, World!
```

## 範例
### 基本用法
以下是 `globalThis` 的一些基本使用範例：

1. 設置和訪問全局變量：
    ```javascript
    globalThis.myGlobalVar = "Hello, World!";
    console.log(globalThis.myGlobalVar); // 輸出：Hello, World!
    ```

2. 定義全局函數：
    ```javascript
    globalThis.myGlobalFunction = function() {
        return "This is a global function!";
    };
    console.log(globalThis.myGlobalFunction()); // 輸出：This is a global function!
    ```

3. 在不同環境中的使用：
    ```javascript
    // 在瀏覽器中
    console.log(globalThis === window); // 輸出：true
    
    // 在 Node.js 中
    console.log(globalThis === global); // 輸出：true
    ```

## 解釋
### 常見的陷阱和注意事項
- 在某些舊版本的 JavaScript 環境中，`globalThis` 可能不被支持，因此需要使用轉譯器（如 Babel）進行轉譯。
- 過度依賴全局變量可能導致命名衝突，建議盡量使用局部變量或模塊來封裝代碼。
- 使用 `globalThis` 設置的全局變量在全局範圍內可見，可能會影響其他代碼的執行。

## 一句總結
`globalThis` 提供了一個統一的方式來訪問 JavaScript 中的全局對象，使代碼在不同執行環境中更具可移植性。