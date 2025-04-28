<!--
Meta Description: # MediaQueryList：JavaScript中的媒介查詢列表 ## 概要 `MediaQueryList` 是一個 JavaScript 介面，用於監聽和操作媒介查詢的狀態，從而能夠根據不同的顯示條件（如螢幕大小、解析度等）動態改變網頁的樣式或行為。 ## 文檔 `MediaQueryLi...
Meta Keywords: mediaquerylist, javascript, addlistener, matches, const
-->

# MediaQueryList：JavaScript中的媒介查詢列表

## 概要
`MediaQueryList` 是一個 JavaScript 介面，用於監聽和操作媒介查詢的狀態，從而能夠根據不同的顯示條件（如螢幕大小、解析度等）動態改變網頁的樣式或行為。

## 文檔
`MediaQueryList` 主要用於檢查媒介查詢的條件是否成立。當你需要根據設備的特性（例如螢幕的寬度、高度或解析度）來調整網頁內容時，這個介面非常有用。

### 主要功能
- **創建媒介查詢**：透過 `window.matchMedia()` 方法創建 `MediaQueryList` 對象。
- **監聽變更**：可以利用 `addListener()` 和 `removeListener()` 方法來監聽媒介查詢狀態的變化。
- **查詢狀態**：使用 `matches` 屬性判斷當前媒介查詢是否符合。

### 使用方法
```javascript
// 創建一個媒介查詢列表
const mediaQueryList = window.matchMedia('(max-width: 600px)');

// 判斷媒介查詢是否符合
if (mediaQueryList.matches) {
  console.log('螢幕寬度小於或等於600px');
}

// 監聽媒介查詢的變化
const handleMediaChange = (event) => {
  if (event.matches) {
    console.log('媒介查詢符合條件');
  } else {
    console.log('媒介查詢不符合條件');
  }
};

mediaQueryList.addListener(handleMediaChange);
```

## 範例
### 基本用法
以下是一個簡單的例子，展示如何使用 `MediaQueryList` 來監聽螢幕寬度的變化：

```javascript
const mq = window.matchMedia('(min-width: 800px)');

const updateLayout = (event) => {
  if (event.matches) {
    document.body.style.backgroundColor = 'lightblue'; // 螢幕寬度大於800px
  } else {
    document.body.style.backgroundColor = 'lightcoral'; // 螢幕寬度小於800px
  }
};

// 初始檢查
updateLayout(mq);

// 監聽變化
mq.addListener(updateLayout);
```

## 解釋
在使用 `MediaQueryList` 時，有幾個注意事項：
- **性能考量**：頻繁的 DOM 操作可能影響性能，應適度使用媒介查詢。
- **事件移除**：使用完畢後，應移除監聽器，以避免記憶體洩漏。
- **相容性**：部分舊版瀏覽器可能不支持 `addListener()`，建議使用 `addEventListener()` 替代。

## 單行總結
`MediaQueryList` 是 JavaScript 中用於檢查和監聽媒介查詢狀態的強大工具，讓開發者能夠更靈活地設計響應式網頁。