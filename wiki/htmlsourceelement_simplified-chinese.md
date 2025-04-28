<!--
Meta Description: # HTMLSourceElement：JavaScript中的HTML源元素 ## 概述 HTMLSourceElement是HTML5中定义的一个接口，代表HTML `<source>` 元素。它在JavaScript中用于动态控制多媒体资源（如音频和视频）的加载和使用。 ## 文档 HTMLS...
Meta Keywords: video, source, src, type, mp4
-->

# HTMLSourceElement：JavaScript中的HTML源元素

## 概述
HTMLSourceElement是HTML5中定义的一个接口，代表HTML `<source>` 元素。它在JavaScript中用于动态控制多媒体资源（如音频和视频）的加载和使用。

## 文档
HTMLSourceElement的主要目的是为音频和视频元素提供多个媒体源的支持。通过使用`<source>`标签，开发者可以为浏览器提供不同格式的媒体文件，以确保在不同浏览器和设备上都能良好播放。

### 属性
- `src`：指定媒体文件的URL。
- `type`：指定媒体文件的MIME类型，例如`"video/mp4"`或`"audio/mpeg"`。
- `media`：用于定义媒体查询，以便在特定条件下加载该资源。

### 方法
HTMLSourceElement本身并不提供特定的方法，但可以通过JavaScript访问和操作其属性。

### 使用
通常，HTMLSourceElement与`<audio>`或`<video>`标签一起使用。例如：

```html
<video controls>
  <source src="movie.mp4" type="video/mp4">
  <source src="movie.ogg" type="video/ogg">
  您的浏览器不支持视频标签。
</video>
```

在JavaScript中，可以通过DOM API访问这些源元素。例如：

```javascript
const video = document.querySelector('video');
const sources = video.getElementsByTagName('source');
console.log(sources[0].src); // 输出第一个源的URL
```

## 示例
以下是使用HTMLSourceElement的基本示例：

```html
<!DOCTYPE html>
<html lang="zh">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>HTMLSourceElement 示例</title>
</head>
<body>
    <video controls>
        <source src="video.mp4" type="video/mp4">
        <source src="video.webm" type="video/webm">
        您的浏览器不支持视频标签。
    </video>

    <script>
        const videoElement = document.querySelector('video');
        videoElement.addEventListener('error', function() {
            console.log('视频加载失败！');
        });
    </script>
</body>
</html>
```

## 解释
使用HTMLSourceElement时，有几个常见的陷阱需要注意：
- **格式兼容性**：确保提供的媒体文件格式在目标浏览器中受支持。例如，某些浏览器可能不支持WebM格式。
- **网络问题**：媒体文件的URL必须有效，否则将导致加载错误。
- **媒体查询**：如果使用`media`属性，确保条件正确设置，以避免误加载。

## 一句话总结
HTMLSourceElement是用于在JavaScript中动态管理HTML `<source>` 元素，支持多媒体的加载和播放。