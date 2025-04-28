<!--
Meta Description: # JavaScript 的 Opener 物件：用於控制瀏覽器窗口 ## 簡介 在 JavaScript 中，`opener` 是一個屬性，用於引用打開當前窗口的父窗口。這個功能在處理多個窗口或標籤頁時特別有用，尤其是在需要在不同窗口之間傳遞信息時。 ## 文檔 `opener` 屬性屬於 `Wi...
Meta Keywords: opener, html, javascript, window, head
-->

# JavaScript 的 Opener 物件：用於控制瀏覽器窗口

## 簡介
在 JavaScript 中，`opener` 是一個屬性，用於引用打開當前窗口的父窗口。這個功能在處理多個窗口或標籤頁時特別有用，尤其是在需要在不同窗口之間傳遞信息時。

## 文檔
`opener` 屬性屬於 `Window` 物件。當一個窗口是通過 `window.open()` 方法打開的時候，這個窗口可以使用 `opener` 屬性來訪問其父窗口的 JavaScript 環境。這使得開發者能夠在新窗口中執行父窗口的函數或訪問其變數。

### 目的
`opener` 的主要目的是允許新窗口或標籤頁與其原始窗口進行交互，這在執行一些需要上下文的操作時非常方便。

### 使用方法
要使用 `opener` 屬性，你可以直接引用它來訪問父窗口。例如，假設你有一個在父窗口中定義的函數，你可以在新窗口中這樣調用：

```javascript
if (opener) {
    opener.someFunction();
}
```

這段代碼會檢查 `opener` 是否存在，然後調用父窗口中的 `someFunction` 函數。

## 範例
### 基本用法
下面是一個簡單的例子，展示如何在新窗口中使用 `opener`：

**父窗口的程式碼**：
```html
<!DOCTYPE html>
<html>
<head>
    <title>父窗口</title>
    <script>
        function sayHello() {
            alert('你好，來自父窗口的問候！');
        }

        function openChildWindow() {
            window.open('child.html', '_blank');
        }
    </script>
</head>
<body>
    <button onclick="openChildWindow()">打開子窗口</button>
</body>
</html>
```

**子窗口 (child.html) 的程式碼**：
```html
<!DOCTYPE html>
<html>
<head>
    <title>子窗口</title>
    <script>
        function callParentFunction() {
            if (opener) {
                opener.sayHello();
            }
        }

        window.onload = callParentFunction;
    </script>
</head>
<body>
    <h1>子窗口已加載</h1>
</body>
</html>
```

在這個例子中，當子窗口加載時，它會自動調用父窗口的 `sayHello` 函數，顯示一個提示框。

## 解釋
使用 `opener` 時有幾個常見的陷阱需要注意：

- **安全性問題**：如果子窗口試圖訪問父窗口的私有數據或函數，可能會導致安全性漏洞。因此，務必確保任何通過 `opener` 進行的交互都是安全的。
  
- **跨域問題**：如果父窗口和子窗口不在同一個域名下，則無法通過 `opener` 進行交互，這會引發安全錯誤。

- **關閉父窗口**：如果父窗口在子窗口打開後被關閉，`opener` 將會是 `null`，這需要在代碼中妥善處理。

## 一句話總結
`opener` 屬性允許 JavaScript 獲取打開當前窗口的父窗口對象，從而實現兩者之間的交互。