<!--
Meta Description: # TransitionEvent：JavaScript 中的過渡事件 ## 概要 TransitionEvent 是一種事件，當 CSS 過渡效果開始或結束時會被觸發。在 JavaScript 中，開發者可以使用 TransitionEvent 來監聽元素的過渡狀態，從而在動畫過程中執行特定的操作...
Meta Keywords: transitionevent, css, box, javascript, transitionend
-->

# TransitionEvent：JavaScript 中的過渡事件

## 概要
TransitionEvent 是一種事件，當 CSS 過渡效果開始或結束時會被觸發。在 JavaScript 中，開發者可以使用 TransitionEvent 來監聽元素的過渡狀態，從而在動畫過程中執行特定的操作。

## 文檔

### 目的
TransitionEvent 主要用於處理 CSS 過渡的開始和結束。在許多情況下，當元素的樣式發生變化時，開發者可能需要根據過渡的狀態來執行某些功能，比如顯示或隱藏元素、更新 UI 等。

### 使用方法
要使用 TransitionEvent，您需要在 DOM 元素上添加事件監聽器，然後根據需要處理事件。例如，您可以監聽 `transitionend` 事件，該事件會在過渡結束時被觸發。

### 詳細說明
TransitionEvent 事件包含以下屬性：
- `propertyName`：觸發過渡的 CSS 屬性名稱。
- `elapsedTime`：過渡持續的時間（以秒為單位）。
- `pseudoElement`：如果是使用偽元素進行的過渡，則返回該偽元素的名稱；否則返回空字串。

這些屬性使得開發者可以獲取與過渡相關的詳細信息。

## 示例

### 基本用法示例
```javascript
const box = document.querySelector('.box');

box.addEventListener('transitionend', (event) => {
    console.log(`過渡結束： ${event.propertyName}，持續時間： ${event.elapsedTime}秒`);
});

// 開始過渡效果
box.style.transition = 'width 2s';
box.style.width = '200px';
```

在這個示例中，當 `.box` 元素的寬度過渡結束時，控制台將輸出過渡的屬性名稱和持續時間。

## 解釋

### 常見陷阱
- **事件名稱拼寫錯誤**：確保使用 `transitionend` 而不是其他錯誤的事件名稱。
- **屬性名稱不正確**：在使用 `propertyName` 時，請確認您監聽的事件屬性名稱正確無誤。
- **CSS 屬性不支持過渡**：並非所有 CSS 屬性都支持過渡，請檢查所使用的屬性是否可以過渡。

### 附加說明
TransitionEvent 主要依賴於 CSS 的過渡屬性，因此在使用時需確保相關的 CSS 設置已正確配置。

## 一句總結
TransitionEvent 是用於監控 CSS 過渡狀態的事件，幫助開發者在動畫過程中執行特定邏輯。