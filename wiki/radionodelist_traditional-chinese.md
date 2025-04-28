<!--
Meta Description: # RadioNodeList：JavaScript 中的單選按鈕集合 ## 摘要 RadioNodeList 是一個在 JavaScript 中用於表示一組單選按鈕的物件，提供了對這些按鈕的方便訪問和操作。 ## 文檔 ### 目的 RadioNodeList 是由 HTML 表單中的 `<inp...
Meta Keywords: radionodelist, radio, javascript, radios, input
-->

# RadioNodeList：JavaScript 中的單選按鈕集合

## 摘要
RadioNodeList 是一個在 JavaScript 中用於表示一組單選按鈕的物件，提供了對這些按鈕的方便訪問和操作。

## 文檔
### 目的
RadioNodeList 是由 HTML 表單中的 `<input type="radio">` 元素組成的集合。它通常通過 `document.forms` 屬性或者使用 `querySelectorAll` 方法來獲取。這使得開發者可以方便地操作和管理單選按鈕的狀態。

### 使用
要獲取 RadioNodeList，通常可以使用以下方法：

```javascript
let radios = document.querySelectorAll('input[type="radio"]');
```

這樣，`radios` 變數將包含所有匹配的單選按鈕。RadioNodeList 類似於陣列，但並不完全是陣列，因此在某些情況下需要轉換。

### 詳細信息
- **屬性**：RadioNodeList 的 `length` 屬性返回集合中元素的數量。
- **方法**：可以使用迴圈來遍歷 RadioNodeList，例如使用 `forEach` 方法：

```javascript
radios.forEach(radio => {
    console.log(radio.value);
});
```

- **選擇和操作**：可以使用 `name` 屬性來獲取特定組的單選按鈕，這對於表單處理尤為重要。

## 範例
### 基本用法
下面是一個簡單的例子，展示如何使用 RadioNodeList：

```html
<form id="myForm">
    <input type="radio" name="color" value="red"> Red<br>
    <input type="radio" name="color" value="green"> Green<br>
    <input type="radio" name="color" value="blue"> Blue<br>
</form>

<script>
    let radios = document.getElementsByName('color');
    radios.forEach(radio => {
        radio.addEventListener('change', () => {
            console.log('Selected color:', radio.value);
        });
    });
</script>
```

在這個例子中，當用戶選擇不同顏色時，控制台將顯示所選的顏色。

## 解釋
### 常見問題與注意事項
- **非陣列特性**：雖然 RadioNodeList 看起來像陣列，但它不支持所有陣列方法，例如 `map`、`filter` 等。如果需要這些功能，請將其轉換為陣列：

```javascript
let radiosArray = Array.from(radios);
```

- **唯一選擇**：在同一 `name` 屬性的單選按鈕中，只有一個按鈕可以被選中，這是單選按鈕的基本特性。

- **DOM 更新**：如果單選按鈕被動態添加或刪除，RadioNodeList 的內容不會自動更新，需重新獲取。

## 一句總結
RadioNodeList 是 JavaScript 中用於操作一組單選按鈕的集合，方便開發者管理用戶的選擇。