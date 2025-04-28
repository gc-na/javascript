<!--
Meta Description: # RadioNodeList 在 JavaScript 中的使用與特性 ## 概述 `RadioNodeList` 是一個特殊的對象類型，在 JavaScript 中用於表示一組與 HTML `<input>` 標籤類型為 `radio` 的元素相對應的節點。這個對象常見於處理表單中的單選按鈕。 ...
Meta Keywords: radionodelist, radio, gender, document, input
-->

# RadioNodeList 在 JavaScript 中的使用與特性

## 概述
`RadioNodeList` 是一個特殊的對象類型，在 JavaScript 中用於表示一組與 HTML `<input>` 標籤類型為 `radio` 的元素相對應的節點。這個對象常見於處理表單中的單選按鈕。

## 文件說明
`RadioNodeList` 是一個類似於陣列的集合，主要用於存取和操作 DOM 中的單選按鈕組。當你使用 `document.getElementsByName()` 或透過 `form.elements` 獲取表單元素時，會得到一個 `RadioNodeList` 對象。這個對象提供了一些方法和屬性，讓開發者可以輕鬆地管理這些單選按鈕的狀態。

### 目的
- 管理一組單選按鈕的選擇狀態。
- 便於檢查哪一個單選按鈕被選中。

### 用法
獲取 `RadioNodeList` 的常用方法包括：
- 使用 `document.getElementsByName('name')` 來獲取一組單選按鈕。
- 使用表單的 `elements` 屬性來獲取。

```javascript
const radioButtons = document.getElementsByName('gender'); // 獲取名稱為 'gender' 的單選按鈕
```

## 示例
### 基本用法範例
```html
<form id="myForm">
    <input type="radio" name="gender" value="male"> 男
    <input type="radio" name="gender" value="female"> 女
    <input type="radio" name="gender" value="other"> 其他
</form>
<button id="submit">提交</button>
<script>
    document.getElementById('submit').addEventListener('click', function() {
        const radios = document.getElementsByName('gender');
        let selectedValue;
        for (const radio of radios) {
            if (radio.checked) {
                selectedValue = radio.value;
                break;
            }
        }
        console.log(`選擇的性別是: ${selectedValue}`);
    });
</script>
```

## 解釋
在使用 `RadioNodeList` 時需要注意以下幾點：
1. **只能選擇一個**：單選按鈕的特性在於同一時間內只能選擇一個，因此在處理時需要檢查每個按鈕的 `checked` 屬性。
2. **集合的類似陣列**：`RadioNodeList` 看起來像陣列，但並不完全是陣列，因此無法直接使用陣列的方法如 `map` 或 `filter`。
3. **獲取選擇的值**：在處理表單提交時，必須遍歷 `RadioNodeList` 以確定哪一個按鈕是被選中的。

## 一句總結
`RadioNodeList` 是一個用來表示與 HTML 單選按鈕相關的節點集合，並提供方便的接口來管理用戶的選擇。