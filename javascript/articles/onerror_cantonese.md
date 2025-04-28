<!--
Meta Description: # JavaScript 中的 onerror：錯誤處理的關鍵功能 ## 概述 `onerror` 是一個 JavaScript 事件處理器，用於捕捉和處理程序中的錯誤。這個功能對於開發者來說非常重要，因為它允許在運行時捕獲異常，並提供用戶友好的錯誤信息或進行相應的處理。 ## 文件說明 `oner...
Meta Keywords: onerror, javascript, console, log, function
-->

# JavaScript 中的 onerror：錯誤處理的關鍵功能

## 概述
`onerror` 是一個 JavaScript 事件處理器，用於捕捉和處理程序中的錯誤。這個功能對於開發者來說非常重要，因為它允許在運行時捕獲異常，並提供用戶友好的錯誤信息或進行相應的處理。

## 文件說明
`onerror` 事件可以應用於多個對象，例如 `window` 和 `img`。其主要目的是在 JavaScript 程序中捕獲未處理的錯誤，以便開發者能夠進行適當的錯誤處理。當錯誤發生時，`onerror` 會觸發，並傳遞錯誤的信息，這樣開發者可以根據需要進行調試或顯示替代內容。

### 用法
在使用 `onerror` 時，可以將其與對象綁定，並指定一個回調函數來處理錯誤。例如：

```javascript
window.onerror = function (message, source, lineno, colno, error) {
    console.log("錯誤信息:", message);
    console.log("錯誤來源:", source);
    console.log("行號:", lineno);
    console.log("列號:", colno);
    console.log("錯誤對象:", error);
};
```

## 示例
以下是一些 `onerror` 的基本用法示例：

### 示例 1：捕獲全局錯誤
```javascript
window.onerror = function (msg, url, lineNo, columnNo, error) {
    alert("捕獲到錯誤: " + msg);
};
```

### 示例 2：圖像加載錯誤
```javascript
const img = new Image();
img.src = "不存在的圖片.jpg";
img.onerror = function () {
    console.log("圖片加載失敗");
};
```

### 示例 3：自定義錯誤處理
```javascript
function myFunction() {
    throw new Error("自定義錯誤");
}

window.onerror = function (msg) {
    console.error("捕獲到自定義錯誤: " + msg);
};

myFunction(); // 這將觸發 onerror
```

## 解釋
使用 `onerror` 時，開發者需要注意以下幾點：

- **無法捕獲某些錯誤**：`onerror` 無法捕獲某些類型的錯誤，例如語法錯誤（SyntaxError）或在 `Promise` 中的錯誤。
- **多個處理器**：如果需要在同一事件上綁定多個處理器，必須使用其他事件機制（例如 `addEventListener`）。
- **性能影響**：過多的錯誤捕獲可能影響性能，因此應謹慎使用。

## 總結
`onerror` 是 JavaScript 中強大的錯誤處理工具，能夠幫助開發者有效捕獲和處理錯誤，從而提升用戶體驗。