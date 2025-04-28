<!--
Meta Description: # TextTrackList：JavaScript中的文本轨道列表 ## 概述 `TextTrackList` 是一个 JavaScript 接口，用于表示与 HTML 视频和音频元素相关联的文本轨道的集合。这些文本轨道包括字幕、说明性文本和章节等，能够为用户提供更好的媒体体验。 ## 文档 ##...
Meta Keywords: texttracklist, texttracks, video, texttrack, label
-->

# TextTrackList：JavaScript中的文本轨道列表

## 概述
`TextTrackList` 是一个 JavaScript 接口，用于表示与 HTML 视频和音频元素相关联的文本轨道的集合。这些文本轨道包括字幕、说明性文本和章节等，能够为用户提供更好的媒体体验。

## 文档
### 目的
`TextTrackList` 的主要目的是提供对媒体元素中可用文本轨道的访问。这些文本轨道可以是不同语言的字幕、描述或章节信息，增强了无障碍性和可用性。

### 使用
`TextTrackList` 可通过访问 HTMLMediaElement 的 `textTracks` 属性获得。以下是 `TextTrackList` 的一些关键特点：

- **属性**：
  - `length`：返回 `TextTrackList` 中包含的文本轨道数量。
  - `item(index)`：返回指定索引位置的 `TextTrack` 对象。
  - `getTrackById(id)`：根据给定的 ID 返回对应的 `TextTrack` 对象。

- **事件**：
  - `change`：当文本轨道的状态发生变化时触发。

### 示例
以下是使用 `TextTrackList` 的基本示例：

```html
<video id="myVideo" controls>
    <source src="movie.mp4" type="video/mp4">
    <track id="track1" kind="subtitles" src="subtitles_en.vtt" srclang="en" label="English">
    <track id="track2" kind="subtitles" src="subtitles_cn.vtt" srclang="zh" label="中文">
    Your browser does not support the video tag.
</video>

<script>
    const video = document.getElementById('myVideo');
    const textTracks = video.textTracks;

    console.log('文本轨道数量:', textTracks.length);

    for (let i = 0; i < textTracks.length; i++) {
        console.log('轨道:', textTracks.item(i).label);
    }

    const chineseTrack = textTracks.getTrackById('track2');
    if (chineseTrack) {
        console.log('找到中文轨道:', chineseTrack.label);
    }
</script>
```

## 说明
- **常见问题**：
  - 确保在视频元素加载完毕后再访问 `textTracks` 属性，以避免获取空的 `TextTrackList`。
  - 不同浏览器对 `TextTrack` 的支持可能有所不同，使用前建议检查兼容性。

- **注意事项**：
  - `TextTrack` 的状态（例如是否启用）可以通过相应的属性进行检查和修改。
  - 使用 `getTrackById` 方法时，确保传入的 ID 是正确的，否则将返回 `null`。

## 一句话总结
`TextTrackList` 是一个用于管理和访问 HTML 媒体元素中的文本轨道集合的 JavaScript 接口。