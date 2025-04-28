<!--
Meta Description: # onwheel 事件在 JavaScript 中的應用 ## 摘要 `onwheel` 事件是 JavaScript 中專門用於處理滑鼠滾輪操作的事件，提供了一種簡便的方法來偵測和響應使用者的滾動行為。 ## 文檔 ### 目的 `onwheel` 事件用於監聽使用者在網頁上進行滾動操作。它可以...
Meta Keywords: onwheel, event, javascript, deltay, zoomable
-->

# onwheel 事件在 JavaScript 中的應用

## 摘要
`onwheel` 事件是 JavaScript 中專門用於處理滑鼠滾輪操作的事件，提供了一種簡便的方法來偵測和響應使用者的滾動行為。

## 文檔
### 目的
`onwheel` 事件用於監聽使用者在網頁上進行滾動操作。它可以用於各種互動，例如頁面滾動、放大縮小、調整內容等。

### 使用方式
`onwheel` 可以通過直接在 HTML 元素中添加事件屬性或使用 JavaScript 的事件監聽器來實現。以下是基本的語法:

```javascript
element.onwheel = function(event) {
    // 處理滾輪事件
};
```

或使用 `addEventListener` 方法：

```javascript
element.addEventListener('wheel', function(event) {
    // 處理滾輪事件
});
```

### 事件屬性
`onwheel` 事件物件包含以下重要屬性：

- `deltaY`：表示滾輪滾動的垂直距離，正值表示向下滾動，負值表示向上滾動。
- `deltaX`：表示滾輪滾動的水平距離，正值表示向右滾動，負值表示向左滾動。
- `deltaMode`：表示 `deltaY` 和 `deltaX` 的單位，可能的值為 `0`（像素）、`1`（行）、`2`（頁面）。

## 範例
以下是一些基本的使用範例：

### 滾動偵測範例

```html
<div id="scrollable" style="height: 200px; overflow: auto;">
    <p>這是一段可以滾動的內容。</p>
    <p>請使用滑鼠滾輪來滾動此區域。</p>
    <p>這是一段可以滾動的內容。</p>
</div>

<script>
    const scrollable = document.getElementById('scrollable');
    
    scrollable.onwheel = function(event) {
        console.log('滾動量：', event.deltaY);
        event.preventDefault(); // 防止預設滾動行為
    };
</script>
```

### 放大縮小範例

```html
<div id="zoomable" style="width: 200px; height: 200px; background-color: lightblue;">
    滾動以放大或縮小
</div>

<script>
    const zoomable = document.getElementById('zoomable');
    let scale = 1;

    zoomable.onwheel = function(event) {
        event.preventDefault();
        scale += event.deltaY > 0 ? -0.1 : 0.1; // 根據滾動方向調整縮放比例
        zoomable.style.transform = `scale(${scale})`;
    };
</script>
```

## 解釋
### 常見陷阱和注意事項
- **預設行為**：使用 `event.preventDefault()` 可以防止滾動事件的預設行為，這對於自定義滾動操作尤為重要。
- **滾動速度**：不同的設備（如觸控板和滑鼠）可能導致不同的 `deltaY` 值，需根據需求調整滾動靈敏度。
- **跨瀏覽器相容性**：雖然 `onwheel` 在現代瀏覽器中表現良好，但在某些舊版瀏覽器中可能需要使用 `mousewheel` 或 `DOMMouseScroll` 事件作為後備方案。

## 一句話總結
`onwheel` 事件是 JavaScript 中用於偵測和處理滑鼠滾輪操作的一種強大工具。