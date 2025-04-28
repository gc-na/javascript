<!--
Meta Description: # RTCDTMFSender 在 JavaScript 中的应用和使用 ## 概述 RTCDTMFSender 是 WebRTC API 中的一个接口，用于发送 DTMF（双音多频）信号。DTMF 信号通常用于电话系统中以传递数字（例如，按键输入）或其他控制命令。 ## 文档 ### 目的 RTC...
Meta Keywords: dtmf, rtcdtmfsender, rtcpeerconnection, webrtc, 发送器
-->

# RTCDTMFSender 在 JavaScript 中的应用和使用

## 概述
RTCDTMFSender 是 WebRTC API 中的一个接口，用于发送 DTMF（双音多频）信号。DTMF 信号通常用于电话系统中以传递数字（例如，按键输入）或其他控制命令。

## 文档
### 目的
RTCDTMFSender 允许开发者在 WebRTC 通话中发送 DTMF 信号，这对于应用程序需要处理按键输入时非常重要，例如在电话会议或语音识别系统中。

### 使用
要使用 RTCDTMFSender，首先需要创建一个 RTCPeerConnection 实例，并通过该实例获取 DTMF 发送器。具体步骤如下：

1. 创建 RTCPeerConnection。
2. 通过 RTCPeerConnection 的 `createDTMFSender()` 方法获取 DTMF 发送器。
3. 使用 DTMF 发送器的 `insertDTMF()` 方法发送信号。

### 详细信息
- **构造函数**: `RTCDTMFSender` 不能直接实例化。它通过 `RTCPeerConnection.createDTMFSender(track)` 方法创建。
- **方法**:
  - `insertDTMF(tones, duration?, interToneGap?)`: 发送 DTMF 音调。`tones` 是一个字符串，包含要发送的 DTMF 音调（如 '123#'），`duration` 是每个音调的持续时间（毫秒），`interToneGap` 是音调之间的间隔（毫秒）。
- **属性**:
  - `track`: 关联的音频轨道。

## 示例
```javascript
// 创建 RTCPeerConnection
const peerConnection = new RTCPeerConnection();

// 假设我们已经有一个音频轨道
const audioTrack = ...; // 获取音频轨道

// 创建 DTMF 发送器
const dtmfSender = peerConnection.createDTMFSender(audioTrack);

// 发送 DTMF 信号
dtmfSender.insertDTMF('123#', 100, 50); // 发送 '123#'，每个音调持续 100 毫秒，间隔 50 毫秒
```

## 说明
- **常见问题**: 在某些浏览器中，RTCDTMFSender 可能不被完全支持，建议在使用前检查浏览器兼容性。
- **音频轨道要求**: DTMF 发送器需要一个有效的音频轨道才能正常工作。
- **信号丢失**: 如果网络不稳定，可能会导致 DTMF 信号丢失，因此在重要场合下进行测试和监控非常重要。

## 一句话总结
RTCDTMFSender 是一个用于在 WebRTC 通话中发送 DTMF 信号的接口，简化了数字输入的处理。