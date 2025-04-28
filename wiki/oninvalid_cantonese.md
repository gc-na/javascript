<!--
Meta Description: # JavaScript oninvalid 事件：表單驗證的關鍵 ## 概要 `oninvalid` 是一個 JavaScript 事件，它在 HTML 表單中使用，用於處理用戶輸入不符合預期格式或者條件時的情況。此事件能夠讓開發者自定義錯誤處理和反饋。 ## 文檔 `oninvalid` 事件是...
Meta Keywords: oninvalid, javascript, event, html, setcustomvalidity
-->

# JavaScript oninvalid 事件：表單驗證的關鍵

## 概要
`oninvalid` 是一個 JavaScript 事件，它在 HTML 表單中使用，用於處理用戶輸入不符合預期格式或者條件時的情況。此事件能夠讓開發者自定義錯誤處理和反饋。

## 文檔
`oninvalid` 事件是當用戶提交表單時，某個表單元素的驗證未通過而觸發的事件。這通常發生在 `<input>`、`<textarea>` 或 `<select>` 元素中。當用戶輸入的數據不符合元素的驗證條件（如 `required`、`pattern`、`min`、`max` 等）時，`oninvalid` 事件會被觸發。

### 用法
`oninvalid` 事件可以在 HTML 中直接使用，也可以通過 JavaScript 進行綁定。以下是其基本語法：

```html
<input type="text" required oninvalid="customInvalidHandler(this);" />
```

在 JavaScript 中，可以使用 addEventListener 來綁定事件：

```javascript
const inputField = document.querySelector('input[type="text"]');
inputField.addEventListener('invalid', function(event) {
    // 自定義處理邏輯
});
```

### 詳細信息
- **觸發條件**：當用戶嘗試提交一個包含不合格數據的表單時。
- **事件對象**：`event` 對象包含有關事件的詳細信息，可以通過 `event.target` 訪問引發事件的元素。
- **取消默認行為**：可以通過 `event.preventDefault()` 來阻止默認的錯誤提示顯示，以便提供自定義的反饋。

## 示例
以下是使用 `oninvalid` 事件的簡單示例：

### HTML 示例
```html
<form>
    <label for="username">用戶名（必填）:</label>
    <input type="text" id="username" required oninvalid="this.setCustomValidity('請輸入用戶名');" />
    <button type="submit">提交</button>
</form>
```

### JavaScript 示例
```javascript
document.querySelector('form').addEventListener('submit', function(event) {
    const usernameField = document.getElementById('username');
    usernameField.setCustomValidity(''); // 重置自定義有效性消息

    if (!usernameField.validity.valid) {
        usernameField.setCustomValidity('請輸入有效的用戶名。');
        usernameField.reportValidity(); // 顯示錯誤消息
        event.preventDefault(); // 阻止表單提交
    }
});
```

## 解釋
- **常見陷阱**：如果未設置 `setCustomValidity`，默認的錯誤提示可能無法滿足用戶需求。
- **兼容性**：`oninvalid` 事件在大多數現代瀏覽器中都受到支持，但在某些舊版瀏覽器（如 Internet Explorer）中可能存在問題。
- **自定義錯誤消息**：使用 `setCustomValidity` 方法可以提供更具體的錯誤反饋。

## 單行摘要
`oninvalid` 事件在 JavaScript 中用於處理表單元素的驗證失敗，讓開發者能夠提供自定義的錯誤反饋。