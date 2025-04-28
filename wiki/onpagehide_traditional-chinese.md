<!--
Meta Description: # JavaScript 的 onpagehide 事件詳解 ## 概述 `onpagehide` 是一個與瀏覽器頁面狀態變化有關的事件，通常在使用者離開當前頁面時觸發。這個事件在單頁應用程式（SPA）中尤為重要，因為它允許開發者在頁面隱藏時進行清理或保存狀態。 ## 文件說明 ### 目的 `on...
Meta Keywords: onpagehide, event, javascript, window, function
-->

# JavaScript 的 onpagehide 事件詳解

## 概述
`onpagehide` 是一個與瀏覽器頁面狀態變化有關的事件，通常在使用者離開當前頁面時觸發。這個事件在單頁應用程式（SPA）中尤為重要，因為它允許開發者在頁面隱藏時進行清理或保存狀態。

## 文件說明
### 目的
`onpagehide` 事件的主要目的是在使用者離開頁面時提供一個機會來執行必要的操作，例如保存用戶的狀態或清理資源。這對於增強用戶體驗和應用性能來說是非常重要的。

### 使用方式
`onpagehide` 事件可以通過為 `window` 對象添加事件監聽器來使用。當頁面被隱藏時，該事件會被觸發，並且可以攜帶一些與頁面狀態相關的資訊。

#### 語法示例：
```javascript
window.onpagehide = function(event) {
    // 當前頁面被隱藏時執行的操作
    console.log('頁面正在隱藏', event);
};
```

## 範例
以下是使用 `onpagehide` 事件的基本範例：

### 範例 1：簡單的頁面隱藏事件
```javascript
window.onpagehide = function(event) {
    alert('您正在離開此頁面！');
};
```
這個範例在使用者試圖離開頁面時顯示一個提示框。

### 範例 2：保存用戶狀態
```javascript
let userData = { name: "John Doe", age: 30 };

window.onpagehide = function(event) {
    localStorage.setItem('userData', JSON.stringify(userData));
    console.log('用戶狀態已保存');
};
```
在這個範例中，當頁面被隱藏時，用戶的狀態會被保存到 `localStorage` 中。

## 解釋
### 常見問題
- **事件不觸發**：如果使用者快速切換頁面，`onpagehide` 事件可能不會被觸發。這是因為頁面隱藏的時間非常短。
- **事件回調中的 `event` 參數**：`event` 參數包含了關於頁面隱藏的詳細資訊，例如 `persisted` 屬性，指示頁面是否被緩存。
- **與 `onpageshow` 事件的配合**：`onpagehide` 通常與 `onpageshow` 一起使用，以便在頁面返回時恢復狀態。

### 附加說明
`onpagehide` 事件是 HTML5 中的一部分，通常在移動設備的瀏覽器中表現得更好。開發者應注意不同瀏覽器對於該事件的支持情況。

## 一行總結
`onpagehide` 是一個在使用者離開頁面時觸發的事件，允許開發者執行必要的狀態保存或清理操作。