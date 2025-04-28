<!--
Meta Description: # DOMRectList：JavaScript 中的矩形列表對象 ## 簡介 DOMRectList 是一個在 JavaScript 中用於表示一組 DOMRect 物件的集合，這些物件通常用於描述元素的邊界矩形。這使得開發人員可以有效地處理和操作這些矩形的幾何屬性。 ## 文檔 ### 目的 D...
Meta Keywords: domrectlist, javascript, domrect, rects, getclientrects
-->

# DOMRectList：JavaScript 中的矩形列表對象

## 簡介
DOMRectList 是一個在 JavaScript 中用於表示一組 DOMRect 物件的集合，這些物件通常用於描述元素的邊界矩形。這使得開發人員可以有效地處理和操作這些矩形的幾何屬性。

## 文檔
### 目的
DOMRectList 主要用於存儲和操作多個 DOMRect 物件，這些物件通常由元素的邊界框（bounding box）計算得出。這在進行碰撞檢測、動畫效果和布局計算時非常有用。

### 用法
DOMRectList 是一個類似於陣列的對象，提供了一些方法和屬性來訪問和操作集合中的 DOMRect 物件。通常，這個對象是通過使用 `getClientRects()` 方法獲取的，該方法會返回一個 DOMRectList 實例。

### 詳細說明
- **屬性**：
  - `length`：返回 DOMRectList 中的 DOMRect 數量。
  
- **方法**：
  - `item(index)`：返回指定索引的 DOMRect 物件。

### 獲取 DOMRectList
要獲取 DOMRectList，您可以使用以下方法：
```javascript
const rects = element.getClientRects();
```

## 示例
以下是如何使用 DOMRectList 的基本示例：

```javascript
// 獲取元素
const element = document.getElementById('myElement');

// 獲取元素的邊界矩形列表
const rects = element.getClientRects();

// 遍歷 DOMRectList
for (let i = 0; i < rects.length; i++) {
    console.log(`矩形 ${i}：`, rects.item(i));
}
```

## 解釋
- **常見陷阱**：
  - 確保在元素渲染到 DOM 後再調用 `getClientRects()`，否則可能會得到空的 DOMRectList。
  
- **注意事項**：
  - DOMRectList 是類似於陣列的對象，但不是真正的陣列，某些數組方法（如 `forEach`）無法直接使用。
  - 若需要使用陣列的方法，可以將其轉換為陣列：
    ```javascript
    const rectArray = Array.from(rects);
    ```

## 一句總結
DOMRectList 是一個在 JavaScript 中用於表示一組 DOMRect 物件的集合，便於開發人員操作和處理元素的邊界矩形。