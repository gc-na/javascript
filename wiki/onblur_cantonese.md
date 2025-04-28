<!--
Meta Description: # JavaScript onblur 事件：網頁表單中的焦點丟失處理 ## 簡介 在JavaScript中，`onblur`事件用於處理當元素失去焦點的情況。這通常應用於表單字段，當用戶點擊其他地方或切換到其他元素時，該事件會被觸發。 ## 文檔 `onblur`事件是一個HTML DOM事件，用...
Meta Keywords: onblur, html, input, head, title
-->

# JavaScript onblur 事件：網頁表單中的焦點丟失處理

## 簡介
在JavaScript中，`onblur`事件用於處理當元素失去焦點的情況。這通常應用於表單字段，當用戶點擊其他地方或切換到其他元素時，該事件會被觸發。

## 文檔
`onblur`事件是一個HTML DOM事件，用來監控元素失去焦點的情況。當用戶從某個可聚焦的元素（例如：輸入框、下拉菜單等）切換到另一個元素時，`onblur`事件會被觸發。這個事件對於表單驗證、用戶界面交互等場景非常有用。

### 用法
`onblur`事件可以直接在HTML元素中使用，也可以通過JavaScript進行事件綁定。以下是兩種常見的用法：

1. **HTML屬性**：
   ```html
   <input type="text" onblur="alert('失去焦點！')">
   ```

2. **JavaScript事件監聽器**：
   ```javascript
   const inputField = document.getElementById('myInput');
   inputField.addEventListener('blur', function() {
       console.log('輸入框失去焦點');
   });
   ```

## 範例
### 基本用法
```html
<!DOCTYPE html>
<html lang="zh-HK">
<head>
    <meta charset="UTF-8">
    <title>onblur 範例</title>
</head>
<body>
    <input type="text" id="nameInput" placeholder="請輸入姓名" onblur="checkInput()">
    <script>
        function checkInput() {
            const input = document.getElementById('nameInput').value;
            if (!input) {
                alert('姓名不能為空！');
            }
        }
    </script>
</body>
</html>
```

### 使用事件監聽器
```html
<!DOCTYPE html>
<html lang="zh-HK">
<head>
    <meta charset="UTF-8">
    <title>事件監聽器範例</title>
</head>
<body>
    <input type="text" id="emailInput" placeholder="請輸入電子郵件">
    <script>
        const emailField = document.getElementById('emailInput');
        emailField.addEventListener('blur', function() {
            if (!this.value.includes('@')) {
                alert('請輸入有效的電子郵件地址。');
            }
        });
    </script>
</body>
</html>
```

## 解釋
使用`onblur`事件時，有幾個常見的陷阱需要注意：
- **事件觸發的時機**：`onblur`事件在元素失去焦點時觸發，這可能會影響用戶的輸入體驗，特別是當用戶還未完成輸入時。
- **與`onfocus`配合使用**：`onblur`經常與`onfocus`事件搭配使用，以便在元素獲得焦點時進行初始化或清除狀態。
- **多個輸入框的處理**：如果在多個輸入框中使用相同的`onblur`處理程序，需確保能正確識別當前字段的狀態。

## 一句總結
`onblur`事件是JavaScript中用於處理元素失去焦點的事件，適合用於表單驗證與用戶交互。