<!--
Meta Description: # DOMPoint：JavaScript 中的平面点对象 ## 概要 DOMPoint 是一個用於表示二維或三維空間中點的 JavaScript 物件，常用於圖形學和計算幾何中。它允許開發者方便地操作和計算點的坐標和相關屬性。 ## 文檔 ### 目的 DOMPoint 提供了一種簡單的方法來表示...
Meta Keywords: dompoint, new, let, javascript, point2d
-->

# DOMPoint：JavaScript 中的平面点对象

## 概要
DOMPoint 是一個用於表示二維或三維空間中點的 JavaScript 物件，常用於圖形學和計算幾何中。它允許開發者方便地操作和計算點的坐標和相關屬性。

## 文檔
### 目的
DOMPoint 提供了一種簡單的方法來表示和操作空間中的點，尤其是在處理畫布（Canvas）和 SVG（可縮放向量圖形）時特別有用。它支援二維和三維坐標系，並能夠輕鬆進行點的轉換和計算。

### 用法
DOMPoint 可以通過 `new DOMPoint()` 構造函數來創建，並可接受一系列參數來初始化點的坐標。

```javascript
let point2D = new DOMPoint(10, 20);
let point3D = new DOMPoint(10, 20, 30, 1);
```

### 參數
- `x` (數字): 點的 X 坐標。
- `y` (數字): 點的 Y 坐標。
- `z` (數字，可選): 點的 Z 坐標，默認為 0。
- `w` (數字，可選): 齊次坐標，默認為 1。

### 方法
- `DOMPoint.fromPoint()`: 從另一個點創建一個新的 DOMPoint。
- `DOMPoint.matrixTransform()`: 將點應用於矩陣變換，返回新的 DOMPoint。

## 示例
### 基本使用示例
```javascript
// 創建一個二維點
let point2D = new DOMPoint(5, 10);
console.log(point2D); // DOMPoint { x: 5, y: 10, z: 0, w: 1 }

// 創建一個三維點
let point3D = new DOMPoint(5, 10, 15);
console.log(point3D); // DOMPoint { x: 5, y: 10, z: 15, w: 1 }

// 使用 matrixTransform 方法
let matrix = new DOMMatrix(); // 創建一個單位矩陣
let transformedPoint = point2D.matrixTransform(matrix);
console.log(transformedPoint); // DOMPoint { x: 5, y: 10, z: 0, w: 1 }
```

## 解釋
使用 DOMPoint 時，開發者應注意以下幾點：
- 確保在創建 DOMPoint 時正確設置坐標，特別是在處理三維點時。
- 使用 `matrixTransform` 方法時，需傳入有效的 DOMMatrix 對象，以確保轉換的正確性。
- DOMPoint 的 `w` 屬性在某些場合可以影響計算，特別是在涉及到透視變換時。

## 一句話總結
DOMPoint 是用於表示和操作二維或三維空間中點的 JavaScript 對象，特別適合於圖形學應用。