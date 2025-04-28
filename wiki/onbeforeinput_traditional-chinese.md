<!--
Meta Description: # JavaScript 的 onbeforeinput 事件詳解 ## 摘要 `onbeforeinput` 是一個用於捕捉用戶在表單輸入元素中即將輸入數據的事件。這一事件在用戶實際輸入數據前觸發，允許開發者進行即時處理或驗證。 ## 文檔 `onbeforeinput` 事件屬於輸入事件的一部分...
Meta Keywords: event, onbeforeinput, input, html, javascript
-->

# JavaScript 的 onbeforeinput 事件詳解

## 摘要
`onbeforeinput` 是一個用於捕捉用戶在表單輸入元素中即將輸入數據的事件。這一事件在用戶實際輸入數據前觸發，允許開發者進行即時處理或驗證。

## 文檔
`onbeforeinput` 事件屬於輸入事件的一部分，當用戶在 `<input>`、`<textarea>` 或其他可編輯元素中進行輸入時，該事件會被觸發。這個事件可以幫助開發者在用戶輸入之前進行質量檢查、格式化或其他即時反饋。

### 目的
`onbeforeinput` 主要用於：
- 在用戶輸入數據之前進行有效性檢查。
- 提供即時反饋或格式化輸入內容。
- 實現特定的用戶界面交互，如自動填充或提示。

### 用法
`onbeforeinput` 可以通過 HTML 屬性或 JavaScript 事件監聽器來使用。以下是基本的用法示例：

#### HTML 屬性
```html
<input type="text" onbeforeinput="handleBeforeInput(event)">
```

#### JavaScript 事件監聽器
```javascript
const inputElement = document.querySelector('input');
inputElement.addEventListener('beforeinput', handleBeforeInput);

function handleBeforeInput(event) {
    console.log('即將輸入:', event.data);
    // 在此處添加其他處理邏輯
}
```

## 範例
以下是幾個 `onbeforeinput` 的使用範例：

### 範例 1：限制輸入的字符數
```html
<input type="text" id="username" onbeforeinput="limitInput(event)">

<script>
function limitInput(event) {
    const input = event.target;
    if (input.value.length >= 10) {
        event.preventDefault(); // 防止超過 10 個字符
        alert('用戶名不能超過 10 個字符。');
    }
}
</script>
```

### 範例 2：格式化輸入
```html
<input type="text" id="phone" onbeforeinput="formatPhone(event)">

<script>
function formatPhone(event) {
    const input = event.target;
    const formatted = input.value.replace(/\D/g, ''); // 只允許數字
    input.value = formatted;
}
</script>
```

## 解釋
在使用 `onbeforeinput` 時，開發者需要注意以下幾點：
- `event.preventDefault()` 可以用來阻止即將發生的輸入行為，這對於驗證或格式化輸入非常有用。
- 此事件在某些瀏覽器中可能不被完全支持，因此在使用之前應檢查兼容性。
- `event.data` 包含即將輸入的內容，開發者可以利用這一特性來獲取用戶輸入的數據。

## 一句總結
`onbeforeinput` 事件允許開發者在用戶輸入數據之前進行即時處理和驗證。