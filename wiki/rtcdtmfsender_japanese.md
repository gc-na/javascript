<!--
Meta Description: # RTCDTMFSender：JavaScriptにおけるDTMF信号送信の完全ガイド ## 概要 RTCDTMFSenderは、WebRTCを使用した音声通話アプリケーションにおいて、Dual-Tone Multi-Frequency（DTMF）信号を送信するためのAPIです。これにより、ユーザ...
Meta Keywords: rtcdtmfsenderは, const, これにより, insertdtmf, tones
-->

# RTCDTMFSender：JavaScriptにおけるDTMF信号送信の完全ガイド

## 概要
RTCDTMFSenderは、WebRTCを使用した音声通話アプリケーションにおいて、Dual-Tone Multi-Frequency（DTMF）信号を送信するためのAPIです。これにより、ユーザーは電話のキー入力をリモートの相手に送信することができます。

## ドキュメンテーション

### 目的
RTCDTMFSenderは、音声通話中にトーン信号を送信するために使用されます。これにより、音声通話中にメニュー選択や電話番号の入力などが可能になります。

### 使用法
RTCDTMFSenderは、RTCPeerConnectionオブジェクトから生成されます。次のプロパティとメソッドがあります：

- **プロパティ**
  - `track`: DTMF信号を送信する対象の音声トラック。
  - `canInsertDTMF`: DTMF信号を送信できるかどうかを示す真偽値。

- **メソッド**
  - `insertDTMF(tones, duration, interToneGap)`: DTMFトーンを送信します。`tones`は送信するトーンの文字列、`duration`はトーンの持続時間（ミリ秒）、`interToneGap`はトーン間の間隔（ミリ秒）を指定します。

### 基本的な使用例
以下に、RTCDTMFSenderの基本的な使用例を示します。

```javascript
// RTCPeerConnectionの生成
const peerConnection = new RTCPeerConnection();

// 音声トラックの取得
const audioTrack = ...; // 既存の音声トラックを取得

// RTCDTMFSenderの生成
const dtmfSender = peerConnection.createDTMFSender(audioTrack);

// DTMFトーンを送信
dtmfSender.insertDTMF("123#", 100, 70);
```

## 説明
RTCDTMFSenderの使用において考慮すべき点は以下の通りです：

- **サポート状況**: 一部のブラウザやデバイスではRTCDTMFSenderがサポートされていない場合があります。最新のブラウザ互換性情報を確認してください。
- **DTMF信号の制限**: 一度に送信できるDTMFトーンの数に制限があります。長いトーン列を送信する際は注意が必要です。
- **音声トラックの状態**: DTMF信号を送信する音声トラックが正しく設定されていることを確認してください。トラックが未接続または無効な場合、DTMF信号は送信されません。

## 一文の要約
RTCDTMFSenderは、WebRTCを使用して音声通話中にDTMF信号を送信するためのJavaScript APIです。