<!--
Meta Description: # JavaScript 中的 onPlaying 事件 ## 摘要 `onPlaying` 事件是一个 JavaScript 事件，通常用于多媒体元素（如 `<audio>` 和 `<video>`）的播放状态。它在媒体开始播放时被触发，开发者可以利用该事件来执行特定的操作或更新用户界面。 ## ...
Meta Keywords: onplaying, video, javascript, html, mp4
-->

# JavaScript 中的 onPlaying 事件

## 摘要
`onPlaying` 事件是一个 JavaScript 事件，通常用于多媒体元素（如 `<audio>` 和 `<video>`）的播放状态。它在媒体开始播放时被触发，开发者可以利用该事件来执行特定的操作或更新用户界面。

## 文档
`onPlaying` 是一个事件处理程序，属于 HTMLMediaElement 接口。在多媒体元素开始播放后，该事件会被触发，意味着媒体文件不再处于暂停状态。

### 目的
`onPlaying` 事件的主要目的是让开发者能够在多媒体文件开始播放时执行特定的操作，比如更新播放控制界面或记录播放统计。

### 用法
可以通过直接在 HTML 标签中设置，或使用 JavaScript 添加事件监听器来使用 `onPlaying` 事件。

#### 示例 1: 在 HTML 中使用
```html
<video id="myVideo" onplaying="videoPlaying()">
    <source src="movie.mp4" type="video/mp4">
    您的浏览器不支持视频标签。
</video>
<script>
function videoPlaying() {
    console.log("视频正在播放");
}
</script>
```

#### 示例 2: 使用 JavaScript 添加事件监听器
```html
<video id="myVideo">
    <source src="movie.mp4" type="video/mp4">
    您的浏览器不支持视频标签。
</video>
<script>
const video = document.getElementById('myVideo');
video.addEventListener('playing', function() {
    console.log("视频正在播放");
});
</script>
```

## 说明
使用 `onPlaying` 事件时，开发者需要注意以下几点：

1. **不触发暂停状态**：`onPlaying` 事件只在媒体开始播放后触发，不会在媒体暂停后再次触发。
2. **与其他事件的关系**：`onPlaying` 事件通常与 `onPause`、`onEnded` 等事件一起使用，以便对媒体状态进行全面监控。
3. **兼容性问题**：尽管大部分现代浏览器都支持 `onPlaying` 事件，但在某些老旧浏览器上可能会有不一致的表现，因此建议进行相应的兼容性测试。

## 一句话总结
`onPlaying` 事件在 JavaScript 中用于监听多媒体元素开始播放的状态变化。