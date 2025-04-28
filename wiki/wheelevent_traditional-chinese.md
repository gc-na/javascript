<!--
Meta Description: # WheelEvent：JavaScript 的滾輪事件 ## 摘要 WheelEvent 是一種在 JavaScript 中處理滾輪操作的事件。它提供了使用者在使用滑鼠滾輪、觸控板或其他滾輪裝置時的詳細資訊。 ## 文檔 ### 目的 WheelEvent 旨在捕捉和處理與滾動相關的事件，並提供...
Meta Keywords: wheelevent, event, javascript, element, deltax
-->

# WheelEvent：JavaScript 的滾輪事件

## 摘要
WheelEvent 是一種在 JavaScript 中處理滾輪操作的事件。它提供了使用者在使用滑鼠滾輪、觸控板或其他滾輪裝置時的詳細資訊。

## 文檔
### 目的
WheelEvent 旨在捕捉和處理與滾動相關的事件，並提供有關滾動的方向、距離和速度等資訊。這對於開發互動式網頁應用程式時非常重要，尤其是在需要自定義滾動行為的場景中。

### 使用
WheelEvent 事件可通過在 DOM 元素上添加事件監聽器來使用。當滑鼠滾輪或其他滾動裝置被操作時，會觸發這些事件。

#### 語法
```javascript
element.addEventListener('wheel', function(event) {
    // 處理滾輪事件
});
```

### 屬性
- **deltaX**: 滾動的水平距離，正值表示向右滾動，負值表示向左滾動。
- **deltaY**: 滾動的垂直距離，正值表示向下滾動，負值表示向上滾動。
- **deltaZ**: 在某些設備上，垂直滾動的第三維度。
- **deltaMode**: 表示 `deltaX`、`deltaY` 和 `deltaZ` 的單位，通常為像素（0）、行（1）或頁面（2）。

## 範例
### 基本使用範例
以下是一個簡單的範例，展示如何使用 WheelEvent 來捕捉滾動事件並顯示滾動距離。

```javascript
const element = document.getElementById('scrollable');

element.addEventListener('wheel', function(event) {
    console.log(`水平滾動: ${event.deltaX}, 垂直滾動: ${event.deltaY}`);
    // 防止頁面滾動
    event.preventDefault();
});
```

## 解釋
### 常見陷阱
- **事件預設行為**: 在滾動事件中，通常需要調用 `event.preventDefault()` 來防止頁面滾動，這對於自定義滾動行為非常重要。
- **多個事件監聽器**: 如果為同一元素添加多個滾輪事件監聽器，可能會導致性能問題，建議合併邏輯或移除不必要的監聽器。
- **設備相容性**: 滾輪事件在不同設備上的表現可能有所不同，開發者應該測試在各種設備上的行為。

## 一句總結
WheelEvent 使開發者能夠精確控制和響應使用者的滾動行為，從而提升網頁的互動性和使用體驗。