<!--
Meta Description: # RTCPeerConnectionとは？JavaScriptでの使用法と実例 ## 概要 `RTCPeerConnection`は、WebRTC（Web Real-Time Communication）APIの一部であり、リアルタイムの音声およびビデオ通信を確立するためのクラスです。ブラウザ間で...
Meta Keywords: rtcpeerconnection, const, peerconnection, event, configuration
-->

# RTCPeerConnectionとは？JavaScriptでの使用法と実例

## 概要
`RTCPeerConnection`は、WebRTC（Web Real-Time Communication）APIの一部であり、リアルタイムの音声およびビデオ通信を確立するためのクラスです。ブラウザ間での直接的なメディアストリームの送受信を可能にし、通信アプリケーションの構築において重要な役割を果たします。

## ドキュメント
### 目的
`RTCPeerConnection`は、オーディオおよびビデオのストリームを転送するための双方向の通信チャネルを提供します。このクラスは、ICE（Interactive Connectivity Establishment）フレームワークを使用して、ネットワーク上のピアを接続するための手続きを管理します。

### 使用法
`RTCPeerConnection`のインスタンスを作成するには、以下のようにします。

```javascript
const configuration = {
  iceServers: [
    { urls: 'stun:stun.l.google.com:19302' }
  ]
};

const peerConnection = new RTCPeerConnection(configuration);
```

- **configuration**: ICEサーバーの設定を含むオブジェクト。STUN（Session Traversal Utilities for NAT）やTURN（Traversal Using Relays around NAT）サーバーを指定します。

### 詳細
1. **メソッド**:
   - `createOffer()`: 新しいメディアのオファーを生成します。
   - `setLocalDescription()`: ローカルのSDP（Session Description Protocol）を設定します。
   - `setRemoteDescription()`: リモートのSDPを設定します。
   - `addIceCandidate()`: 新しいICE候補を追加します。

2. **イベント**:
   - `icecandidate`: 新しいICE候補が生成されたときにトリガーされます。
   - `track`: 新しいメディアストリームが追加されたときにトリガーされます。
   - `connectionstatechange`: 接続の状態が変化したときにトリガーされます。

## 例
以下は、基本的な使用例です。

```javascript
const peerConnection = new RTCPeerConnection();

peerConnection.onicecandidate = event => {
  if (event.candidate) {
    console.log('新しいICE候補:', event.candidate);
  }
};

peerConnection.ontrack = event => {
  const remoteStream = event.streams[0];
  const videoElement = document.getElementById('remoteVideo');
  videoElement.srcObject = remoteStream;
};

// メディアストリームを追加
navigator.mediaDevices.getUserMedia({ video: true, audio: true })
  .then(stream => {
    stream.getTracks().forEach(track => peerConnection.addTrack(track, stream));
  });
```

## 説明
`RTCPeerConnection`を使用する際の一般的な落とし穴には、ICE候補の管理が含まれます。ICE候補は非同期的に生成されるため、すべての候補を正しく処理するために、適切なイベントハンドリングが必要です。また、セキュリティ上の理由から、WebRTCはHTTPS経由で動作する必要がありますので注意が必要です。

## 一文の要約
`RTCPeerConnection`は、WebRTCを利用してブラウザ間でリアルタイムの音声およびビデオ通信を実現するための重要なJavaScriptクラスです。