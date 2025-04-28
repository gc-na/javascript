<!--
Meta Description: # HTMLFieldSetElement：JavaScript 操作 HTML 表單的關鍵元素 ## 概要 HTMLFieldSetElement 是一個用於組織表單控件的 HTML 元素，能夠將相關的表單元素分組，以提高可讀性和可用性。在 JavaScript 中，開發者可以利用此元素來更方便地...
Meta Keywords: fieldset, html, javascript, htmlfieldsetelement, legend
-->

# HTMLFieldSetElement：JavaScript 操作 HTML 表單的關鍵元素

## 概要
HTMLFieldSetElement 是一個用於組織表單控件的 HTML 元素，能夠將相關的表單元素分組，以提高可讀性和可用性。在 JavaScript 中，開發者可以利用此元素來更方便地操作表單組件。

## 文件說明
HTMLFieldSetElement 是一個 HTML 元素，通常用於將一組表單控件（例如輸入框、選擇框等）歸類在一起。它提供了一種邏輯結構，幫助用戶理解表單的內容和結構。Fieldset 元素通常與 `<legend>` 元素一起使用，以顯示這組控件的標題。

### 目的
- 組織和分組表單控件
- 提高表單的可讀性
- 提供語義化的 HTML 結構

### 用法
在 HTML 中，使用 `<fieldset>` 標籤來創建 FieldSet 元素。透過 JavaScript，開發者可以輕鬆地訪問和操作這些元素。

```html
<fieldset>
    <legend>個人資訊</legend>
    <input type="text" name="name" placeholder="姓名">
    <input type="email" name="email" placeholder="電子郵件">
</fieldset>
```

在 JavaScript 中，可以使用 `document.getElementsByTagName()`、`document.querySelector()` 或其他 DOM 操作方法來獲取 FieldSet 元素，並進行相應的操作。

```javascript
const fieldset = document.querySelector('fieldset');
fieldset.style.border = '2px solid blue'; // 修改邊框顏色
```

## 範例
以下是 HTMLFieldSetElement 的基本用法範例：

### 基本範例
```html
<!DOCTYPE html>
<html lang="zh-Hant">
<head>
    <meta charset="UTF-8">
    <title>FieldSet 示例</title>
</head>
<body>
    <form>
        <fieldset>
            <legend>聯絡方式</legend>
            <label for="phone">電話:</label>
            <input type="tel" id="phone" name="phone">
        </fieldset>
    </form>
    <script>
        const fieldset = document.querySelector('fieldset');
        console.log(fieldset); // 獲取 FieldSet 元素
    </script>
</body>
</html>
```

### JavaScript 操作範例
```javascript
const fieldset = document.querySelector('fieldset');
fieldset.disabled = true; // 禁用 FieldSet 中的所有表單元素
```

## 解釋
在使用 HTMLFieldSetElement 時，開發者需注意以下幾點：
- FieldSet 元素中的所有表單控件在父元素被禁用時都會一併被禁用。
- FieldSet 元素不支援某些 CSS 樣式，開發者需確保所需的樣式不會受到限制。
- 使用 `<legend>` 元素能夠為 FieldSet 提供標題，這對於可訪問性和用戶體驗非常重要。

## 總結
HTMLFieldSetElement 是一個有助於組織表單控件的 HTML 元素，通過 JavaScript 可以輕鬆地進行操作和控制。