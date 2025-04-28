<!--
Meta Description: # onscrollsnapchange：JavaScript 中的滾動快照變更事件 ## 簡介 `onscrollsnapchange` 是一個在滾動快照變更時觸發的事件，主要用於提升用戶體驗，特別是在帶有滾動快照的容器中。此事件可以幫助開發者監控用戶的滾動行為，進而執行相應的操作或效果。 ## ...
Meta Keywords: scroll, onscrollsnapchange, container, div, snap
-->

# onscrollsnapchange：JavaScript 中的滾動快照變更事件

## 簡介
`onscrollsnapchange` 是一個在滾動快照變更時觸發的事件，主要用於提升用戶體驗，特別是在帶有滾動快照的容器中。此事件可以幫助開發者監控用戶的滾動行為，進而執行相應的操作或效果。

## 文件說明
`onscrollsnapchange` 事件是當使用者滾動一個支持快照滾動的容器時，當快照位置改變時觸發的事件。這個事件通常與 CSS 的 `scroll-snap-type` 和 `scroll-snap-align` 屬性一起使用，以實現平滑的滾動效果。

### 目的
- 監控滾動快照的變更。
- 提供用戶交互反饋。
- 觸發動畫或效果，提升用戶體驗。

### 使用方式
要使用 `onscrollsnapchange` 事件，需在支持快照滾動的容器上添加事件監聽器。以下是基本的語法範例：

```javascript
const container = document.querySelector('.scroll-container');

container.onscrollsnapchange = function(event) {
    console.log('滾動快照已變更！');
};
```

## 範例
以下是使用 `onscrollsnapchange` 的基本示例：

```html
<!DOCTYPE html>
<html lang="zh-Hant">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>滾動快照變更事件示範</title>
    <style>
        .scroll-container {
            height: 200px;
            overflow-y: scroll;
            scroll-snap-type: y mandatory;
        }
        .scroll-item {
            height: 100px;
            scroll-snap-align: start;
            border: 1px solid black;
            margin: 10px 0;
        }
    </style>
</head>
<body>
    <div class="scroll-container">
        <div class="scroll-item">項目 1</div>
        <div class="scroll-item">項目 2</div>
        <div class="scroll-item">項目 3</div>
    </div>

    <script>
        const container = document.querySelector('.scroll-container');
        
        container.onscrollsnapchange = function() {
            console.log('當前滾動快照已變更！');
        };
    </script>
</body>
</html>
```

## 說明
### 常見陷阱
- **不支持的瀏覽器**：並非所有瀏覽器都支持 `onscrollsnapchange` 事件，開發者應檢查相容性並考慮後備方案。
- **性能影響**：在滾動過程中頻繁觸發事件可能會影響性能，建議使用防抖或節流技術來優化事件處理。

### 額外說明
- `onscrollsnapchange` 事件不會在每個滾動位置都觸發，只會在快照點之間切換時觸發。
- 確保容器的 CSS 屬性正確設置，否則可能無法觸發此事件。

## 一句總結
`onscrollsnapchange` 是一個用於監控快照滾動變更的事件，能夠增強用戶互動和體驗。