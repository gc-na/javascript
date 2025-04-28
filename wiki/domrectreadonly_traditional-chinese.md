<!--
Meta Description: # DOMRectReadOnly：JavaScript 中的不可變矩形物件 ## 概述 `DOMRectReadOnly` 是一個在 JavaScript 中用於描述矩形的物件，主要用於提供元素的邊界框（bounding box）資訊。此物件提供了矩形的各個屬性，例如寬度、高度和位置等，且其屬性為...
Meta Keywords: domrectreadonly, getboundingclientrect, rect, html, element
-->

# DOMRectReadOnly：JavaScript 中的不可變矩形物件

## 概述
`DOMRectReadOnly` 是一個在 JavaScript 中用於描述矩形的物件，主要用於提供元素的邊界框（bounding box）資訊。此物件提供了矩形的各個屬性，例如寬度、高度和位置等，且其屬性為唯讀，無法被修改。

## 文件說明
`DOMRectReadOnly` 物件的目的在於提供一個簡單的方式來獲取 HTML 元素的幾何資訊。它包含以下屬性：

- `x`：矩形的左上角 x 坐標。
- `y`：矩形的左上角 y 坐標。
- `width`：矩形的寬度。
- `height`：矩形的高度。
- `top`：矩形的上邊界 y 坐標。
- `right`：矩形的右邊界 x 坐標。
- `bottom`：矩形的下邊界 y 坐標。
- `left`：矩形的左邊界 x 坐標。

這些屬性都是計算後的值，通常用於獲取元素的顯示位置和尺寸，特別是在進行動畫或碰撞檢測時非常有用。

### 使用方法
`DOMRectReadOnly` 通常由 `getBoundingClientRect()` 方法返回。這個方法是 `Element` 介面的成員，返回當前元素的邊界框資訊。

```javascript
const element = document.getElementById('myElement');
const rect = element.getBoundingClientRect();
```

## 範例
以下是如何使用 `DOMRectReadOnly` 的基本範例：

```html
<!DOCTYPE html>
<html lang="zh-Hant">
<head>
    <meta charset="UTF-8">
    <title>DOMRectReadOnly 範例</title>
    <style>
        #myElement {
            width: 100px;
            height: 50px;
            background-color: lightblue;
            position: relative;
        }
    </style>
</head>
<body>
    <div id="myElement"></div>
    <script>
        const element = document.getElementById('myElement');
        const rect = element.getBoundingClientRect();
        console.log('X:', rect.x);
        console.log('Y:', rect.y);
        console.log('Width:', rect.width);
        console.log('Height:', rect.height);
    </script>
</body>
</html>
```

## 說明
在使用 `DOMRectReadOnly` 時，需要注意以下幾點：

1. **唯讀屬性**：`DOMRectReadOnly` 的所有屬性都是唯讀的，這意味著不能通過這個物件改變矩形的值，必須通過調用 `getBoundingClientRect()` 方法來獲取最新的邊界框資訊。
  
2. **座標系統**：`getBoundingClientRect()` 返回的座標是相對於視窗（viewport）的，若需要相對於文檔（document），需要進行額外的計算。

3. **滾動影響**：在滾動頁面時，`getBoundingClientRect()` 返回的值會隨著頁面滾動而變化。這一點在進行動態布局時需要特別留意。

## 總結
`DOMRectReadOnly` 是一個提供元素邊界框資訊的唯讀物件，常用於網頁元素的幾何計算和布局調整。