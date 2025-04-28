<!--
Meta Description: # HTMLVideoElement：JavaScript 中的视频元素 ## 概述 HTMLVideoElement 是一个 JavaScript 接口，用于操作 HTML 中的 `<video>` 元素。它允许开发者通过编程方式控制视频播放、暂停、音量、全屏等功能，增强用户体验。 ## 文档 H...
Meta Keywords: video, htmlvideoelement, javascript, html, currenttime
-->

# HTMLVideoElement：JavaScript 中的视频元素

## 概述
HTMLVideoElement 是一个 JavaScript 接口，用于操作 HTML 中的 `<video>` 元素。它允许开发者通过编程方式控制视频播放、暂停、音量、全屏等功能，增强用户体验。

## 文档
HTMLVideoElement 接口提供了一系列属性和方法，用于对视频内容进行控制和管理。它是 HTMLMediaElement 的子类，包含许多用于视频处理的基本功能。

### 主要用途
- 控制视频播放（播放、暂停、停止）
- 调整音量和播放速度
- 处理视频的元数据和状态

### 重要属性
- `currentTime`：获取或设置视频播放的当前时间（秒）。
- `duration`：返回视频的总时长（秒）。
- `paused`：返回一个布尔值，指示视频是否暂停。
- `muted`：获取或设置视频是否静音。
- `volume`：获取或设置视频的音量（0.0 到 1.0）。

### 重要方法
- `play()`：开始播放视频。
- `pause()`：暂停视频播放。
- `load()`：重新加载视频。
- `canPlayType(type)`：检查浏览器是否支持特定视频类型。

## 示例
以下是使用 HTMLVideoElement 的基本示例：

### 创建视频元素
```html
<video id="myVideo" width="640" height="360" controls>
    <source src="movie.mp4" type="video/mp4">
    您的浏览器不支持视频标签。
</video>
```

### JavaScript 控制视频
```javascript
const video = document.getElementById('myVideo');

// 播放视频
video.play();

// 暂停视频
video.pause();

// 设置当前播放时间
video.currentTime = 10; // 跳到第10秒

// 调整音量
video.volume = 0.5; // 设置音量为50%
```

## 说明
使用 HTMLVideoElement 时，开发者常见的陷阱包括：
- 确保视频文件格式和 MIME 类型正确，以避免 `canPlayType` 返回 "probably" 或 "maybe"。
- 在视频加载完成之前，不要尝试访问 `duration` 或 `currentTime`，否则可能会得到 NaN 值。
- 在播放视频之前，确保处理好用户权限和浏览器的自动播放政策。

## 一句话总结
HTMLVideoElement 是 JavaScript 中用于控制和操作 HTML `<video>` 元素的强大接口。