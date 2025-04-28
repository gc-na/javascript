<!--
Meta Description: # RTCIceCandidateとは？JavaScriptにおける使用法と機能 ## 概要 RTCIceCandidateは、WebRTCにおいてリアルタイム通信を実現するために使用される候補者（ICE候補）の一つです。このオブジェクトは、ピアツーピア接続の確立に必要な情報を保持し、接続の最適化を...
Meta Keywords: candidate, error, console, rtcicecandidateは, addicecandidate
-->

# RTCIceCandidateとは？JavaScriptにおける使用法と機能

## 概要
RTCIceCandidateは、WebRTCにおいてリアルタイム通信を実現するために使用される候補者（ICE候補）の一つです。このオブジェクトは、ピアツーピア接続の確立に必要な情報を保持し、接続の最適化を図ります。

## ドキュメント
### 目的
RTCIceCandidateは、WebRTCのICE（Interactive Connectivity Establishment）プロトコルに基づいて、ネットワーク上のピア間での接続を確立するための候補者を表現します。このオブジェクトは、IPアドレスやポート番号、候補のタイプ（ホスト、リレー、スリーレー）などの情報を含みます。

### 使用法
RTCIceCandidateは、通常、RTCPeerConnectionの`addIceCandidate()`メソッドを使用して追加されます。新しいICE候補が発見されたとき、これをRTCPeerConnectionに追加することで、接続の成功率を向上させます。

```javascript
// RTCIceCandidateのインスタンスを作成
const candidate = new RTCIceCandidate({
  candidate: 'candidate:842163049 1 udp 1677729535 192.168.1.2 54321 typ host',
  sdpMid: '0',
  sdpMLineIndex: 0
});

// RTCPeerConnectionへの追加
peerConnection.addIceCandidate(candidate)
  .then(() => {
    console.log('ICE候補が正常に追加されました。');
  })
  .catch((error) => {
    console.error('ICE候補の追加に失敗しました:', error);
  });
```

## 例
以下は、RTCIceCandidateを使用してICE候補を追加する基本的な例です。

```javascript
const peerConnection = new RTCPeerConnection();

// ICE候補のリスナーを設定
peerConnection.onicecandidate = (event) => {
  if (event.candidate) {
    console.log('新しいICE候補:', event.candidate);
  }
};

// ICE候補を追加
const iceCandidate = new RTCIceCandidate({
  candidate: 'candidate:12345 1 udp 2113937151 203.0.113.1 12345 typ srflx raddr 203.0.113.2 rport 54321',
  sdpMid: '0',
  sdpMLineIndex: 0
});

peerConnection.addIceCandidate(iceCandidate)
  .then(() => {
    console.log('候補が追加されました。');
  })
  .catch((error) => {
    console.error('候補の追加に失敗:', error);
  });
```

## 説明
RTCIceCandidateを使用する際の一般的な注意点として、次の点が挙げられます。

1. **ICE候補の形式**: ICE候補は特定の形式を持っており、正しい形式でなければエラーが発生します。特に、`candidate`フィールドの内容は正確である必要があります。

2. **sdpMidとsdpMLineIndexの重要性**: これらのフィールドは、特定のメディアストリームに関連するICE候補を識別するために必要です。間違った値を設定すると、ICE候補が無視される可能性があります。

3. **非同期処理**: `addIceCandidate()`メソッドはPromiseを返します。このため、成功時や失敗時の処理を適切に行うためには、`.then()`および`.catch()`を使用することが重要です。

## 一文要約
RTCIceCandidateは、WebRTCにおけるピアツーピア接続の最適化に必要なICE候補情報を提供するJavaScriptオブジェクトです。