<!--
Meta Description: # HTMLFormControlsCollection 在 JavaScript 中的應用 ## 概要 `HTMLFormControlsCollection` 是一個用於表示一組 HTML 表單控制項的集合，常用於操作和管理表單中的輸入元素，如文本框、選擇框和按鈕等。 ## 文檔 `HTMLFo...
Meta Keywords: htmlformcontrolscollection, let, form, javascript, elements
-->

# HTMLFormControlsCollection 在 JavaScript 中的應用

## 概要
`HTMLFormControlsCollection` 是一個用於表示一組 HTML 表單控制項的集合，常用於操作和管理表單中的輸入元素，如文本框、選擇框和按鈕等。

## 文檔
`HTMLFormControlsCollection` 是一個類似數組的集合，專門用於存放 HTML 表單中的所有控制項。它提供了一系列方法和屬性來訪問和操作這些控制項。

### 目的
`HTMLFormControlsCollection` 的主要目的是讓開發者能夠方便地操作表單內的控件，並且能夠透過 JavaScript 動態地讀取或修改控件的屬性和狀態。

### 用法
當你通過 JavaScript 獲取一個表單的控制項集合時，會返回一個 `HTMLFormControlsCollection` 對象。這可以透過以下方式實現：

```javascript
let form = document.getElementById('myForm');
let controls = form.elements; // 返回 HTMLFormControlsCollection
```

這個集合包含了表單中所有的控件，開發者可以使用索引或名稱來訪問特定的控件。

### 詳細說明
- **屬性**: `HTMLFormControlsCollection` 提供了多種屬性，如 `length`，用於獲取集合中控件的數量。
- **方法**: 儘管這個集合類似於數組，但它不具備所有數組的方法；你可以使用 `item(index)` 或 `namedItem(name)` 方法來獲取特定的控件。

## 範例
以下是一些基本的使用範例：

### 獲取所有控件
```javascript
let form = document.querySelector('form');
let controls = form.elements;

for (let i = 0; i < controls.length; i++) {
    console.log(controls[i].name); // 輸出每個控件的名稱
}
```

### 根據名稱訪問特定控件
```javascript
let form = document.getElementById('myForm');
let username = form.elements.namedItem('username'); // 獲取名稱為 'username' 的控件
console.log(username.value); // 輸出用戶名的值
```

## 解釋
在使用 `HTMLFormControlsCollection` 時，開發者應注意以下幾點：
- 控件的順序：控件在 `elements` 集合中的順序是根據它們在 HTML 中出現的順序。
- 控件的類型：不同類型的控件（如 `<input>`、`<select>` 等）可能會有不同的屬性和方法。
- 動態變化：如果在頁面中添加或刪除控件，`elements` 集合會自動更新。

## 總結
`HTMLFormControlsCollection` 是一個強大的工具，幫助開發者有效地管理和操作 HTML 表單中的控制項。