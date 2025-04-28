<!--
Meta Description: # JavaScript 的 onmouseover 事件 ## 簡介 `onmouseover` 是一個 JavaScript 事件，用於在滑鼠指標移動到 HTML 元素上時觸發特定的 JavaScript 代碼。這個事件通常用於交互式網頁設計，能夠提升用戶體驗。 ## 文檔 ### 目的 `on...
Meta Keywords: onmouseover, html, javascript, div, head
-->

# JavaScript 的 onmouseover 事件

## 簡介
`onmouseover` 是一個 JavaScript 事件，用於在滑鼠指標移動到 HTML 元素上時觸發特定的 JavaScript 代碼。這個事件通常用於交互式網頁設計，能夠提升用戶體驗。

## 文檔
### 目的
`onmouseover` 事件的主要目的是監聽滑鼠指標進入指定元素的行為，通常用於創建動態效果，例如顯示提示、改變元素樣式或執行其他 JavaScript 函數。

### 使用方法
`onmouseover` 事件可以直接在 HTML 標籤中使用，也可以通過 JavaScript 為元素添加事件監聽器。以下是兩種常見的使用方式：

#### 1. 直接在 HTML 中使用
```html
<div onmouseover="myFunction()">將滑鼠懸停在我上面</div>
```

#### 2. 使用 JavaScript 添加事件監聽器
```javascript
const element = document.getElementById("myElement");
element.addEventListener("mouseover", myFunction);
```

### 詳細說明
- `onmouseover` 事件觸發時，會傳遞一個事件對象，這個對象包含了事件的各種屬性和方法，能夠提供事件發生時的上下文信息。
- 這個事件是對 `onmouseout` 事件的對應，即當滑鼠指標離開元素時，`onmouseout` 事件會被觸發。

## 範例
以下是幾個 `onmouseover` 事件的基本使用範例：

### 範例 1: 變更顏色
```html
<!DOCTYPE html>
<html>
<head>
  <title>onmouseover 範例</title>
  <style>
    #myElement {
      width: 200px;
      height: 100px;
      background-color: lightblue;
      text-align: center;
      line-height: 100px;
    }
  </style>
</head>
<body>
  <div id="myElement" onmouseover="this.style.backgroundColor='lightgreen'">滑鼠懸停</div>
</body>
</html>
```

### 範例 2: 顯示提示
```html
<!DOCTYPE html>
<html>
<head>
  <title>onmouseover 提示範例</title>
</head>
<body>
  <button onmouseover="alert('這是提示信息！')">滑鼠懸停我</button>
</body>
</html>
```

## 解釋
- **常見的陷阱**：在使用 `onmouseover` 時，要注意事件的冒泡行為，可能會導致意外的觸發。如果元素內部還有其他可交互元素，滑鼠移動到這些元素上時也會觸發 `onmouseover`。
- **性能考量**：如果在 `onmouseover` 事件中執行複雜的計算或 DOM 操作，可能會影響性能。因此，應儘量簡化事件處理函數內的邏輯。
- **可訪問性**：考慮到可訪問性，建議為所有用於 `onmouseover` 的效果提供適當的替代方案，例如鍵盤操作方式，讓所有用戶都能享受完整的體驗。

## 總結
`onmouseover` 事件用於處理滑鼠指標進入 HTML 元素時的行為，能夠提升網頁的交互性和用戶體驗。