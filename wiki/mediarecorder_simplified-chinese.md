<!--
Meta Description: # MediaRecorder：JavaScript 中的多媒体录制API ## 概述 MediaRecorder 是一个 JavaScript API，允许开发者在网页中录制音频和视频流。该 API 使得捕获和保存多媒体内容变得简单，广泛应用于音频通话、视频会议及其他多媒体应用。 ## 文档 ##...
Meta Keywords: mediarecorder, api, video, const, javascript
-->

# MediaRecorder：JavaScript 中的多媒体录制API

## 概述
MediaRecorder 是一个 JavaScript API，允许开发者在网页中录制音频和视频流。该 API 使得捕获和保存多媒体内容变得简单，广泛应用于音频通话、视频会议及其他多媒体应用。

## 文档
### 目的
MediaRecorder API 旨在提供一个简单的接口，通过它，开发者可以轻松地录制来自 `<video>` 或 `<audio>` 元素、媒体设备（如摄像头和麦克风）等的音频和视频流。

### 用法
要使用 MediaRecorder，首先需要获取一个媒体流（MediaStream），通常通过 `getUserMedia()` 方法获取。然后，可以创建一个 MediaRecorder 实例，并开始录制。

### 细节
以下是 MediaRecorder 的关键属性和方法：
- **属性**
  - `state`：表示录制器的当前状态（"inactive"、"recording" 或 "paused"）。
  - `mimeType`：表示录制的媒体类型，如 "video/webm" 或 "audio/webm"。
  
- **方法**
  - `start()`：开始录制媒体流，可以指定录制的时间片（以毫秒为单位）。
  - `stop()`：停止录制。
  - `pause()`：暂停录制。
  - `resume()`：恢复录制。

- **事件**
  - `dataavailable`：在录制过程中生成媒体数据时触发。
  - `stop`：在录制停止时触发。

使用示例：

```javascript
// 获取媒体流
navigator.mediaDevices.getUserMedia({ video: true, audio: true })
  .then(stream => {
    // 创建 MediaRecorder 实例
    const mediaRecorder = new MediaRecorder(stream);
    const chunks = [];

    // 监听 dataavailable 事件
    mediaRecorder.ondataavailable = event => {
      if (event.data.size > 0) {
        chunks.push(event.data);
      }
    };

    // 监听 stop 事件
    mediaRecorder.onstop = () => {
      const blob = new Blob(chunks, { type: 'video/webm' });
      const url = URL.createObjectURL(blob);
      const a = document.createElement('a');
      a.href = url;
      a.download = 'recorded-video.webm';
      document.body.appendChild(a);
      a.click();
      document.body.removeChild(a);
    };

    // 开始录制
    mediaRecorder.start();

    // 停止录制后 5 秒
    setTimeout(() => {
      mediaRecorder.stop();
    }, 5000);
  })
  .catch(error => {
    console.error('获取媒体流失败:', error);
  });
```

## 解释
在使用 MediaRecorder 时，开发者应注意以下几点：
- **浏览器兼容性**：MediaRecorder API 在某些旧版浏览器中可能不被支持，因此在使用前需要检查兼容性。
- **MIME 类型**：确保使用的 MIME 类型在浏览器中得到支持。不同的浏览器对于支持的媒体类型有所不同。
- **数据处理**：在 `dataavailable` 事件中，可能会有多个数据块生成，因此需要妥善处理这些数据块。

## 一句话总结
MediaRecorder 是一个强大的 JavaScript API，允许开发者轻松录制和保存音频和视频流。