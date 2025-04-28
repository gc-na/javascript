<!--
Meta Description: # RTCPeerConnection：JavaScript中的实时通信核心 ## 概述 RTCPeerConnection 是 WebRTC API 的核心组成部分，允许浏览器之间进行音频、视频和数据流的直接通信。它提供了必要的方法和事件，以实现点对点的连接，适用于实时通信应用程序，如视频会议和实...
Meta Keywords: rtcpeerconnection, peerconnection, const, offer, javascript
-->

# RTCPeerConnection：JavaScript中的实时通信核心

## 概述
RTCPeerConnection 是 WebRTC API 的核心组成部分，允许浏览器之间进行音频、视频和数据流的直接通信。它提供了必要的方法和事件，以实现点对点的连接，适用于实时通信应用程序，如视频会议和实时数据共享。

## 文档
### 目的
RTCPeerConnection 的主要目的是在浏览器之间建立和管理 WebRTC 连接，支持音频、视频和数据的传输。它处理信号交换、网络传输、编解码以及连接的生命周期管理。

### 使用方法
要使用 RTCPeerConnection，首先需要创建一个 RTCPeerConnection 实例。以下是基本的使用步骤：

1. **创建 RTCPeerConnection 实例**：
   ```javascript
   const configuration = {
       iceServers: [
           { urls: 'stun:stun.l.google.com:19302' }
       ]
   };
   const peerConnection = new RTCPeerConnection(configuration);
   ```

2. **添加媒体流**：
   使用 `addTrack()` 或 `addStream()` 方法将音频或视频流添加到连接中。
   ```javascript
   const localStream = await navigator.mediaDevices.getUserMedia({ video: true, audio: true });
   localStream.getTracks().forEach(track => peerConnection.addTrack(track, localStream));
   ```

3. **创建和发送 SDP Offer**：
   使用 `createOffer()` 和 `setLocalDescription()` 方法创建并设置连接的描述。
   ```javascript
   const offer = await peerConnection.createOffer();
   await peerConnection.setLocalDescription(offer);
   ```

4. **处理 ICE 候选**：
   监听 `icecandidate` 事件以获取网络候选并发送给另一端。
   ```javascript
   peerConnection.onicecandidate = event => {
       if (event.candidate) {
           // 发送候选到远端
       }
   };
   ```

### 详细信息
- **配置**：RTCPeerConnection 接受一个配置对象，通常包含 ICE 服务器信息以帮助连接建立。
- **信令**：RTCPeerConnection 本身不处理信令，需要通过 WebSocket 或其他方式实现信令交换。
- **事件**：RTCPeerConnection 提供多个事件，如 `oniceconnectionstatechange`, `ontrack` 等，用于处理连接状态和媒体流。

## 示例
以下是一个简单的示例，展示了如何使用 RTCPeerConnection 进行视频通话：

```javascript
const peerConnection = new RTCPeerConnection(configuration);

// 获取本地媒体流
navigator.mediaDevices.getUserMedia({ video: true, audio: true })
    .then(stream => {
        stream.getTracks().forEach(track => peerConnection.addTrack(track, stream));
    });

// 处理远端媒体流
peerConnection.ontrack = event => {
    const remoteVideo = document.getElementById('remoteVideo');
    remoteVideo.srcObject = event.streams[0];
};

// 创建并发送 Offer
async function startCall() {
    const offer = await peerConnection.createOffer();
    await peerConnection.setLocalDescription(offer);
    // 发送 offer 到远端
}
```

## 说明
- **常见问题**：确保设备的音视频权限已被授予，否则无法获取媒体流。
- **网络问题**：网络环境可能影响 ICE 候选的收集和连接的建立，使用多个 ICE 服务器可以提高成功率。
- **信令实现**：需要自行实现信令机制以交换 SDP 描述和 ICE 候选。

## 一句话总结
RTCPeerConnection 是 WebRTC 中用于实现浏览器间实时音视频和数据通信的基础构件。