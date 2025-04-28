<!--
Meta Description: # HTMLInputElement：JavaScript 中的 HTML 輸入元素 ## 概述 `HTMLInputElement` 是一種代表 `<input>` 元素的 JavaScript 物件，允許開發者透過 JavaScript 操作和控制用戶輸入的資料。這個物件提供了多種屬性和方法，幫...
Meta Keywords: javascript, inputelement, htmlinputelement, const, document
-->

# HTMLInputElement：JavaScript 中的 HTML 輸入元素

## 概述
`HTMLInputElement` 是一種代表 `<input>` 元素的 JavaScript 物件，允許開發者透過 JavaScript 操作和控制用戶輸入的資料。這個物件提供了多種屬性和方法，幫助開發者操作表單輸入並處理用戶交互。

## 文檔
`HTMLInputElement` 屬於 DOM（文件物件模型）的一部分，通過 JavaScript 可以輕鬆地訪問和操作。它的主要目的是提供用戶與網頁之間的交互，並收集輸入的數據。開發者可以使用這個物件的屬性來獲取或設置用戶輸入的值、驗證輸入的格式以及控制輸入的外觀。

### 主要屬性
- `value`：獲取或設置輸入框的值。
- `type`：獲取或設置輸入框的類型，例如 'text', 'password', 'checkbox' 等。
- `checked`：對於選擇框或單選框，獲取或設置其選中狀態。
- `disabled`：獲取或設置輸入框是否禁用。
- `placeholder`：獲取或設置輸入框的佔位符文本。

### 主要方法
- `focus()`：將焦點設置到輸入框上。
- `select()`：選擇輸入框中的文本。
- `setCustomValidity()`：設置自定義的有效性訊息。

## 例子
以下是一些基本的使用範例：

### 獲取輸入值
```javascript
const inputElement = document.getElementById('myInput');
const inputValue = inputElement.value;
console.log(inputValue);
```

### 設置輸入值
```javascript
const inputElement = document.getElementById('myInput');
inputElement.value = '新的值';
```

### 禁用輸入框
```javascript
const inputElement = document.getElementById('myInput');
inputElement.disabled = true;
```

### 選擇文本
```javascript
const inputElement = document.getElementById('myInput');
inputElement.focus();
inputElement.select();
```

## 解釋
在使用 `HTMLInputElement` 時，開發者需注意以下幾點：
- 不同類型的輸入框（例如，文本框、單選框、復選框）具有不同的屬性。確保使用正確的屬性來獲取或設置值。
- 如果在輸入框中使用 `setCustomValidity()` 方法，必須在表單提交之前調用此方法，以便進行有效性檢查。
- 使用 `focus()` 和 `select()` 方法時，確保這些方法的調用是在用戶互動之後，否則可能不會如預期生效。

## 總結
`HTMLInputElement` 是 JavaScript 中操作 HTML 輸入元素的關鍵物件，提供了多種屬性和方法以實現用戶輸入的有效控制和處理。