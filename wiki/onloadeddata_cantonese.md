<!--
Meta Description: # onloadeddata 事件：JavaScript 中的媒體加載事件 ## 概述 `onloadeddata` 是一個 JavaScript 事件，主要用於媒體元素（如 `<audio>` 和 `<video>`）在數據加載完成後的處理。當媒體數據已經加載，可以開始播放時，這個事件就會被觸發。...
Meta Keywords: video, onloadeddata, javascript, audio, addeventlistener
-->

# onloadeddata 事件：JavaScript 中的媒體加載事件

## 概述
`onloadeddata` 是一個 JavaScript 事件，主要用於媒體元素（如 `<audio>` 和 `<video>`）在數據加載完成後的處理。當媒體數據已經加載，可以開始播放時，這個事件就會被觸發。

## 文檔
### 目的
`onloadeddata` 事件可以讓開發者在媒體數據成功加載後執行特定的操作，例如更新用戶界面或啟動播放。

### 使用方法
這個事件可以通過 JavaScript 的事件監聽器來使用，具體步驟如下：

1. 獲取媒體元素的引用，例如 `<video>` 或 `<audio>`。
2. 使用 `.addEventListener()` 方法來監聽 `onloadeddata` 事件。
3. 在事件處理器中編寫相應的邏輯。

### 詳細信息
- **事件類型**：`Event`
- **適用元素**：`<audio>` 和 `<video>` 標籤
- **兼容性**：大多數現代瀏覽器均支持該事件。

## 示例
以下是使用 `onloadeddata` 事件的基本示例：

```html
<video id="myVideo" controls>
    <source src="movie.mp4" type="video/mp4">
    Your browser does not support the video tag.
</video>

<script>
    const video = document.getElementById('myVideo');
    
    video.addEventListener('loadeddata', function() {
        console.log('媒體數據已加載，可以開始播放了！');
        video.play();
    });
</script>
```

## 解釋
### 常見陷阱
- `onloadeddata` 事件僅在媒體數據成功加載後觸發。如果媒體文件無法加載，則不會觸發此事件。
- 有些開發者可能會錯誤地使用 `onload` 事件，這通常用於圖片等其他元素，而不是媒體元素。

### 注意事項
- 這個事件不保證在所有數據都加載完成後觸發，因此需要考慮到可能的網絡延遲或數據流問題。
- 在使用 `video.play()` 之前，最好檢查媒體的就緒狀態，以避免因為播放時介面未就緒而造成的錯誤。

## 一句話總結
`onloadeddata` 是一個關鍵的媒體事件，允許開發者在音頻或視頻數據加載後進行後續操作。