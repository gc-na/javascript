<!--
Meta Description: # RTCStatsReport：JavaScript 中的實時通訊統計報告 ## 簡介 RTCStatsReport 是一個在 WebRTC 中用於獲取連接統計數據的接口。它提供了關於媒體流、網絡狀態以及連接的詳細信息，對於開發者來說，這是一個重要的工具以便於監控和優化實時通訊應用。 ## 文檔 ...
Meta Keywords: rtcstatsreport, report, console, log, getstats
-->

# RTCStatsReport：JavaScript 中的實時通訊統計報告

## 簡介
RTCStatsReport 是一個在 WebRTC 中用於獲取連接統計數據的接口。它提供了關於媒體流、網絡狀態以及連接的詳細信息，對於開發者來說，這是一個重要的工具以便於監控和優化實時通訊應用。

## 文檔
### 目的
RTCStatsReport 旨在提供有關 WebRTC 連接的實時統計數據，幫助開發者分析和改善通訊質量。

### 用法
RTCStatsReport 由 RTCPeerConnection 的 getStats() 方法生成。使用此方法，開發者可以獲取一組統計數據，這些數據可以用於評估連接的整體性能。

### 詳細信息
- **返回類型**：RTCStatsReport 是一個只讀對象，包含一組 RTCStats 對象。
- **屬性**：每個 RTCStats 對象都包含有關媒體流的各種屬性，例如 jitter、packetLoss、roundTripTime 等。
- **更新頻率**：RTCStatsReport 可以持續更新，因此開發者可以定期調用 getStats() 以獲取最新的統計數據。

## 示例
```javascript
const peerConnection = new RTCPeerConnection();

// 獲取統計數據
peerConnection.getStats(null).then(stats => {
    stats.forEach(report => {
        console.log(`Report type: ${report.type}`);
        console.log(`ID: ${report.id}`);
        console.log(`Timestamp: ${report.timestamp}`);
        console.log(`Jitter: ${report.jitter}`);
        console.log(`Packet Loss: ${report.packetsLost}`);
    });
});
```

## 解釋
- **常見陷阱**：在使用 RTCStatsReport 時，開發者可能會忽略統計數據的更新頻率。確保定期調用 getStats() 以獲取最新的數據。
- **注意事項**：不同瀏覽器對於 RTCStatsReport 的支持程度可能不同，請確保在不同環境中進行測試。

## 總結
RTCStatsReport 是一個關鍵的工具，幫助開發者獲取 WebRTC 連接的實時統計數據，以便於分析和優化通訊質量。