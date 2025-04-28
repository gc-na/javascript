<!--
Meta Description: # JavaScript 的 ondrag 事件詳解 ## 概述 `ondrag` 是一個 JavaScript 事件，屬於拖放 API，主要用於處理用戶在網頁上拖動元素的情況。當元素被拖動時，`ondrag` 事件會被觸發，這使得開發者能夠對拖動行為進行控制和反應。 ## 文檔 ### 目的 `o...
Meta Keywords: ondrag, javascript, html, draggable, event
-->

# JavaScript 的 ondrag 事件詳解

## 概述
`ondrag` 是一個 JavaScript 事件，屬於拖放 API，主要用於處理用戶在網頁上拖動元素的情況。當元素被拖動時，`ondrag` 事件會被觸發，這使得開發者能夠對拖動行為進行控制和反應。

## 文檔
### 目的
`ondrag` 事件的主要目的是在用戶拖動 HTML 元素時，執行特定的 JavaScript 代碼。這對於創建可互動的用戶界面是非常有用的，特別是在實現拖放功能時。

### 使用方法
`ondrag` 事件可以直接在 HTML 元素中使用，也可以通過 JavaScript 來監聽。

#### HTML 示例
```html
<div id="draggable" draggable="true" ondrag="drag(event)">拖動我</div>
```

#### JavaScript 示例
```javascript
const draggableElement = document.getElementById("draggable");
draggableElement.ondrag = function(event) {
    console.log("元素正在被拖動");
};
```

### 詳細說明
- **屬性**: `draggable` 屬性必須設置為 `true`，以使元素可被拖動。
- **事件對象**: `event` 參數提供了有關拖動操作的詳細信息，包括拖動的目標和輸入的位置。
- **兼容性**: `ondrag` 在大多數現代瀏覽器中均受支持，但在某些舊版瀏覽器中可能不兼容。

## 示例
### 基本用法
以下是一個簡單的示例，展示如何使用 `ondrag` 事件來跟蹤拖動元素的過程。

```html
<!DOCTYPE html>
<html lang="zh-Hant">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>拖動示例</title>
    <style>
        #draggable {
            width: 100px;
            height: 100px;
            background-color: blue;
            color: white;
            text-align: center;
            line-height: 100px;
        }
    </style>
</head>
<body>
    <div id="draggable" draggable="true" ondrag="drag(event)">拖動我</div>

    <script>
        function drag(event) {
            console.log("元素正在被拖動");
        }
    </script>
</body>
</html>
```

## 解釋
### 常見問題
- **未觸發事件**: 確保元素的 `draggable` 屬性設置為 `true`。如果未設置，`ondrag` 不會被觸發。
- **事件處理程序**: 如果使用 JavaScript 來設置 `ondrag` 事件，請確保在 DOM 加載後進行設置，否則可能會導致無法正常工作。
- **其他拖放事件**: `ondrag` 事件通常與 `ondragstart` 和 `ondragend` 事件一起使用，以便更全面地處理拖放過程。

## 總結
`ondrag` 事件是 JavaScript 中一個強大的功能，允許開發者在用戶拖動元素時進行反應和控制，從而增強網頁的互動性。