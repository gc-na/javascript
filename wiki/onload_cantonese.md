<!--
Meta Description: # JavaScript onload 事件：網頁加載後的執行時機 ## 概述 `onload` 是一個 JavaScript 事件，當網頁的所有資源（如圖片、樣式表、JavaScript 文件等）都已經完全加載後觸發。這個事件常用於確保在對 DOM 進行操作或執行其他代碼之前，所有元素都已準備好。...
Meta Keywords: onload, html, body, javascript, head
-->

# JavaScript onload 事件：網頁加載後的執行時機

## 概述
`onload` 是一個 JavaScript 事件，當網頁的所有資源（如圖片、樣式表、JavaScript 文件等）都已經完全加載後觸發。這個事件常用於確保在對 DOM 進行操作或執行其他代碼之前，所有元素都已準備好。

## 文檔
### 目的
`onload` 事件的主要目的是在網頁完全加載後執行特定的 JavaScript 代碼，這樣可以避免因為 DOM 尚未加載而導致的錯誤。

### 用法
可以在 `<body>` 標籤中直接使用 `onload` 屬性，或是通過 JavaScript 註冊事件處理器。

#### 用法示例 1：使用 HTML 屬性
```html
<body onload="initFunction()">
    <h1>歡迎來到我的網站</h1>
</body>
```

#### 用法示例 2：使用 JavaScript 註冊事件
```html
<!DOCTYPE html>
<html lang="zh-HK">
<head>
    <meta charset="UTF-8">
    <title>示例頁面</title>
    <script>
        function initFunction() {
            console.log("頁面已加載！");
        }

        window.onload = initFunction; // 註冊 onload 事件
    </script>
</head>
<body>
    <h1>歡迎來到我的網站</h1>
</body>
</html>
```

## 例子
以下是一個簡單的 `onload` 事件示例，當網頁加載完成後，顯示一個歡迎信息。

```html
<!DOCTYPE html>
<html lang="zh-HK">
<head>
    <meta charset="UTF-8">
    <title>歡迎頁面</title>
    <script>
        function displayWelcomeMessage() {
            alert("歡迎來到我們的網站！");
        }

        window.onload = displayWelcomeMessage;
    </script>
</head>
<body>
    <h1>網站內容</h1>
</body>
</html>
```

## 解釋
使用 `onload` 時需注意以下幾點：
- **多重事件處理器**：如果你使用 `onload` 屬性來指定多個函數，只有最後一個函數會被執行。為了註冊多個函數，最佳做法是使用 `addEventListener` 方法。
- **加載時間**：`onload` 事件在所有資源加載完成後才會觸發，這可能會導致用戶在大量資源的情況下等待較長時間。
- **舊版瀏覽器兼容性**：某些舊版瀏覽器可能對 `onload` 的支持不佳，開發者應考慮兼容性問題。

## 一句總結
`onload` 事件在網頁完全加載後觸發，是執行初始化代碼的重要時機。