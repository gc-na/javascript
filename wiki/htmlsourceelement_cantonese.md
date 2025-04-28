<!--
Meta Description: # HTMLSourceElement：JavaScript 中的 HTML 源元素 ## 概述 HTMLSourceElement 是一個與網頁多媒體內容（如音頻和視頻）相關的 HTML 元素，主要用於指定媒體資源的來源。在 JavaScript 中，這個元素可用於動態地控制媒體內容的顯示。 ##...
Meta Keywords: video, source, htmlsourceelement, javascript, src
-->

# HTMLSourceElement：JavaScript 中的 HTML 源元素

## 概述
HTMLSourceElement 是一個與網頁多媒體內容（如音頻和視頻）相關的 HTML 元素，主要用於指定媒體資源的來源。在 JavaScript 中，這個元素可用於動態地控制媒體內容的顯示。

## 文檔
HTMLSourceElement 的主要目的是支持 `<source>` 標籤，這個標籤可以用於 `<audio>` 和 `<video>` 元素。通過使用 `<source>`，開發者可以為不同格式的媒體提供多個來源，讓瀏覽器根據支持的格式自動選擇最合適的來源。

### 用法
在 JavaScript 中，您可以使用 `document.createElement` 方法創建一個新的 HTMLSourceElement。例如：

```javascript
const sourceElement = document.createElement('source');
sourceElement.src = 'video.mp4';
sourceElement.type = 'video/mp4';
```

這段代碼創建了一個新的 `<source>` 標籤，並設置了資源的來源和類型。

### 詳細信息
- `src` 屬性：指定媒體資源的 URL。
- `type` 屬性：指定媒體的 MIME 類型，例如 `audio/mpeg` 或 `video/mp4`。
- 可以在 `<audio>` 或 `<video>` 標籤內使用多個 `<source>` 標籤，讓瀏覽器選擇最適合的格式。

## 示例
以下是一個使用 HTMLSourceElement 的基本示例：

```html
<video controls>
    <source src="video.mp4" type="video/mp4">
    <source src="video.ogg" type="video/ogg">
    您的瀏覽器不支持 video 標籤。
</video>
```

在這個例子中，瀏覽器將選擇支持的第一個媒體來源。

### 使用 JavaScript 動態添加源
```javascript
const video = document.querySelector('video');
const source = document.createElement('source');
source.src = 'video.webm';
source.type = 'video/webm';
video.appendChild(source);
video.load(); // 重新加載視頻以使用新源
```

## 解釋
在使用 HTMLSourceElement 時，有幾個常見的陷阱需要注意：
1. 確保 `src` 和 `type` 屬性正確，否則媒體可能無法加載。
2. 當動態添加 `<source>` 標籤時，務必調用 `.load()` 方法以重新加載媒體元素，否則新源不會生效。
3. 在某些舊版瀏覽器中，可能不支持某些 MIME 類型，導致媒體無法播放。

## 一句總結
HTMLSourceElement 是用於指定多媒體資源來源的 HTML 元素，可以通過 JavaScript 動態控制媒體內容的顯示。