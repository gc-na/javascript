<!--
Meta Description: # TextTrackList：JavaScript 中的文本轨道列表 ## 概述 `TextTrackList` 是一個與 HTML5 媒體元素相關的 JavaScript 接口，用於處理媒體的文本軌道（如字幕和描述）。它提供了一組方法和屬性來訪問和管理媒體元素中的文本軌道。 ## 文檔 ### ...
Meta Keywords: texttracklist, texttracks, video, javascript, length
-->

# TextTrackList：JavaScript 中的文本轨道列表

## 概述
`TextTrackList` 是一個與 HTML5 媒體元素相關的 JavaScript 接口，用於處理媒體的文本軌道（如字幕和描述）。它提供了一組方法和屬性來訪問和管理媒體元素中的文本軌道。

## 文檔
### 目的
`TextTrackList` 的主要目的是允許開發者在媒體播放時動態管理文本軌道，這對於可訪問性和用戶體驗至關重要。

### 使用方法
`TextTrackList` 是由 HTMLMediaElement 的 `textTracks` 屬性返回的，這意味著你需要有一個媒體元素（如 `<video>` 或 `<audio>`）來使用它。

#### 屬性
- **length**: 返回 `TextTrackList` 中文本軌道的數量。
- **item(index)**: 根據索引返回對應的 `TextTrack` 對象。
- **[index]**: 允許通過索引直接訪問文本軌道。

### 例子
以下是使用 `TextTrackList` 的基本示例：

```html
<video id="myVideo" controls>
    <source src="movie.mp4" type="video/mp4">
    <track src="subtitles_en.vtt" kind="subtitles" srclang="en" label="English">
    <track src="subtitles_es.vtt" kind="subtitles" srclang="es" label="Spanish">
    Your browser does not support the video tag.
</video>

<script>
    const video = document.getElementById('myVideo');
    const textTracks = video.textTracks;

    console.log('文本軌道數量:', textTracks.length);

    for (let i = 0; i < textTracks.length; i++) {
        console.log('文本軌道:', textTracks.item(i).label);
    }
</script>
```

### 解釋
在使用 `TextTrackList` 時，開發者需要注意以下幾點：
- 確保媒體元素已正確加載，否則 `textTracks` 可能回傳空列表。
- 在不同瀏覽器中，`TextTrack` 的行為可能有所不同，特別是對於 `kind` 和 `srclang` 的支援。
- 當使用動態創建的文本軌道時，需要確保文本文件的格式正確。

## 總結
`TextTrackList` 是一個強大的工具，允許開發者在 JavaScript 中有效管理多媒體內容中的文本軌道，提升用戶的觀影體驗。