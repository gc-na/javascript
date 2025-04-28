<!--
Meta Description: # DocumentPictureInPicture：JavaScript 中的畫中畫功能 ## 摘要 `DocumentPictureInPicture` 是一個JavaScript API，允許網頁中的媒體元素進入畫中畫模式，使用戶能夠在小視窗中繼續觀看視頻或其他內容，而不會干擾他們的其他工作。...
Meta Keywords: video, documentpictureinpicture, pipbutton, document, audio
-->

# DocumentPictureInPicture：JavaScript 中的畫中畫功能

## 摘要
`DocumentPictureInPicture` 是一個JavaScript API，允許網頁中的媒體元素進入畫中畫模式，使用戶能夠在小視窗中繼續觀看視頻或其他內容，而不會干擾他們的其他工作。

## 文檔
### 目的
`DocumentPictureInPicture` 的主要目的是提升用戶體驗，使用戶能夠在瀏覽器中方便地觀看視頻內容，同時瀏覽其他網頁或應用程式。

### 使用方式
要啟用畫中畫模式，開發者需確保媒體元素（如 `<video>` 或 `<audio>`）已經被用戶交互觸發。然後，可以調用 `requestPictureInPicture()` 方法來進入畫中畫模式。

### 詳細說明
- 當媒體進入畫中畫模式後，內容將以浮動窗口形式顯示，並且用戶可以自由地移動這個窗口。
- 用戶可以隨時退出畫中畫模式，通常通過按下窗口上的關閉按鈕。
- 畫中畫模式的支持情況取決於用戶的瀏覽器及其版本。

## 範例
以下是如何在HTML中實現畫中畫功能的基本範例：

```html
<video id="myVideo" controls>
  <source src="video.mp4" type="video/mp4">
  您的瀏覽器不支持視頻標籤。
</video>
<button id="pipButton">進入畫中畫模式</button>

<script>
  const video = document.getElementById('myVideo');
  const pipButton = document.getElementById('pipButton');

  pipButton.addEventListener('click', async () => {
    if (video !== document.pictureInPictureElement) {
      await video.requestPictureInPicture();
    } else {
      await document.exitPictureInPicture();
    }
  });
</script>
```

## 解釋
### 常見問題
1. **不支援的瀏覽器**：並非所有瀏覽器都支持畫中畫功能，查看您的瀏覽器版本是否支持。
2. **自動播放限制**：根據瀏覽器的自動播放政策，視頻可能需要用戶交互才能開始播放並進入畫中畫模式。
3. **媒體元素要求**：僅支持 `<video>` 和 `<audio>` 等媒體元素。其他元素無法使用畫中畫功能。

## 一句總結
`DocumentPictureInPicture` 使開發者能夠在網頁中實現畫中畫模式，提升用戶的多任務處理能力。