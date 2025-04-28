<!--
Meta Description: # HTMLAudioElement：JavaScript 中音頻操作的核心對象 ## 概要 HTMLAudioElement 是一個用於在網頁中操作音頻的 JavaScript 對象，讓開發者能夠方便地控制音頻播放、暫停、音量等功能。 ## 文檔 ### 目的 HTMLAudioElement 使...
Meta Keywords: javascript, audioelement, html, htmlaudioelement, audio
-->

# HTMLAudioElement：JavaScript 中音頻操作的核心對象

## 概要
HTMLAudioElement 是一個用於在網頁中操作音頻的 JavaScript 對象，讓開發者能夠方便地控制音頻播放、暫停、音量等功能。

## 文檔
### 目的
HTMLAudioElement 使開發者能夠使用 JavaScript 來控制音頻元素，提供了一個接口來播放、暫停、調整音量以及獲取音頻的當前播放狀態等功能。

### 使用方法
您可以通過 HTML 標籤 `<audio>` 創建一個音頻元素，然後使用 JavaScript 獲取該元素的引用，進行操作。

### 詳細信息
- **創建音頻元素**：
  ```html
  <audio id="myAudio" src="音頻檔案.mp3" controls></audio>
  ```
  
- **JavaScript 操作**：
  ```javascript
  const audioElement = document.getElementById('myAudio');
  audioElement.play(); // 播放音頻
  audioElement.pause(); // 暫停音頻
  audioElement.volume = 0.5; // 設定音量為50%
  ```

- **屬性**：
  - `src`: 音頻來源
  - `volume`: 音量（範圍 0.0 到 1.0）
  - `paused`: 布林值，指示音頻是否暫停

- **方法**：
  - `play()`: 開始播放音頻
  - `pause()`: 暫停音頻

## 範例
### 基本用法
以下是如何使用 HTMLAudioElement 的基本範例：

```html
<!DOCTYPE html>
<html lang="zh-HK">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>音頻示例</title>
</head>
<body>
    <audio id="myAudio" src="音頻檔案.mp3" controls></audio>
    <button onclick="playAudio()">播放音頻</button>
    <button onclick="pauseAudio()">暫停音頻</button>

    <script>
        const audioElement = document.getElementById('myAudio');

        function playAudio() {
            audioElement.play();
        }

        function pauseAudio() {
            audioElement.pause();
        }
    </script>
</body>
</html>
```

## 解釋
### 常見問題
1. **音頻無法播放**：確保音頻檔案的路徑是正確的，並且文件格式受瀏覽器支持。
2. **音量無法調整**：音量必須在 0.0 到 1.0 之間，任何超出這個範圍的值都會被自動修正。

### 附加說明
- 當使用 `play()` 方法時，某些瀏覽器可能要求用戶先與頁面互動，例如點擊按鈕，才能播放音頻。
- 監聽音頻事件（如 `ended`、`timeupdate`）可以讓開發者獲取音頻的狀態變化。

## 總結
HTMLAudioElement 是用於在網頁中播放和控制音頻的強大 JavaScript 對象，為開發者提供了靈活的音頻操作接口。