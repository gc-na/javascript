<!--
Meta Description: # JavaScript 事件 (Event) – 完整指南 ## 簡介 JavaScript 的「事件」是一個極其重要的概念，允許開發者處理用戶互動、系統事件或其他類型的觸發行為。無論是點擊按鈕、提交表單還是滾動頁面，事件都是促使網頁反應的核心。 ## 文檔 ### 目的 在 JavaScript...
Meta Keywords: javascript, event, dom, addeventlistener, click
-->

# JavaScript 事件 (Event) – 完整指南

## 簡介
JavaScript 的「事件」是一個極其重要的概念，允許開發者處理用戶互動、系統事件或其他類型的觸發行為。無論是點擊按鈕、提交表單還是滾動頁面，事件都是促使網頁反應的核心。

## 文檔
### 目的
在 JavaScript 中，「事件」用於監聽和響應用戶或系統發生的特定行為。透過事件處理，開發者可以創建動態和互動的網頁應用程序。

### 用法
事件的使用通常涉及以下幾個步驟：
1. **選取元素**：使用 DOM 方法選取需要監聽事件的元素。
2. **添加事件監聽器**：使用 `addEventListener` 方法來綁定特定事件。
3. **處理事件**：定義事件處理函數，以響應事件的發生。

### 詳細說明
- **事件類型**：JavaScript 支持多種事件，包括但不限於：
  - 鼠標事件（例如 `click`, `dblclick`, `mouseover`）
  - 鍵盤事件（例如 `keydown`, `keyup`, `keypress`）
  - 表單事件（例如 `submit`, `change`, `focus`）
- **事件物件**：當事件發生時，會傳遞一個事件物件到事件處理函數，該物件包含有關事件的詳細信息，如事件類型、目標元素等。
- **移除事件監聽器**：可以使用 `removeEventListener` 方法來移除已添加的事件監聽器。

## 範例
### 基本用法
```javascript
// 選取按鈕元素
const button = document.getElementById('myButton');

// 添加點擊事件監聽器
button.addEventListener('click', function(event) {
    alert('按鈕被點擊了！');
});
```

### 表單提交事件
```javascript
// 選取表單元素
const form = document.getElementById('myForm');

// 添加提交事件監聽器
form.addEventListener('submit', function(event) {
    event.preventDefault(); // 防止默認提交
    alert('表單已提交！');
});
```

## 解釋
### 常見問題
- **事件冒泡與捕獲**：事件在 DOM 樹中會先通過捕獲階段，再經過目標元素進入冒泡階段。了解這一點可以幫助你更好地控制事件的處理。
- **多個事件監聽器**：可以為同一個元素添加多個事件監聽器，但要注意函數的執行順序。
- **性能考量**：過多的事件監聽器可能會影響性能，因此應適度使用。

### 注意事項
- 確保事件處理函數不會阻塞主線程，特別是在需要進行計算或操作 DOM 的情況下。
- 在移除事件監聽器時，必須使用與添加時完全相同的函數引用。

## 一句總結
JavaScript 事件是用於響應用戶和系統行為的核心機制，通過事件監聽器來實現互動。