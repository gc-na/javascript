<!--
Meta Description: # ValidityState：JavaScript 中的有效性狀態物件 ## 摘要 `ValidityState` 是一個用於表示 HTML 表單元素有效性狀態的物件，能夠幫助開發者在進行表單驗證時獲取元素的有效性資訊。 ## 文檔 `ValidityState` 物件通常用於 HTML 表單元素...
Meta Keywords: validitystate, validity, html, email, form
-->

# ValidityState：JavaScript 中的有效性狀態物件

## 摘要
`ValidityState` 是一個用於表示 HTML 表單元素有效性狀態的物件，能夠幫助開發者在進行表單驗證時獲取元素的有效性資訊。

## 文檔
`ValidityState` 物件通常用於 HTML 表單元素，透過該物件，開發者可以檢查表單元素的各種有效性狀態，例如是否有效、是否為必填項、格式是否正確等。這些狀態可以通過表單元素的 `validity` 屬性獲取。

### 目的
`ValidityState` 主要用於表單驗證，幫助開發者判斷用戶輸入的數據是否符合預期的格式與要求。

### 使用
要使用 `ValidityState`，您需要先獲取某個表單元素的 `validity` 屬性，該屬性返回 `ValidityState` 物件。以下是一些常用的有效性狀態屬性：

- `valid`: 表示元素的值是否有效。
- `valueMissing`: 表示必填欄位是否未填寫。
- `typeMismatch`: 表示元素值是否與預期的類型不匹配。
- `tooLong`: 表示元素的值是否超過了最大長度。
- `rangeUnderflow`: 表示元素的值是否小於最小值。
- `rangeOverflow`: 表示元素的值是否超過了最大值。

### 詳細範例
以下是使用 `ValidityState` 的基本範例：

```html
<form id="myForm">
  <label for="email">電子郵件:</label>
  <input type="email" id="email" required>
  <button type="submit">提交</button>
</form>

<script>
  const form = document.getElementById('myForm');
  const emailInput = document.getElementById('email');

  form.addEventListener('submit', function(event) {
    event.preventDefault(); // 防止表單提交
    const validity = emailInput.validity;

    if (validity.valid) {
      console.log('電子郵件有效！');
    } else {
      if (validity.valueMissing) {
        console.log('電子郵件為必填項！');
      } else if (validity.typeMismatch) {
        console.log('電子郵件格式不正確！');
      }
    }
  });
</script>
```

## 解釋
在使用 `ValidityState` 時，開發者應注意以下幾點：

- 確保表單元素具有正確的 HTML 屬性，例如 `required` 或 `type="email"`，以便 `ValidityState` 能夠正確反映其有效性。
- 在處理表單提交事件時，請記得使用 `event.preventDefault()` 來防止表單的默認提交行為，這樣可以在進行驗證後進行相應的處理。
- `ValidityState` 僅適用於瀏覽器支持的表單元素，某些舊版本的瀏覽器可能不支持。

## 總結
`ValidityState` 是一個關鍵的 JavaScript 物件，幫助開發者有效處理 HTML 表單的驗證與狀態管理。