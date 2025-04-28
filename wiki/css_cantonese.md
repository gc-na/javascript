<!--
Meta Description: # CSS 與 JavaScript 的關係：一個全面指南 ## 簡介 CSS（層疊樣式表）是用來描述 HTML 文件外觀的樣式語言。JavaScript 作為一種強大的編程語言，能夠動態操控 CSS，讓網頁設計更加靈活和互動。 ## 文件說明 CSS 的主要目的是為了控制網頁的佈局和設計，而 Ja...
Meta Keywords: css, javascript, html, myelement, document
-->

# CSS 與 JavaScript 的關係：一個全面指南

## 簡介
CSS（層疊樣式表）是用來描述 HTML 文件外觀的樣式語言。JavaScript 作為一種強大的編程語言，能夠動態操控 CSS，讓網頁設計更加靈活和互動。

## 文件說明
CSS 的主要目的是為了控制網頁的佈局和設計，而 JavaScript 則可以通過 DOM（文檔物件模型）來改變 CSS 樣式。這兩者的結合使得開發者能夠創建動態和響應式的用戶界面，並且可以在用戶與網頁互動時即時更新樣式。

### 使用方法
JavaScript 可以通過以下幾種方式來操作 CSS：

1. **直接修改樣式屬性**：
   ```javascript
   document.getElementById("myElement").style.color = "red";
   ```

2. **添加/移除 CSS 類別**：
   ```javascript
   document.getElementById("myElement").classList.add("new-class");
   document.getElementById("myElement").classList.remove("old-class");
   ```

3. **使用 CSS 變數**：
   ```javascript
   document.documentElement.style.setProperty('--main-color', 'blue');
   ```

## 示例
### 直接修改樣式
```html
<!DOCTYPE html>
<html>
<head>
    <title>CSS 與 JavaScript 示例</title>
</head>
<body>
    <div id="myElement">這是一個測試元素</div>
    <button onclick="changeColor()">改變顏色</button>

    <script>
        function changeColor() {
            document.getElementById("myElement").style.color = "green";
        }
    </script>
</body>
</html>
```

### 添加和移除類別
```html
<!DOCTYPE html>
<html>
<head>
    <style>
        .highlight {
            background-color: yellow;
        }
    </style>
</head>
<body>
    <div id="myElement">這是一個測試元素</div>
    <button onclick="toggleHighlight()">切換高亮</button>

    <script>
        function toggleHighlight() {
            document.getElementById("myElement").classList.toggle("highlight");
        }
    </script>
</body>
</html>
```

## 解釋
在使用 JavaScript 操作 CSS 時，開發者常常會遇到一些常見的陷阱。例如，當使用 `style` 屬性時，需要確保屬性名稱是駝峰式（例如 `backgroundColor` 而非 `background-color`）。此外，對於動態變化的樣式，過度使用 JavaScript 可能會導致性能問題，因此應謹慎使用。

## 簡短總結
JavaScript 能夠動態操控 CSS，為網頁設計增添互動性和靈活性。