<!--
Meta Description: # JavaScript 中的「blur」事件：深入解析與實用範例 ## 簡介 在 JavaScript 中，「blur」事件是用於處理元素失去焦點的情況，特別是在表單元素和按鈕中。當使用者點擊其他地方或使用鍵盤導航離開當前元素時，會觸發此事件。 ## 文檔 ### 目的 「blur」事件的主要目的...
Meta Keywords: blur, javascript, script, html, addeventlistener
-->

# JavaScript 中的「blur」事件：深入解析與實用範例

## 簡介
在 JavaScript 中，「blur」事件是用於處理元素失去焦點的情況，特別是在表單元素和按鈕中。當使用者點擊其他地方或使用鍵盤導航離開當前元素時，會觸發此事件。

## 文檔
### 目的
「blur」事件的主要目的是監聽並響應使用者與頁面互動的方式，特別是在表單驗證或用戶體驗方面。

### 使用方式
「blur」事件可以通過 JavaScript 的事件監聽器來使用。可以在 HTML 元素上直接設置，也可以在 JavaScript 代碼中添加。

#### 語法：
```javascript
element.addEventListener('blur', function(event) {
    // 事件處理代碼
});
```

### 參數
- `event`: 事件對象，包含有關事件的詳細信息。

### 例子
以下是使用「blur」事件的基本範例：

#### 範例 1：基本使用
```html
<input type="text" id="myInput" placeholder="請輸入文字" />

<script>
    const inputElement = document.getElementById('myInput');
    
    inputElement.addEventListener('blur', function() {
        console.log('輸入框失去焦點');
    });
</script>
```

#### 範例 2：表單驗證
```html
<form id="myForm">
    <input type="text" id="username" placeholder="用戶名" required />
    <input type="submit" value="提交" />
</form>

<script>
    const usernameField = document.getElementById('username');
    
    usernameField.addEventListener('blur', function() {
        if (usernameField.value === '') {
            alert('用戶名不能為空');
        }
    });
</script>
```

## 解釋
使用「blur」事件時，有幾個常見的陷阱和注意事項：
- **事件觸發時機**：當使用者點擊其他元素或使用鍵盤導航移動焦點時，「blur」事件會被觸發，確保在需要的時候正確處理事件。
- **不要與「focus」混淆**：與「blur」相對的事件是「focus」，它在元素獲得焦點時觸發。兩者經常一起使用來進行用戶輸入的處理。
- **性能考量**：在大量元素上使用「blur」事件時，需注意性能問題，適當地使用節流或防抖技術來優化效能。

## 一句總結
「blur」事件是 JavaScript 中用於檢測元素失去焦點的重要工具，適用於表單驗證及用戶互動管理。