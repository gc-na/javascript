<!--
Meta Description: # JavaScript 事件 onended：使用指南与示例 ## 概述 `onended` 是一个与多媒体元素（如 `<audio>` 和 `<video>`）相关的事件处理程序属性，旨在当媒体播放结束时触发。它在开发基于音频和视频的应用程序时非常有用，能够帮助开发者实现自定义的逻辑。 ## 文...
Meta Keywords: onended, audio, html, javascript, myaudio
-->

# JavaScript 事件 onended：使用指南与示例

## 概述
`onended` 是一个与多媒体元素（如 `<audio>` 和 `<video>`）相关的事件处理程序属性，旨在当媒体播放结束时触发。它在开发基于音频和视频的应用程序时非常有用，能够帮助开发者实现自定义的逻辑。

## 文档
### 目的
`onended` 事件用于检测音频或视频播放的结束。这使得开发者能够在媒体播放完成后执行特定的操作，比如加载下一首音频或显示提示信息。

### 用法
`onended` 事件可以直接在 HTML 元素中使用，也可以通过 JavaScript 代码进行绑定。以下是两种常见的用法：

1. **HTML 使用示例**：
   ```html
   <audio id="myAudio" src="audio.mp3" onended="myFunction()"></audio>
   ```

2. **JavaScript 绑定**：
   ```javascript
   const audioElement = document.getElementById('myAudio');
   audioElement.onended = function () {
       console.log('音频播放结束');
   };
   ```

### 详细说明
- **属性类型**：`onended` 是一个事件处理程序属性，可以接受一个函数作为值。
- **事件**：当音频或视频播放到达结束时，`onended` 事件会被触发。
- **兼容性**：大多数现代浏览器都支持 `onended` 事件，包括 Chrome、Firefox、Safari 和 Edge。

## 示例
### 基本用法示例
以下是一个简单的示例，展示如何使用 `onended` 事件：

```html
<!DOCTYPE html>
<html lang="zh">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>音频播放示例</title>
</head>
<body>
    <audio id="myAudio" src="audio.mp3" controls></audio>
    <script>
        const audio = document.getElementById('myAudio');
        audio.onended = function() {
            alert('音频播放结束');
        };
    </script>
</body>
</html>
```

## 解释
- **常见问题**：确保媒体文件（音频或视频）正确加载，否则 `onended` 事件可能不会触发。
- **注意事项**：在某些情况下，若用户手动暂停或停止播放，`onended` 事件将不会被触发。
- **额外提示**：可以结合其他事件（如 `onplay` 或 `onpause`）来实现更复杂的逻辑。

## 一句话总结
`onended` 事件用于在多媒体播放结束时触发特定的回调函数，帮助开发者实现自定义功能。