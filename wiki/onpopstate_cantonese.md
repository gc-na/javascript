<!--
Meta Description: # onpopstate 事件：JavaScript 中的歷史管理 ## 簡介 `onpopstate` 是一個在 JavaScript 中使用的事件，當瀏覽器的歷史紀錄狀態改變時觸發。這通常發生在用戶使用後退或前進按鈕時，或者通過 JavaScript 操作歷史紀錄。 ## 文檔 ### 目的 `...
Meta Keywords: onpopstate, event, state, history, button
-->

# onpopstate 事件：JavaScript 中的歷史管理

## 簡介
`onpopstate` 是一個在 JavaScript 中使用的事件，當瀏覽器的歷史紀錄狀態改變時觸發。這通常發生在用戶使用後退或前進按鈕時，或者通過 JavaScript 操作歷史紀錄。

## 文檔
### 目的
`onpopstate` 事件主要用於監控和處理歷史紀錄狀態的變化，這對於單頁應用程序（SPA）特別重要，因為它可以讓開發者在用戶導航時保持應用的狀態。

### 使用方式
要使用 `onpopstate` 事件，你需要將事件處理器分配給 `window` 對象的 `onpopstate` 屬性。當用戶導航到一個新的歷史狀態時，這個事件會被觸發。

```javascript
window.onpopstate = function(event) {
    if (event.state) {
        console.log("狀態變更:", event.state);
    }
};
```

### 詳細說明
- `event.state`：這個屬性包含與當前歷史紀錄狀態相關的數據。當你使用 `history.pushState()` 或 `history.replaceState()` 方法時，這些數據會被設置。
- `onpopstate` 事件不會在首次加載頁面時觸發，只有在用戶通過瀏覽器的歷史紀錄進行導航時才會觸發。

## 例子
### 基本使用示例
以下是一個簡單的例子，展示如何使用 `onpopstate` 事件來處理歷史狀態：

```html
<!DOCTYPE html>
<html lang="zh-HK">
<head>
    <meta charset="UTF-8">
    <title>onpopstate 事件示例</title>
    <script>
        window.onload = function() {
            // 添加歷史狀態
            history.pushState({page: 1}, "頁面 1", "?page=1");

            window.onpopstate = function(event) {
                if (event.state) {
                    console.log("現在的頁面:", event.state.page);
                }
            };
        };

        function goToPage(pageNumber) {
            history.pushState({page: pageNumber}, "頁面 " + pageNumber, "?page=" + pageNumber);
            console.log("轉到頁面:", pageNumber);
        }
    </script>
</head>
<body>
    <button onclick="goToPage(1)">頁面 1</button>
    <button onclick="goToPage(2)">頁面 2</button>
    <button onclick="goToPage(3)">頁面 3</button>
</body>
</html>
```

## 解釋
### 常見問題與注意事項
- `onpopstate` 事件不會在頁面加載時觸發，因此如果你需要在頁面首次加載時處理狀態，你應該在頁面加載時檢查 `history.state`。
- 如果歷史狀態未變更（例如，使用 `history.pushState()` 但沒有改變狀態）則不會觸發 `onpopstate`。
- 注意在使用 `pushState` 和 `replaceState` 時，必須正確設置狀態對象，以便在 `onpopstate` 中能夠正確獲取所需的數據。

## 一句總結
`onpopstate` 是一個用於監控瀏覽器歷史狀態變化的事件，對於實現單頁應用程序的流暢導航至關重要。