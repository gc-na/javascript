<!--
Meta Description: # JavaScript 的 onblur 事件：用於處理失去焦點的事件 ## 概述 `onblur` 是一個與 HTML 元素相關的事件，當元素失去焦點時觸發。它通常用於表單輸入框，以便在用戶完成輸入並移開焦點時執行特定的 JavaScript 操作。 ## 文件說明 ### 目的 `onblur...
Meta Keywords: onblur, html, javascript, message, input
-->

# JavaScript 的 onblur 事件：用於處理失去焦點的事件

## 概述
`onblur` 是一個與 HTML 元素相關的事件，當元素失去焦點時觸發。它通常用於表單輸入框，以便在用戶完成輸入並移開焦點時執行特定的 JavaScript 操作。

## 文件說明
### 目的
`onblur` 事件主要用於處理用戶在表單中移動焦點的情況，特別是對於 `<input>`、`<textarea>` 和 `<select>` 等可編輯元素。通過監聽這個事件，開發者可以執行資料驗證、更新 UI 或執行其他相關的操作。

### 使用方法
`onblur` 事件可以通過 HTML 標籤的屬性或 JavaScript 事件監聽器來使用。以下是兩種常見的使用方式：

1. **HTML 內聯使用**：
   ```html
   <input type="text" onblur="myFunction()">
   ```

2. **JavaScript 事件監聽器**：
   ```javascript
   document.getElementById("myInput").onblur = function() {
       myFunction();
   };
   ```

### 詳細資訊
- `onblur` 事件不會冒泡，也就是說，它不會向上傳遞到父元素。
- 通常與 `onfocus` 事件一起使用，以便在獲得或失去焦點時進行特定的操作。
- 事件可以接收一個事件對象參數，提供有關事件的詳細資訊。

## 示例
### 基本用法
以下是一個簡單的示例，顯示如何使用 `onblur` 事件來驗證用戶輸入的電子郵件格式：

```html
<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <title>onblur 範例</title>
    <script>
        function validateEmail() {
            var emailInput = document.getElementById("email").value;
            var message = document.getElementById("message");
            var regex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/; // 簡單的電子郵件格式驗證

            if (!regex.test(emailInput)) {
                message.textContent = "請輸入有效的電子郵件地址。";
            } else {
                message.textContent = "電子郵件格式正確！";
            }
        }
    </script>
</head>
<body>
    <h1>電子郵件驗證示範</h1>
    <input type="text" id="email" placeholder="請輸入電子郵件" onblur="validateEmail()">
    <p id="message"></p>
</body>
</html>
```

## 解釋
### 常見問題
- **事件不觸發**：如果元素是不可見的，`onblur` 事件可能不會被觸發。確保元素是可見且可互動的。
- **與其他事件的衝突**：在某些情況下，使用 `onblur` 可能會與其他事件（例如 `onchange`）產生衝突，需謹慎設計交互邏輯。

### 附加註解
- 在多個元素上使用 `onblur` 時，考慮使用事件委託來提高性能。
- 在使用 `onblur` 事件時，記得考慮用戶體驗，避免在失去焦點時出現突兀的提示或訊息。

## 總結
`onblur` 是一個強大的事件，用於處理用戶在表單元素中失去焦點的情況，適合用於資料驗證和 UI 更新。