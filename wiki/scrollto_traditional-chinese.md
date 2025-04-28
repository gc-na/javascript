<!--
Meta Description: # JavaScript 中的 scrollTo：滾動到特定位置的技巧 ## 簡介 `scrollTo` 是一個 JavaScript 方法，用於滾動到指定的元素或位置，提供了一種簡單的方式來改善用戶體驗，尤其是在單頁應用程序或長內容頁面中。 ## 文檔 ### 目的 `scrollTo` 方法用於...
Meta Keywords: scrollto, javascript, window, behavior, smooth
-->

# JavaScript 中的 scrollTo：滾動到特定位置的技巧

## 簡介
`scrollTo` 是一個 JavaScript 方法，用於滾動到指定的元素或位置，提供了一種簡單的方式來改善用戶體驗，尤其是在單頁應用程序或長內容頁面中。

## 文檔
### 目的
`scrollTo` 方法用於控制滾動條的位置，無論是滾動到特定的坐標還是滾動到特定的 HTML 元素。它可以使網頁的視覺交互更加流暢和直觀。

### 使用方法
`scrollTo` 方法可被應用於 `window` 對象或任何具有滾動條的元素。其語法如下：

```javascript
window.scrollTo(x, y);
```

#### 參數
- `x`：目標水平坐標，通常是像素值。
- `y`：目標垂直坐標，通常是像素值。

從 ECMAScript 2015 開始，`scrollTo` 還可以接受一個選項對象，語法如下：

```javascript
window.scrollTo({
  top: y,
  left: x,
  behavior: 'auto' | 'smooth'
});
```

#### 選項
- `top`：目標垂直坐標。
- `left`：目標水平坐標。
- `behavior`：滾動的行為，`auto` 表示瞬間滾動，`smooth` 表示平滑滾動。

## 範例
### 基本用法
1. 瞬間滾動到 (0, 500)：
   ```javascript
   window.scrollTo(0, 500);
   ```

2. 平滑滾動到 (0, 500)：
   ```javascript
   window.scrollTo({
     top: 500,
     left: 0,
     behavior: 'smooth'
   });
   ```

3. 滾動到特定元素：
   ```javascript
   const element = document.getElementById('target-element');
   element.scrollIntoView({ behavior: 'smooth' });
   ```

## 解釋
### 常見問題
- **滾動不工作**：確保元素或窗口已經具有滾動條，否則滾動將不會生效。
- **平滑滾動不兼容**：某些舊版瀏覽器不支持 `behavior: 'smooth'`，在這些情況下，滾動將是瞬間的。
- **坐標問題**：確保提供的坐標在頁面範圍內，否則會導致滾動到無法到達的位置。

## 總結
`scrollTo` 方法提供了一種靈活的方式來控制滾動行為，增強了用戶與網頁的互動體驗。