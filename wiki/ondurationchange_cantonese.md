<!--
Meta Description: # JavaScript 的 ondurationchange 事件 ## 概述 `ondurationchange` 是一個與媒體元素（如 `<video>` 和 `<audio>`）相關的事件，當媒體的持續時間發生改變時觸發。這通常發生在動態加載或修改媒體的情況下。 ## 文檔 `ondurat...
Meta Keywords: ondurationchange, videoelement, javascript, video, myvideo
-->

# JavaScript 的 ondurationchange 事件

## 概述
`ondurationchange` 是一個與媒體元素（如 `<video>` 和 `<audio>`）相關的事件，當媒體的持續時間發生改變時觸發。這通常發生在動態加載或修改媒體的情況下。

## 文檔
`ondurationchange` 事件主要用於監控媒體元素的持續時間變化。當媒體的持續時間由於某些原因（如串流內容的變更）而改變時，這個事件會被觸發。開發者可以通過監聽這個事件來執行相應的操作，例如更新用戶界面或啟動其他功能。

### 用法
要使用 `ondurationchange` 事件，開發者需要將事件監聽器附加到媒體元素。以下是一個簡單的示例：

```javascript
const videoElement = document.getElementById('myVideo');

videoElement.ondurationchange = function() {
    console.log('媒體持續時間已改變。');
};
```

## 示例
以下是使用 `ondurationchange` 事件的基本示例：

### HTML 代碼
```html
<video id="myVideo" controls>
    <source src="movie.mp4" type="video/mp4">
    您的瀏覽器不支持視頻標籤。
</video>
```

### JavaScript 代碼
```javascript
const videoElement = document.getElementById('myVideo');

videoElement.ondurationchange = function() {
    console.log('新的媒體持續時間是：' + videoElement.duration + ' 秒');
};
```

在這個例子中，當視頻的持續時間改變時，控制台會輸出新的持續時間。

## 解釋
在使用 `ondurationchange` 事件時，開發者需要注意以下幾點：

1. **多次觸發**：這個事件在某些情況下可能被多次觸發，因此需要考慮如何管理事件處理器，避免重複執行相同的代碼。
2. **瀏覽器兼容性**：雖然大多數現代瀏覽器都支持此事件，但在一些舊版本的瀏覽器中可能會存在兼容性問題，因此建議進行測試。
3. **動態內容**：對於動態加載的媒體，`ondurationchange` 將是監控持續時間變化的一個重要手段。

## 單行總結
`ondurationchange` 事件在媒體持續時間改變時觸發，對於處理動態媒體內容非常有用。