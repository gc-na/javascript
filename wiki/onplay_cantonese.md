<!--
Meta Description: # JavaScript onplay 事件使用指南 ## 簡介 `onplay` 是一個在 HTML5 視頻和音頻元素中使用的事件，當媒體開始播放時觸發。這個事件可以幫助開發者在媒體播放開始時執行某些操作，例如顯示播放計時器或更改 UI 狀態。 ## 文檔 ### 目的 `onplay` 事件的主...
Meta Keywords: onplay, video, html, javascript, audio
-->

# JavaScript onplay 事件使用指南

## 簡介
`onplay` 是一個在 HTML5 視頻和音頻元素中使用的事件，當媒體開始播放時觸發。這個事件可以幫助開發者在媒體播放開始時執行某些操作，例如顯示播放計時器或更改 UI 狀態。

## 文檔
### 目的
`onplay` 事件的主要目的是讓開發者能夠在媒體開始播放時接收通知，並根據需要執行相應的操作。

### 使用方式
以下是如何使用 `onplay` 事件的基本步驟：

1. 在 HTML 中創建一個 `<video>` 或 `<audio>` 元素。
2. 使用 JavaScript 來添加事件監聽器，監聽 `onplay` 事件。

### 詳細信息
- **事件類型**: `Event`
- **適用於**: `<video>` 和 `<audio>` 標籤
- **觸發時機**: 媒體開始播放
- **相應的事件處理**: 可以通過添加事件監聽器來定義應該在播放開始時執行的代碼。

## 範例
### 基本使用範例
以下是使用 `onplay` 事件的基本代碼示例：

```html
<!DOCTYPE html>
<html lang="zh-HK">
<head>
    <meta charset="UTF-8">
    <title>onplay 事件範例</title>
</head>
<body>
    <video id="myVideo" width="320" height="240" controls>
        <source src="movie.mp4" type="video/mp4">
        您的瀏覽器不支持視頻標籤。
    </video>

    <script>
        const video = document.getElementById('myVideo');

        video.onplay = function() {
            console.log('視頻正在播放！');
        };
    </script>
</body>
</html>
```

## 解釋
### 常見問題
- **事件不觸發**: 確保媒體文件可以正常播放，並且沒有其他錯誤影響播放流程。
- **事件順序**: 注意 `onplay` 事件會在 `onpause` 之後觸發，而不是在 `onended` 事件之前。
- **多個事件監聽器**: 可以為同一元素添加多個 `onplay` 事件監聽器，但要注意事件的執行順序。

## 一句總結
`onplay` 事件在媒體開始播放時觸發，讓開發者可以自定義播放開始時的行為。