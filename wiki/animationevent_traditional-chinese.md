<!--
Meta Description: # AnimationEvent 在 JavaScript 中的應用 ## 摘要 AnimationEvent 是一個用於處理 CSS 動畫事件的 JavaScript 事件，允許開發者在動畫開始、結束或重置時執行特定操作。 ## 文檔 ### 目的 AnimationEvent 旨在提供一種方式來...
Meta Keywords: animationevent, css, event, javascript, box
-->

# AnimationEvent 在 JavaScript 中的應用

## 摘要
AnimationEvent 是一個用於處理 CSS 動畫事件的 JavaScript 事件，允許開發者在動畫開始、結束或重置時執行特定操作。

## 文檔
### 目的
AnimationEvent 旨在提供一種方式來偵測 CSS 動畫的狀態變化，幫助開發者在動畫的不同階段執行功能，例如監聽動畫的開始、結束或中斷。

### 使用方法
在 JavaScript 中，AnimationEvent 事件可以通過以下方式來偵測：

1. **監聽事件**：使用 `addEventListener` 方法來監聽 `animationstart`、`animationend` 和 `animationiteration` 事件。
2. **事件屬性**：AnimationEvent 物件包含多個有用的屬性，例如：
   - `animationName`：返回觸發的動畫名稱。
   - `elapsedTime`：返回從動畫開始到事件發生的時間（以秒為單位）。

### 事件類型
- `animationstart`：當動畫開始時觸發。
- `animationend`：當動畫結束時觸發。
- `animationiteration`：當動畫重複播放時觸發。

## 範例
### 基本用法
以下是使用 AnimationEvent 的基本範例：

```javascript
// 獲取要添加事件監聽的元素
const box = document.querySelector('.box');

// 監聽動畫開始事件
box.addEventListener('animationstart', (event) => {
    console.log(`動畫開始: ${event.animationName}`);
});

// 監聽動畫結束事件
box.addEventListener('animationend', (event) => {
    console.log(`動畫結束: ${event.animationName}, 經過時間: ${event.elapsedTime}秒`);
});

// 監聽動畫重複事件
box.addEventListener('animationiteration', (event) => {
    console.log(`動畫重複: ${event.animationName}`);
});
```

### CSS 動畫範例
在 HTML 中添加一個 CSS 動畫：

```css
.box {
    width: 100px;
    height: 100px;
    background-color: red;
    animation: exampleAnimation 2s infinite;
}

@keyframes exampleAnimation {
    from { transform: translateY(0); }
    to { transform: translateY(100px); }
}
```

## 解釋
### 常見問題
- **事件不觸發**：確保 CSS 動畫已正確設置，並且 JavaScript 代碼在 DOM 內容加載完成後執行。
- **性能考量**：過度使用動畫可能影響性能，特別是在移動設備上，應謹慎使用。
- **瀏覽器兼容性**：大多數現代瀏覽器支持 AnimationEvent，但在某些舊版本中可能需要檢查。

## 一句總結
AnimationEvent 是 JavaScript 中用於處理 CSS 動畫狀態變化的重要事件，幫助開發者實現更豐富的交互效果。