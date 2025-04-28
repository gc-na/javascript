<!--
Meta Description: # JavaScript 中的 "opener" 屬性：理解與應用 ## 簡介 在 JavaScript 中，`opener` 屬性是一個有用的工具，允許開啟新視窗或標籤的網頁訪問其父視窗的引用。這對於在多個視窗之間進行互動的應用程序來說是非常重要的。 ## 文檔 ### 目的 `opener` 屬...
Meta Keywords: opener, window, javascript, open, newwindow
-->

# JavaScript 中的 "opener" 屬性：理解與應用

## 簡介
在 JavaScript 中，`opener` 屬性是一個有用的工具，允許開啟新視窗或標籤的網頁訪問其父視窗的引用。這對於在多個視窗之間進行互動的應用程序來說是非常重要的。

## 文檔
### 目的
`opener` 屬性的主要目的是允許新開啟的窗口或標籤頁訪問其原始（父）窗口的 JavaScript 環境，這樣可以方便地在兩個窗口之間傳遞數據或指令。

### 使用方法
`opener` 屬性通常用於新開啟的窗口或標籤中。當一個窗口是通過 JavaScript 的 `window.open()` 方法打開的時候，該窗口就可以透過 `window.opener` 來獲取原始窗口的引用。例如：

```javascript
// 在父窗口中打開新窗口
var newWindow = window.open('https://example.com');

// 在新窗口中訪問原始窗口
if (window.opener) {
    window.opener.console.log('這是來自新窗口的消息');
}
```

### 詳細說明
- `opener` 屬性返回一個對父窗口的引用，如果該窗口不是通過 `window.open()` 方法打開的，則返回 `null`。
- 這個屬性可以被用於傳遞資料或調用父窗口中的函數。
- 注意，出於安全考量，某些瀏覽器可能會限制跨域訪問，這意味著如果父窗口和新窗口的來源不同，則無法使用 `opener` 屬性。

## 範例
### 基本使用範例
```javascript
// 父窗口代碼
var newWindow = window.open('child.html');

// 子窗口代碼（child.html）
if (window.opener) {
    window.opener.alert('子窗口已打開');
}
```

### 傳遞資料範例
```javascript
// 父窗口代碼
var newWindow = window.open('child.html');
newWindow.data = { message: '這是來自父窗口的數據' };

// 子窗口代碼（child.html）
if (window.opener && window.opener.data) {
    console.log(window.opener.data.message); // 輸出: 這是來自父窗口的數據
}
```

## 解釋
使用 `opener` 屬性時，需要注意以下幾點：
- **安全性**：當涉及到跨域操作時，某些瀏覽器會阻止對 `opener` 的訪問，這會導致 `window.opener` 返回 `null`。
- **性能**：過多的依賴於 `opener` 可能會影響性能，因為每次訪問都需要查找父窗口的引用。
- **關閉窗口**：如果父窗口被關閉，`opener` 將不再有效，訪問它會導致錯誤。

## 一句總結
`opener` 屬性在 JavaScript 中允許新窗口或標籤訪問其父窗口的引用，便於實現多窗口間的交互和數據傳遞。