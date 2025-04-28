<!--
Meta Description: # MediaStreamTrackAudioStats: JavaScriptのメディアストリームトラックオーディオ統計 ## 概要 `MediaStreamTrackAudioStats`は、WebRTC APIにおけるオーディオトラックのパフォーマンスを評価するための統計情報を提供します。この...
Meta Keywords: mediastreamtrackaudiostats, report, getstats, peerconnection, audio
-->

# MediaStreamTrackAudioStats: JavaScriptのメディアストリームトラックオーディオ統計

## 概要
`MediaStreamTrackAudioStats`は、WebRTC APIにおけるオーディオトラックのパフォーマンスを評価するための統計情報を提供します。このオブジェクトは、オーディオストリームの品質を監視し、デバッグや最適化に役立ちます。

## ドキュメント
`MediaStreamTrackAudioStats`は、オーディオトラックに関する様々な統計データを含むオブジェクトです。これには、エコーキャンセリング、ノイズ抑制、音声アクティビティの検出に関する情報が含まれています。主に、WebRTCを利用するアプリケーションで音声通話やビデオ通話の品質を向上させるために使用されます。

### 使用方法
このオブジェクトは、`RTCPeerConnection.getStats()`メソッドを使用して取得します。以下のプロパティを持っています：

- `echoReturnLoss`: エコーキャンセリングの効果を示す指標。
- `echoReturnLossEnhancement`: エコーキャンセリングの強化度。
- `totalAudioEnergy`: オーディオ信号のエネルギーの合計。
- `totalSamplesDuration`: サンプルの合計持続時間。

これらの統計情報を使用して、オーディオトラックのパフォーマンスを評価し、適切な改善策を講じることができます。

## 例
以下は、`MediaStreamTrackAudioStats`を取得する基本的なコード例です。

```javascript
const peerConnection = new RTCPeerConnection();

// オーディオトラックを追加
navigator.mediaDevices.getUserMedia({ audio: true })
    .then(stream => {
        stream.getTracks().forEach(track => peerConnection.addTrack(track, stream));
    });

// 統計情報を取得
peerConnection.getStats().then(stats => {
    stats.forEach(report => {
        if (report.type === 'audio') {
            console.log(`Echo Return Loss: ${report.echoReturnLoss}`);
            console.log(`Total Audio Energy: ${report.totalAudioEnergy}`);
        }
    });
});
```

## 説明
- **一般的な落とし穴**: `MediaStreamTrackAudioStats`は、サポートされているブラウザやデバイスによって異なる結果を返すことがあります。特に、エコーキャンセリング機能が有効な場合と無効な場合で統計が異なることがあります。
- **データの更新頻度**: 取得した統計情報はリアルタイムで変化するため、一定のインターバルで`getStats()`を呼び出すことが推奨されます。
- **ブラウザの互換性**: 全てのブラウザが完全にサポートしているわけではないため、各ブラウザのドキュメントを確認することが重要です。

## 一文要約
`MediaStreamTrackAudioStats`は、WebRTCにおけるオーディオトラックのパフォーマンスを測定し、音声通話の品質向上に役立つ統計情報を提供します。