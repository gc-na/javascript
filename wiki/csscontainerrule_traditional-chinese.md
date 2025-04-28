<!--
Meta Description: # CSSContainerRule：JavaScript 中的 CSS 容器規則 ## 概述 CSSContainerRule 是一種用於在 JavaScript 中操作 CSS 容器查詢的規則，允許開發者根據容器的大小來應用不同的樣式。這一特性使得響應式設計更加靈活和強大。 ## 文檔 CSSC...
Meta Keywords: csscontainerrule, javascript, stylesheet, style, width
-->

# CSSContainerRule：JavaScript 中的 CSS 容器規則

## 概述
CSSContainerRule 是一種用於在 JavaScript 中操作 CSS 容器查詢的規則，允許開發者根據容器的大小來應用不同的樣式。這一特性使得響應式設計更加靈活和強大。

## 文檔
CSSContainerRule 主要用於定義容器查詢的規則，這些規則可以在容器的尺寸改變時自動應用。這使得開發者能夠根據其父容器的大小來調整樣式，而不僅僅是根據視口大小。

### 定義
CSSContainerRule 的結構如下：
```javascript
let containerRule = new CSSContainerRule(selectorText, style);
```
- **selectorText**: 一個字符串，表示容器查詢的選擇器。
- **style**: 一個 CSSStyleDeclaration 物件，包含要應用的樣式屬性和相應的值。

### 使用
要使用 CSSContainerRule，首先需要創建一個包含容器查詢的 CSS 樣式表，然後通過 JavaScript 對其進行操作。以下是創建和使用 CSSContainerRule 的基本步驟：

1. **創建樣式表**：
   ```javascript
   const styleSheet = document.styleSheets[0];
   ```

2. **添加容器規則**：
   ```javascript
   styleSheet.insertRule('@container (min-width: 500px) { .example { color: blue; } }', styleSheet.cssRules.length);
   ```

3. **查詢和修改容器規則**：
   ```javascript
   const containerRule = styleSheet.cssRules[0];
   containerRule.style.color = 'red';
   ```

## 範例
以下是一個簡單的範例，演示如何使用 CSSContainerRule：
```html
<!DOCTYPE html>
<html lang="zh-Hant">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CSSContainerRule 範例</title>
    <style>
        @container (min-width: 500px) {
            .example {
                color: blue;
            }
        }
        .example {
            color: red;
        }
    </style>
</head>
<body>
    <div class="example">這是一個容器查詢範例。</div>
    <script>
        const styleSheet = document.styleSheets[0];
        styleSheet.insertRule('@container (min-width: 500px) { .example { color: blue; } }', styleSheet.cssRules.length);
    </script>
</body>
</html>
```

## 解釋
在使用 CSSContainerRule 時，開發者需要注意以下幾點：
- **支援性**：不是所有的瀏覽器都支援這個特性，因此在使用前需確認兼容性。
- **性能考量**：過多的容器查詢可能會影響性能，應保持適度。
- **樣式衝突**：當多個樣式規則適用於同一元素時，需注意規則的優先級。

## 一句話總結
CSSContainerRule 是 JavaScript 中用於操作和管理 CSS 容器查詢的強大工具，能有效提升響應式設計的靈活性。