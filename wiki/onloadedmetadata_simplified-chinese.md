<!--
Meta Description: # onloadedmetadata：JavaScript 中的重要事件 ## 概述 `onloadedmetadata` 是一个 JavaScript 事件，当媒体元素（如 `<audio>` 或 `<video>`）的元数据加载完成时触发。元数据包括诸如持续时间、尺寸、轨道等信息，这些信息对于控...
Meta Keywords: onloadedmetadata, video, html, javascript, console
-->

# onloadedmetadata：JavaScript 中的重要事件

## 概述
`onloadedmetadata` 是一个 JavaScript 事件，当媒体元素（如 `<audio>` 或 `<video>`）的元数据加载完成时触发。元数据包括诸如持续时间、尺寸、轨道等信息，这些信息对于控制媒体播放至关重要。

## 文档
`onloadedmetadata` 事件在媒体元素的元数据加载完毕时触发。此事件通常用于在媒体开始播放之前获取媒体的相关信息。可以通过添加事件监听器来处理此事件。

### 语法
```javascript
媒体元素.onloadedmetadata = function() {
    // 处理元数据加载完成后的逻辑
};
```

### 使用
1. **创建媒体元素**：首先，需要在 HTML 中创建一个 `<video>` 或 `<audio>` 元素。
2. **添加事件监听器**：可以通过设置 `onloadedmetadata` 属性或使用 `addEventListener` 方法来监听事件。
3. **实现逻辑**：在事件处理函数中编写处理元数据的逻辑。

## 示例
以下是一个基本的示例，展示如何使用 `onloadedmetadata` 事件。

```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <title>onloadedmetadata 示例</title>
</head>
<body>

<video id="myVideo" controls>
    <source src="video.mp4" type="video/mp4">
    您的浏览器不支持视频标签。
</video>

<script>
    const video = document.getElementById('myVideo');

    video.onloadedmetadata = function() {
        console.log('视频时长: ' + video.duration + '秒');
        console.log('视频宽度: ' + video.videoWidth + '像素');
        console.log('视频高度: ' + video.videoHeight + '像素');
    };
</script>

</body>
</html>
```

在这个示例中，当视频的元数据加载完成后，控制台会输出视频的时长和尺寸信息。

## 解释
使用 `onloadedmetadata` 事件时，有一些常见的注意事项：
- **浏览器兼容性**：确保所使用的浏览器支持 `onloadedmetadata` 事件。大多数现代浏览器都支持，但在一些旧版浏览器中可能会出现问题。
- **多次触发**：该事件在视频/音频元素的元数据每次加载时都会触发，因此在同一个元素上，如果更换源文件，事件会再次触发。
- **监听器位置**：在设置事件监听器时，应确保在加载媒体元素之前就已设置，以避免错过事件。

## 一句话总结
`onloadedmetadata` 事件为开发者提供了在媒体元素元数据加载完成时执行特定逻辑的能力，是控制媒体播放的重要工具。