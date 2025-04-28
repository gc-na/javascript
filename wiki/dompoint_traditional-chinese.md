<!--
Meta Description: # DOMPoint：JavaScript 中的二維點對象 ## 簡介 `DOMPoint` 是一個用於表示二維或三維空間中的點的物件，主要用於 Web 開發中的 Canvas 和 SVG 相關操作。它提供了便捷的方式來創建和操作點的坐標。 ## 文檔 `DOMPoint` 是一個可以用來表示一個點...
Meta Keywords: dompoint, javascript, let, new, 預設為
-->

# DOMPoint：JavaScript 中的二維點對象

## 簡介
`DOMPoint` 是一個用於表示二維或三維空間中的點的物件，主要用於 Web 開發中的 Canvas 和 SVG 相關操作。它提供了便捷的方式來創建和操作點的坐標。

## 文檔
`DOMPoint` 是一個可以用來表示一個點的物件，這個點可以在二維或三維空間中進行計算。它是 `DOM` 的一部分，特別是在使用 `Canvas` 和 `SVG` 時非常有用。

### 目的
`DOMPoint` 旨在提供一個簡單的 API 來處理二維和三維坐標，支援坐標轉換、計算以及其他相關操作。

### 使用方法
要使用 `DOMPoint`，可以通過以下方式創建一個新的點：

```javascript
let point = new DOMPoint(x, y, z, w);
```

- `x`：點的 x 坐標，預設為 0。
- `y`：點的 y 坐標，預設為 0。
- `z`：點的 z 坐標，預設為 0（僅在三維空間中使用）。
- `w`：點的同質性坐標，預設為 1。

### 屬性
- `x`：該點在 x 軸上的坐標。
- `y`：該點在 y 軸上的坐標。
- `z`：該點在 z 軸上的坐標（可選）。
- `w`：同質性坐標（可選）。

### 方法
- `matrixTransform(matrix)`：將此點與給定的變換矩陣相乘，返回一個新的 `DOMPoint` 物件。

## 範例
以下是一些使用 `DOMPoint` 的基本範例：

### 創建二維點
```javascript
let point2D = new DOMPoint(10, 20);
console.log(point2D); // DOMPoint { x: 10, y: 20, z: 0, w: 1 }
```

### 創建三維點
```javascript
let point3D = new DOMPoint(10, 20, 30);
console.log(point3D); // DOMPoint { x: 10, y: 20, z: 30, w: 1 }
```

### 使用矩陣變換
```javascript
let point = new DOMPoint(10, 20);
let transformMatrix = new DOMMatrix().translate(5, 5);
let transformedPoint = point.matrixTransform(transformMatrix);
console.log(transformedPoint); // DOMPoint { x: 15, y: 25, z: 0, w: 1 }
```

## 解釋
在使用 `DOMPoint` 時，有一些常見的陷阱和注意事項：

- **同質性坐標**：在大多數情況下，`w` 預設為 1。當進行投影或變換時，確保理解同質性坐標的意義。
- **三維坐標**：如果只需要二維坐標，仍然可以使用 `DOMPoint`，但 `z` 和 `w` 會影響計算結果。
- **矩陣運算**：確保傳遞給 `matrixTransform` 的矩陣是正確的，否則會導致意外的變換結果。

## 一句總結
`DOMPoint` 是 JavaScript 中用於表示和操作二維及三維空間點的強大工具，特別適用於圖形和動畫處理。