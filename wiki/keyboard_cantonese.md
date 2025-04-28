<!--
Meta Description: # JavaScript 鍵盤事件 (Keyboard Events) ## 簡介 在 JavaScript 中，鍵盤事件是用來偵測用戶在鍵盤上按下或放開鍵的行為，這些事件對於開發互動應用程式非常重要。 ## 文檔 鍵盤事件主要包括三種：`keydown`、`keypress` 和 `keyup`。...
Meta Keywords: event, javascript, keydown, keypress, keyup
-->

# JavaScript 鍵盤事件 (Keyboard Events)

## 簡介
在 JavaScript 中，鍵盤事件是用來偵測用戶在鍵盤上按下或放開鍵的行為，這些事件對於開發互動應用程式非常重要。

## 文檔
鍵盤事件主要包括三種：`keydown`、`keypress` 和 `keyup`。這些事件可以幫助開發者獲取用戶的鍵盤輸入，並做出相應的反應。

### 目的
鍵盤事件的主要目的是提供一種方式來判斷用戶何時按下或放開鍵盤上的按鍵。這對於各種應用程序（如表單驗證、遊戲控制等）非常有用。

### 使用
要使用鍵盤事件，你需要將事件監聽器附加到 DOM 元素上。例如：

```javascript
document.addEventListener('keydown', function(event) {
    console.log(`你按下了鍵: ${event.key}`);
});
```

這段代碼會在用戶按下鍵盤上的任何鍵時，將鍵的名稱輸出到控制台。

## 示例
以下是一些基本的鍵盤事件使用示例：

### `keydown` 事件
```javascript
document.addEventListener('keydown', function(event) {
    if (event.key === 'Enter') {
        alert('你按下了 Enter 鍵！');
    }
});
```

### `keyup` 事件
```javascript
document.addEventListener('keyup', function(event) {
    console.log(`你放開了鍵: ${event.key}`);
});
```

### `keypress` 事件
```javascript
document.addEventListener('keypress', function(event) {
    console.log(`你正在輸入: ${String.fromCharCode(event.charCode)}`);
});
```

## 解釋
- **常見陷阱**：`keypress` 事件在某些瀏覽器中已被棄用，建議使用 `keydown` 和 `keyup` 事件來替代。
- **事件順序**：`keydown` 事件會在按下鍵時觸發，然後是 `keypress`，最後是 `keyup`。了解這些事件的觸發順序有助於更好地管理鍵盤輸入。
- **跨瀏覽器兼容性**：在不同的瀏覽器中，事件的行為可能會有所不同，因此在開發過程中應進行測試。

## 總結
鍵盤事件在 JavaScript 中是用來偵測鍵盤輸入的關鍵工具，能夠讓開發者創建更加互動的應用程式。