<!--
Meta Description: # USBIsochronousInTransferResult: JavaScriptにおけるUSB非同期転送結果の理解 ## 概要 USBIsochronousInTransferResultは、JavaScriptにおけるUSB APIの一部であり、USBデバイスとの非同期データ転送の結果を表...
Meta Keywords: data, result, usbisochronousintransferresultは, error, status
-->

# USBIsochronousInTransferResult: JavaScriptにおけるUSB非同期転送結果の理解

## 概要
USBIsochronousInTransferResultは、JavaScriptにおけるUSB APIの一部であり、USBデバイスとの非同期データ転送の結果を表します。このオブジェクトは、USBデバイスからデータを受信する際の情報を提供し、開発者が転送の状態やエラーを把握するのに役立ちます。

## ドキュメント
### 概要
USBIsochronousInTransferResultは、USBデバイスからのデータを受信するための非同期転送の結果を示します。具体的には、転送されたデータのバッファ、転送の成功状態、エラーコードなどを含む情報を提供します。

### 使用法
USBIsochronousInTransferResultは通常、`navigator.usb` APIを介して取得されます。このAPIを使用してUSBデバイスに接続し、非同期にデータを取得することができます。

### プロパティ
- **data**: 受信したデータを含むArrayBuffer。
- **status**: 転送の成功または失敗を示すステータスコード。
- **error**: 転送中に発生したエラーがあれば、その詳細を示すオブジェクト。

### メソッド
- **getData()**: 受信したデータを取得します。
- **getStatus()**: 転送のステータスを取得します。

## 例
以下は、USBIsochronousInTransferResultを使用した基本的な例です。

```javascript
async function readFromDevice(device) {
    const result = await device.transferIn(endpointNumber, length);
    
    if (result.status === 'ok') {
        const data = result.data;
        console.log('受信データ:', new Uint8Array(data));
    } else {
        console.error('転送エラー:', result.error);
    }
}
```

## 説明
USBIsochronousInTransferResultを使用する際に注意が必要な点を以下に示します。

- **非同期操作**: USBデバイスからのデータ転送は非同期で行われるため、結果を受け取るためには`await`を使用する必要があります。
- **エラーハンドリング**: 転送が失敗した場合は、エラーメッセージを適切に処理することが重要です。
- **データの形式**: 受信したデータはArrayBuffer形式であるため、必要に応じて適切な型に変換する必要があります。

## 一文要約
USBIsochronousInTransferResultは、JavaScriptにおけるUSBデバイスからの非同期データ転送結果を表すオブジェクトです。