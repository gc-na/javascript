<!--
Meta Description: # HTMLHRElement 在 JavaScript 中的應用 ## 摘要 HTMLHRElement 是一個代表 HTML `<hr>` 標籤的接口，這個標籤通常用於在網頁中創建水平分隔線。它在 JavaScript 中的操作使得開發者能夠動態修改頁面結構和樣式。 ## 文檔 ### 目的 H...
Meta Keywords: javascript, htmlhrelement, document, hrelement, setattribute
-->

# HTMLHRElement 在 JavaScript 中的應用

## 摘要
HTMLHRElement 是一個代表 HTML `<hr>` 標籤的接口，這個標籤通常用於在網頁中創建水平分隔線。它在 JavaScript 中的操作使得開發者能夠動態修改頁面結構和樣式。

## 文檔
### 目的
HTMLHRElement 的主要目的是表示一個水平線，該線用來分隔內容，通常用於視覺上劃分不同的部分。使用 JavaScript 操作 HTMLHRElement 讓開發者能夠更靈活地控制其屬性和樣式。

### 用法
在 JavaScript 中，開發者可以通過 DOM 操作來創建和修改 HTMLHRElement。這可以使用 `document.createElement` 方法來創建 `<hr>` 標籤，或通過選擇現有的 `<hr>` 元素來進行操作。

#### 常用屬性
- `width`: 設定水平線的寬度。
- `size`: 設定線的厚度。
- `color`: 設定線的顏色（在某些瀏覽器中可能不支持）。

### 詳細說明
HTMLHRElement 的創建和修改可以通過以下方法進行：

1. **創建新的 `<hr>` 元素**:
   ```javascript
   const hrElement = document.createElement('hr');
   ```

2. **添加至 DOM**:
   ```javascript
   document.body.appendChild(hrElement);
   ```

3. **設置屬性**:
   ```javascript
   hrElement.setAttribute('width', '50%');
   hrElement.setAttribute('size', '2');
   hrElement.style.color = 'blue';
   ```

## 示例
### 基本用法
以下是一個簡單的示例，展示如何使用 JavaScript 創建和設置一個 `<hr>` 元素：

```javascript
const hr = document.createElement('hr');
hr.setAttribute('width', '80%');
hr.setAttribute('size', '5');
document.body.appendChild(hr);
```

### 動態改變樣式
可以輕鬆地為現有的 `<hr>` 元素添加樣式變化：

```javascript
const hr = document.querySelector('hr');
hr.style.backgroundColor = 'red';
hr.style.height = '3px';
```

## 說明
- **常見問題**: 在某些情況下，屬性如 `color` 可能不會在所有瀏覽器中正確顯示，因此建議使用 CSS 來定義樣式。
- **注意事項**: 確保在操作 DOM 時，目標元素已經存在，否則可能會遇到錯誤。

## 一句總結
HTMLHRElement 讓開發者能夠通過 JavaScript 動態創建和管理水平分隔線，增強網頁的可視化效果。