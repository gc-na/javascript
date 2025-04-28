<!--
Meta Description: # DOMPointReadOnly：JavaScript 中的只讀點物件 ## 概述 DOMPointReadOnly 是一個用於表示二維或三維空間中點的物件，特別是在 Web 開發中的 Canvas 和 SVG 中非常有用。這個物件是只讀的，意味著其屬性無法改變，提供了一種安全的方式來處理坐標數...
Meta Keywords: dompointreadonly, point, console, log, dommatrix
-->

# DOMPointReadOnly：JavaScript 中的只讀點物件

## 概述
DOMPointReadOnly 是一個用於表示二維或三維空間中點的物件，特別是在 Web 開發中的 Canvas 和 SVG 中非常有用。這個物件是只讀的，意味著其屬性無法改變，提供了一種安全的方式來處理坐標數據。

## 文件說明
### 目的
DOMPointReadOnly 的設計目的是為了提供一個不會被意外改變的點物件，適合用於需要精確坐標的場景，例如圖形繪製和動畫。

### 用法
- **創建**: 通常由其他 API 生成，例如 DOMMatrix 的方法。
- **屬性**: 包含 `x`, `y`, `z`, 和 `w` 屬性，分別表示點的 X、Y、Z 坐標以及齊次坐標。

### 詳細說明
- **屬性**:
  - `x`: 返回點在 X 軸上的位置。
  - `y`: 返回點在 Y 軸上的位置。
  - `z`: 返回點在 Z 軸上的位置（在三維空間中）。
  - `w`: 齊次坐標，通常用於計算和轉換。

- **方法**: DOMPointReadOnly 主要是用來讀取點的屬性，並不提供任何方法來修改點的數據。

## 範例
### 基本用法
```javascript
// 通過 DOMMatrix 創建 DOMPointReadOnly
const matrix = new DOMMatrix();
const point = matrix.transformPoint(new DOMPoint(1, 2, 3));

// 訪問點的屬性
console.log(point.x); // 輸出: 1
console.log(point.y); // 輸出: 2
console.log(point.z); // 輸出: 3
console.log(point.w); // 輸出: 1
```

## 解釋
在使用 DOMPointReadOnly 時，開發者需注意以下幾點：
- **只讀性**: 該物件的所有屬性都是只讀的，無法直接修改。
- **生成方式**: 通常需要通過其他方法生成，無法直接用構造函數創建。
- **性能考量**: 由於是只讀物件，能夠提高性能，避免不必要的數據修改。

## 總結
DOMPointReadOnly 是一個專為二維或三維坐標系統設計的只讀點物件，確保坐標數據的穩定性與安全性。