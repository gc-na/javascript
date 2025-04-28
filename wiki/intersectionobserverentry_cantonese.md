<!--
Meta Description: # IntersectionObserverEntry：JavaScript 的觀察者條目 ## 簡介 `IntersectionObserverEntry` 是一個用於追蹤一個元素與其父容器（或視口）交集狀態的 JavaScript 物件。這個物件提供了進一步了解元素何時進入或離開視口的能力，對於...
Meta Keywords: intersectionobserverentry, intersectionobserver, target, entry, javascript
-->

# IntersectionObserverEntry：JavaScript 的觀察者條目

## 簡介
`IntersectionObserverEntry` 是一個用於追蹤一個元素與其父容器（或視口）交集狀態的 JavaScript 物件。這個物件提供了進一步了解元素何時進入或離開視口的能力，對於實現懶加載、動畫效果及無限滾動等功能非常有用。

## 文件說明
`IntersectionObserverEntry` 主要用於 `IntersectionObserver` API。當觀察的元素進入或離開視口時，該 API 會返回一個 `IntersectionObserverEntry` 物件，該物件提供以下屬性：

- **boundingClientRect**: 一個 DOMRectReadOnly 物件，表示元素的邊界框相對於視口的位置。
- **intersectionRatio**: 一個數字，表示元素與視口交集的比例，範圍從 0 到 1。
- **intersectionRect**: 一個 DOMRectReadOnly 物件，表示元素與視口的交集部分。
- **isIntersecting**: 一個布林值，表示元素是否在視口內。
- **rootBounds**: 一個 DOMRectReadOnly 物件，表示觀察根的邊界框。
- **target**: 被觀察的目標元素。

### 用途
`IntersectionObserverEntry` 使開發者能夠有效地監控元素的可見性，從而提升網站的性能和用戶體驗。

## 範例
以下是如何使用 `IntersectionObserverEntry` 的基本範例：

```javascript
// 創建一個 IntersectionObserver
const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
        if (entry.isIntersecting) {
            console.log('元素進入視口:', entry.target);
        } else {
            console.log('元素離開視口:', entry.target);
        }
    });
});

// 觀察目標元素
const targetElement = document.querySelector('.target');
observer.observe(targetElement);
```

在上面的範例中，當 `.target` 元素進入或離開視口時，將會在控制台輸出相應的消息。

## 解釋
在使用 `IntersectionObserverEntry` 時，開發者應注意以下幾點：

- **性能考量**: 使用 `IntersectionObserver` 來替代傳統的滾動事件檢測，可以有效減少性能開銷，因為它在瀏覽器的空閒時間執行。
- **多次觸發**: 當元素在視口內部移動時，可能會多次觸發 `isIntersecting` 的變化，這需要謹慎處理，以避免過多的計算或操作。
- **支持性**: 確保在使用前檢查瀏覽器的支持情況，因為並非所有舊版本的瀏覽器都支持 `IntersectionObserver`。

## 總結
`IntersectionObserverEntry` 是一個強大的工具，能方便開發者追蹤元素的可見性狀態，並為用戶提供更流暢的瀏覽體驗。