<!--
Meta Description: # JavaScript 的 oninvalid 事件處理器 ## 簡介 `oninvalid` 是一個 JavaScript 事件，用於監聽 HTML 表單元素的驗證失敗情況。當使用者提交表單時，如果某個輸入元素的值不符合定義的驗證規則，則會觸發此事件。 ## 文檔 `oninvalid` 事件主...
Meta Keywords: oninvalid, input, javascript, html, form
-->

# JavaScript 的 oninvalid 事件處理器

## 簡介
`oninvalid` 是一個 JavaScript 事件，用於監聽 HTML 表單元素的驗證失敗情況。當使用者提交表單時，如果某個輸入元素的值不符合定義的驗證規則，則會觸發此事件。

## 文檔
`oninvalid` 事件主要用於提高用戶體驗，讓開發者能夠自定義錯誤提示或進行其他處理。這個事件通常與 `<input>`、`<textarea>` 和 `<select>` 等表單元素一起使用。

### 目的
- 提供用戶友好的錯誤提示。
- 允許開發者自定義驗證反饋。

### 用法
`oninvalid` 事件可以通過直接在 HTML 標籤中設置屬性或通過 JavaScript 事件監聽器來使用。當用戶嘗試提交表單且某個輸入元素的值無效時，該事件會被觸發。

#### HTML 示例
```html
<form>
  <input type="text" required oninvalid="alert('請填寫此欄位！');">
  <input type="submit">
</form>
```

#### JavaScript 示例
```javascript
document.querySelector('input').addEventListener('invalid', function(event) {
  event.preventDefault(); // 防止默認的提示
  alert('請填寫此欄位！');
});
```

## 範例
以下是如何使用 `oninvalid` 事件的基本範例：

### 範例 1：直接設定屬性
```html
<form>
  <input type="email" required oninvalid="this.setCustomValidity('請輸入有效的電子郵件地址');" oninput="this.setCustomValidity('');">
  <input type="submit">
</form>
```

### 範例 2：使用 JavaScript 設定
```html
<form id="myForm">
  <input type="password" required id="password">
  <input type="submit">
</form>

<script>
  document.getElementById('password').addEventListener('invalid', function(event) {
    event.preventDefault();
    alert('密碼為必填項目！');
  });
</script>
```

## 解釋
在使用 `oninvalid` 時，有幾個常見的陷阱和注意事項：

- **未設置 required 屬性**：如果未設置 `required` 屬性，`oninvalid` 將不會被觸發。
- **默認提示**：瀏覽器會自動顯示默認的錯誤提示，可能需要使用 `event.preventDefault()` 來防止這種情況。
- **自定義驗證**：可以使用 `setCustomValidity()` 方法來設置自定義的錯誤消息，以便在驗證失敗時顯示。

## 一句話總結
`oninvalid` 事件允許開發者在表單元素驗證失敗時提供自定義反饋，以提升用戶體驗。