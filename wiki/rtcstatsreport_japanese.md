<!--
Meta Description: # RTCStatsReport: JavaScriptにおけるリアルタイム通信統計レポート ## 概要 RTCStatsReportは、WebRTC（Web Real-Time Communication）APIの一部であり、リアルタイム通信の統計情報を提供するオブジェクトです。このオブジェクトは...
Meta Keywords: report, error, peerconnection, getstats, type
-->

# RTCStatsReport: JavaScriptにおけるリアルタイム通信統計レポート

## 概要
RTCStatsReportは、WebRTC（Web Real-Time Communication）APIの一部であり、リアルタイム通信の統計情報を提供するオブジェクトです。このオブジェクトは、音声やビデオのストリームに関する詳細なデータを収集し、通信の品質を分析するのに役立ちます。

## ドキュメンテーション
### 目的
RTCStatsReportは、WebRTCアプリケーションのパフォーマンスをモニタリングし、改善するために使用されます。これには、遅延、パケットロス、ビットレートなどの重要な指標が含まれます。

### 使用方法
RTCStatsReportオブジェクトは通常、`RTCPeerConnection`の`getStats()`メソッドを使用して取得されます。このメソッドは、現在の通信状況に関する統計情報を非同期で返します。

### 詳細
- **プロパティ**: RTCStatsReportは、各統計情報に対して特定のプロパティを持つ複数のRTCStatsオブジェクトを含みます。これらのプロパティには、`timestamp`, `type`, `id`などが含まれます。
- **使用例**:
    ```javascript
    const peerConnection = new RTCPeerConnection();

    // ... ここで接続を確立するコード ...

    peerConnection.getStats(null).then(stats => {
        stats.forEach(report => {
            console.log(`Report ID: ${report.id}, Type: ${report.type}, Timestamp: ${report.timestamp}`);
        });
    }).catch(error => {
        console.error('Error getting stats: ', error);
    });
    ```

## 例
以下は、RTCStatsReportを使用して統計情報を取得する簡単な例です。

```javascript
const peerConnection = new RTCPeerConnection();

// メディアストリームを追加
navigator.mediaDevices.getUserMedia({ video: true, audio: true })
    .then(stream => {
        stream.getTracks().forEach(track => peerConnection.addTrack(track, stream));
        
        // 接続が確立された後に統計を取得
        peerConnection.oniceconnectionstatechange = () => {
            if (peerConnection.iceConnectionState === 'connected') {
                peerConnection.getStats(null).then(stats => {
                    stats.forEach(report => {
                        console.log(`Report ID: ${report.id}, Type: ${report.type}`);
                    });
                });
            }
        };
    }).catch(error => {
        console.error('Error accessing media devices.', error);
    });
```

## 説明
RTCStatsReportを使用する際の一般的な落とし穴には、以下のようなものがあります。
- **非同期取得**: `getStats()`は非同期メソッドであるため、統計情報の取得が完了する前に次の処理を進めると、期待通りの結果が得られない場合があります。
- **空のレポート**: 接続が確立されていない状態で`getStats()`を呼び出すと、空のレポートが返されることがあります。必ずICE接続状態を確認してから呼び出すようにしましょう。

## 一文要約
RTCStatsReportは、WebRTC通信の質を分析するために重要な統計情報を提供するJavaScriptオブジェクトです。