<!--
Meta Description: # TouchList：JavaScript 中的觸控事件列表 ## 概述 TouchList 是一種 JavaScript 物件，用於表示一組觸控點，通常在觸控設備的觸控事件中使用。它提供了一個接口來訪問與觸控相關的數據，如觸控點的數量、位置和狀態。 ## 文檔 ### 目的 TouchList ...
Meta Keywords: touchlist, touches, javascript, changedtouches, length
-->

# TouchList：JavaScript 中的觸控事件列表

## 概述
TouchList 是一種 JavaScript 物件，用於表示一組觸控點，通常在觸控設備的觸控事件中使用。它提供了一個接口來訪問與觸控相關的數據，如觸控點的數量、位置和狀態。

## 文檔
### 目的
TouchList 主要用於處理觸控事件（例如 touchstart、touchmove 和 touchend），幫助開發者獲取和管理觸控點的資訊。這對於創建觸控友好的用戶界面和應用程式至關重要。

### 使用方法
TouchList 由瀏覽器自動生成，當一個觸控事件發生時，相關的觸控點會被添加到 TouchList 中。要訪問 TouchList，可以使用事件對象的 `touches`、`targetTouches` 或 `changedTouches` 屬性。

### 詳細信息
- **touches**: 包含當前屏幕上所有觸控點的 TouchList。
- **targetTouches**: 包含當前觸控目標上的所有觸控點的 TouchList。
- **changedTouches**: 包含最近發生變化的觸控點的 TouchList。

每個 TouchList 都有以下方法和屬性：
- `length`: 返回觸控點的數量。
- `item(index)`: 根據索引返回特定的觸控點物件。
- `forEach(callback)`: 遍歷 TouchList 中的每個觸控點。

## 示例
```javascript
// 監聽觸控事件
document.addEventListener('touchstart', function(event) {
    const touches = event.touches;
    console.log('觸控點數量:', touches.length);
    
    for (let i = 0; i < touches.length; i++) {
        console.log(`觸控點 ${i}:`, touches[i]);
    }
});
```

## 解釋
- **常見問題**:
  - 確保在觸控事件上使用 `event.touches`。如果在非觸控事件上使用，將會返回 undefined。
  - 注意觸控點的數量可能會隨著用戶的操作而變化，特別是在多點觸控的情況下。

- **注意事項**:
  - 手指移動或抬起時，相關的觸控點會從 `touches` 中移除，並添加到 `changedTouches` 中。
  - 在處理觸控事件時，應考慮不同設備的觸控特性，以確保良好的用戶體驗。

## 一句話摘要
TouchList 是一個用於處理和管理觸控事件中觸控點的 JavaScript 物件，對開發觸控友好的應用至關重要。