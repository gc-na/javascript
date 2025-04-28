<!--
Meta Description: # RTCSessionDescription：JavaScript中的WebRTC会话描述 ## 概述 `RTCSessionDescription` 是WebRTC API的一部分，用于表示多媒体会话的描述信息。它通常用于建立WebRTC连接时，定义媒体流的类型、编码和其它重要参数。 ## 文档...
Meta Keywords: rtcsessiondescription, type, sdp, offer, ip4
-->

# RTCSessionDescription：JavaScript中的WebRTC会话描述

## 概述
`RTCSessionDescription` 是WebRTC API的一部分，用于表示多媒体会话的描述信息。它通常用于建立WebRTC连接时，定义媒体流的类型、编码和其它重要参数。

## 文档
`RTCSessionDescription` 构造函数用于创建一个会话描述对象，主要有两个属性：`type` 和 `sdp`。

- **type**: 描述会话的类型，通常为`"offer"`或`"answer"`。`"offer"`用于发起连接，而`"answer"`用于响应连接请求。
- **sdp**: 会话描述协议（Session Description Protocol）字符串，包含有关媒体流的详细信息，如编解码器、媒体格式、网络地址等。

### 用法
要使用 `RTCSessionDescription`，需要首先创建一个实例并传入一个对象，其中包含 `type` 和 `sdp`：

```javascript
const sessionDescription = new RTCSessionDescription({
    type: 'offer',
    sdp: 'v=0\r\no=- 4611733201948988239 2 IN IP4 127.0.0.1\r\ns=-\r\nc=IN IP4 127.0.0.1\r\nt=0 0\r\nm=audio 9 UDP/TLS/RTP/SAVPF 111 103\r\na=rtpmap:111 opus/48000/2\r\na=rtpmap:103 ISAC/16000\r\n'
});
```

## 示例
以下是一个创建和使用 `RTCSessionDescription` 的基本示例：

```javascript
// 创建一个RTCSessionDescription实例
const offerDescription = new RTCSessionDescription({
    type: 'offer',
    sdp: 'v=0\r\no=- 4611733201948988239 2 IN IP4 127.0.0.1\r\ns=-\r\nc=IN IP4 127.0.0.1\r\nt=0 0\r\nm=video 9 UDP/TLS/RTP/SAVPF 96\r\na=rtpmap:96 VP8/90000\r\n'
});

// 使用RTCPeerConnection设置会话描述
const peerConnection = new RTCPeerConnection();
peerConnection.setLocalDescription(offerDescription)
    .then(() => {
        console.log('本地描述设置成功！');
    })
    .catch(error => {
        console.error('设置本地描述失败:', error);
    });
```

## 说明
在使用 `RTCSessionDescription` 时，需要注意以下几点：

1. **SDP格式**: 确保传入的SDP字符串格式正确，任何格式错误可能导致连接失败。
2. **异步操作**: `setLocalDescription` 和 `setRemoteDescription` 方法是异步的，确保使用`Promise`处理返回结果。
3. **类型匹配**: 确保在设置会话描述时，`type` 的值与预期的操作一致，通常发起方使用`"offer"`，接收方使用`"answer"`。

## 一句话总结
`RTCSessionDescription` 是WebRTC API中用于描述多媒体会话的重要对象，包含会话类型和SDP信息。