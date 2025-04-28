<!--
Meta Description: # HTMLSourceElement：JavaScript 中的 HTML 來源元素 ## 簡介 HTMLSourceElement 是 JavaScript 中的 DOM 介面之一，用於表示 HTML 源元素 `<source>`。該元素通常用於媒體元素（如 `<audio>` 和 `<vide...
Meta Keywords: video, source, htmlsourceelement, type, javascript
-->

# HTMLSourceElement：JavaScript 中的 HTML 來源元素

## 簡介
HTMLSourceElement 是 JavaScript 中的 DOM 介面之一，用於表示 HTML 源元素 `<source>`。該元素通常用於媒體元素（如 `<audio>` 和 `<video>`）中，以指定多個媒體資源，讓瀏覽器根據支持的格式自動選擇最合適的資源。

## 文檔
### 目的
HTMLSourceElement 的主要目的是提供靈活性，使開發者能夠為媒體播放指定多個來源。每個 `<source>` 元素可以指定不同的媒體格式，這樣瀏覽器能夠選擇最兼容的格式來播放。

### 使用方法
在 JavaScript 中，可以通過 `document.createElement('source')` 方法創建一個新的 `<source>` 元素，並使用其屬性來設置資源 URL 和其他相關屬性，例如 `type` 和 `media`。

#### 屬性
- **src**：指定媒體文件的 URL。
- **type**：指定媒體文件的 MIME 類型（例如，`"audio/mp3"`）。
- **media**：用於指定媒體條件（例如，`"(min-width: 600px)"`）。

### 詳細說明
HTMLSourceElement 是 HTMLMediaElement 的一部分，這意味著它只能在特定的上下文中使用。通常，它與 `<audio>` 和 `<video>` 元素一起使用，用於提供多個來源以實現更好的瀏覽器兼容性。

## 範例
以下是使用 HTMLSourceElement 的基本範例：

```html
<video controls>
    <source src="video.mp4" type="video/mp4">
    <source src="video.ogg" type="video/ogg">
    您的瀏覽器不支持 video 標籤。
</video>
```

在 JavaScript 中創建 `<source>` 元素：

```javascript
let video = document.createElement('video');
video.controls = true;

let source1 = document.createElement('source');
source1.src = 'video.mp4';
source1.type = 'video/mp4';
video.appendChild(source1);

let source2 = document.createElement('source');
source2.src = 'video.ogg';
source2.type = 'video/ogg';
video.appendChild(source2);

document.body.appendChild(video);
```

## 解釋
在使用 `<source>` 元素時，開發者應注意以下幾點：
- 確保提供的媒體格式被目標瀏覽器支持，以免用戶無法播放媒體。
- `<source>` 元素必須放置在 `<audio>` 或 `<video>` 標籤內，否則不會生效。
- 在某些情況下，瀏覽器可能會忽略不被支持的來源，因此提供多個來源是最佳實踐。

## 一句總結
HTMLSourceElement 是一個用於指定媒體來源的 DOM 介面，確保在支持的格式中為媒體播放提供最佳選擇。