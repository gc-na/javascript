<!--
Meta Description: # JavaScript 事件：ondrag 事件詳解 ## 概述 `ondrag` 事件是 JavaScript 中用於處理拖放操作的事件之一。當用戶拖動一個元素時，`ondrag` 事件會被觸發，允許開發者對拖動過程進行反應和控制。 ## 文檔 ### 目的 `ondrag` 事件的主要目的是在...
Meta Keywords: ondrag, draggable, html, event, div
-->

# JavaScript 事件：ondrag 事件詳解

## 概述
`ondrag` 事件是 JavaScript 中用於處理拖放操作的事件之一。當用戶拖動一個元素時，`ondrag` 事件會被觸發，允許開發者對拖動過程進行反應和控制。

## 文檔
### 目的
`ondrag` 事件的主要目的是在用戶拖動元素時執行特定的 JavaScript 代碼，從而可以實現自定義的拖放功能。

### 使用
`ondrag` 事件可以附加到可拖動的 HTML 元素上，通常與 `draggable` 屬性一起使用。當元素被拖動時，相關的事件處理程序會被調用。

```html
<div id="draggable" draggable="true">拖動我！</div>
```

### 事件屬性
- **event.target**: 觸發事件的元素。
- **event.clientX**: 鼠標指針的 X 坐標。
- **event.clientY**: 鼠標指針的 Y 坐標。

## 範例
以下是一個簡單的示例，展示如何使用 `ondrag` 事件：

```html
<!DOCTYPE html>
<html lang="zh-HK">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ondrag 事件示例</title>
    <style>
        #draggable {
            width: 100px;
            height: 100px;
            background-color: lightblue;
            border: 1px solid blue;
            text-align: center;
            line-height: 100px;
            cursor: move;
        }
    </style>
</head>
<body>

<div id="draggable" draggable="true" ondrag="drag(event)">拖動我！</div>

<script>
function drag(event) {
    console.log("正在拖動元素：", event.target.id);
}
</script>

</body>
</html>
```

在這個示例中，當用戶拖動 `div` 元素時，會在控制台上輸出元素的 ID。

## 解釋
在使用 `ondrag` 事件時，開發者需要注意以下幾點：
- 確保元素設置了 `draggable="true"` 屬性，否則 `ondrag` 事件不會被觸發。
- `ondrag` 事件的觸發並不代表元素已經被放置，這是一個過程中的事件，通常還需要配合其他事件（如 `ondrop`）來完成完整的拖放操作。
- 由於不同的瀏覽器對於拖放操作的支持程度不同，應進行充分的測試。

## 總結
`ondrag` 事件是 JavaScript 中用於監聽和處理拖動操作的事件，通過適當的使用，可以增強用戶的交互體驗。