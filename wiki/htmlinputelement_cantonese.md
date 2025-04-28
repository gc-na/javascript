<!--
Meta Description: # HTMLInputElement：JavaScript 中的表單輸入元素 ## 簡介 `HTMLInputElement` 是一種用於表示 HTML 表單中的輸入元素的接口，讓開發者可以通過 JavaScript 操作和控制用戶的輸入。 ## 文檔 `HTMLInputElement` 繼承自 ...
Meta Keywords: javascript, htmlinputelement, checkbox, html, value
-->

# HTMLInputElement：JavaScript 中的表單輸入元素

## 簡介
`HTMLInputElement` 是一種用於表示 HTML 表單中的輸入元素的接口，讓開發者可以通過 JavaScript 操作和控制用戶的輸入。

## 文檔
`HTMLInputElement` 繼承自 `HTMLElement`，代表 HTML 中的 `<input>` 標籤。這個元素可以用來收集用戶的輸入數據，並且支持多種類型，例如文本框、勾選框、單選按鈕等等。

### 目的
`HTMLInputElement` 的主要目的是提供一個統一的接口來訪問和操作輸入元素的屬性和方法，使開發者能夠創建動態和互動的用戶界面。

### 使用方法
要使用 `HTMLInputElement`，首先需要在 HTML 中定義一個 `<input>` 標籤，然後通過 JavaScript 來訪問和操作這些元素。

```html
<input type="text" id="myInput" value="Hello World">
```

在 JavaScript 中可以這樣訪問：

```javascript
const inputElement = document.getElementById("myInput");
```

### 屬性
`HTMLInputElement` 提供了多個屬性，例如：

- `value`：獲取或設置輸入框的當前值。
- `type`：獲取或設置輸入元素的類型（如 text、checkbox、radio 等）。
- `checked`：僅對類型為 checkbox 和 radio 有效，用於獲取或設置該元素是否被選中。

## 範例
以下是一些基本使用範例：

### 設置輸入值
```javascript
const inputElement = document.getElementById("myInput");
inputElement.value = "新值"; // 設置新的值
```

### 獲取輸入值
```javascript
const inputValue = inputElement.value; // 獲取當前值
console.log(inputValue);
```

### 檢查是否被選中
```javascript
const checkbox = document.getElementById("myCheckbox");
if (checkbox.checked) {
    console.log("Checkbox is checked");
} else {
    console.log("Checkbox is not checked");
}
```

## 解釋
使用 `HTMLInputElement` 時，有一些常見的注意事項：

- 確保在 DOM 加載完成後再訪問輸入元素，否則可能會導致 `null` 錯誤。
- 不同類型的輸入元素有不同的屬性，使用時需根據具體類型進行檢查。
- 使用 `addEventListener` 可以監聽輸入的變化，從而實現實時更新。

## 總結
`HTMLInputElement` 是一個強大的 JavaScript 接口，讓開發者能夠輕鬆地控制和操作 HTML 表單中的輸入元素。