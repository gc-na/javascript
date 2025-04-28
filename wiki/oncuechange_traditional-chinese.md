<!--
Meta Description: # oncuechange 事件在 JavaScript 中的應用 ## 簡介 `oncuechange` 是一個 JavaScript 事件，專門用於處理媒體元素（如 `<video>` 和 `<audio>`）中的字幕或描述性文本的變化。這個事件在媒體播放時非常有用，特別是在需要即時反應字幕變更...
Meta Keywords: video, oncuechange, javascript, activecues, addeventlistener
-->

# oncuechange 事件在 JavaScript 中的應用

## 簡介
`oncuechange` 是一個 JavaScript 事件，專門用於處理媒體元素（如 `<video>` 和 `<audio>`）中的字幕或描述性文本的變化。這個事件在媒體播放時非常有用，特別是在需要即時反應字幕變更的情境下。

## 文檔
### 目的
`oncuechange` 事件的主要目的是在媒體播放過程中，當字幕或描述性文本發生變化時觸發相應的回調函數。這使得開發者可以在字幕顯示時執行特定操作，例如更新用戶界面或記錄用戶行為。

### 使用方式
這個事件可以通過 JavaScript 的事件監聽器來捕獲。可以將事件直接指定在媒體元素上，或者通過 `addEventListener` 方法來添加。

#### 事件語法
```javascript
mediaElement.oncuechange = function() {
    // 事件處理邏輯
};
```

或者使用事件監聽器：
```javascript
mediaElement.addEventListener('cuechange', function() {
    // 事件處理邏輯
});
```

### 參數
- `mediaElement`：一個 HTMLMediaElement（如 `<video>` 或 `<audio>`），在該元素中監聽 `oncuechange` 事件。

## 示例
### 基本用法
以下是一個簡單的例子，展示如何使用 `oncuechange` 事件來獲取當前顯示的字幕：

```html
<video id="video" controls>
    <source src="movie.mp4" type="video/mp4">
    <track src="subs_en.vtt" kind="subtitles" srclang="en" label="English">
    Your browser does not support HTML5 video.
</video>

<script>
    const video = document.getElementById('video');

    video.addEventListener('cuechange', function() {
        const activeCues = video.textTracks[0].activeCues;
        if (activeCues.length > 0) {
            console.log('當前字幕:', activeCues[0].text);
        }
    });
</script>
```

## 解釋
### 常見問題
1. **事件不觸發**：確保媒體元素中已正確添加字幕檔案，且該檔案格式支持。若無有效字幕，則 `oncuechange` 事件不會被觸發。
   
2. **多個字幕檔案**：若媒體元素中有多個字幕檔，請確認正確訪問所需的 `textTracks`，並使用相應的索引來獲取活動字幕。

3. **瀏覽器兼容性**：雖然大多數現代瀏覽器都支持 `oncuechange` 事件，仍建議在開發過程中測試不同瀏覽器的行為。

## 總結
`oncuechange` 是一個非常實用的事件，用於即時響應媒體播放過程中的字幕變化，幫助開發者提升用戶體驗。