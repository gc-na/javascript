<!--
Meta Description: # USBInTransferResult: JavaScriptにおけるUSBデータ転送結果オブジェクト ## 概要 `USBInTransferResult`は、WebUSB APIにおいてUSBデバイスからのデータ転送結果を表すオブジェクトです。このオブジェクトは、デバイスから受信したデータや...
Meta Keywords: usbintransferresult, device, await, data, transferin
-->

# USBInTransferResult: JavaScriptにおけるUSBデータ転送結果オブジェクト

## 概要
`USBInTransferResult`は、WebUSB APIにおいてUSBデバイスからのデータ転送結果を表すオブジェクトです。このオブジェクトは、デバイスから受信したデータやステータスを取得するために使用されます。

## ドキュメント
`USBInTransferResult`は、USBデバイスとの通信において、データ受信の結果を管理するための重要な構造を提供します。このオブジェクトは、以下のプロパティを持ちます。

### プロパティ
- **data**: `ArrayBuffer`または`ArrayBufferView`型で、受信したデータを格納します。
- **status**: `number`型で、転送のステータスを表します。通常は、成功、失敗、または警告のコードが含まれます。

### 使用方法
`USBInTransferResult`は、USBデバイスからデータを受信した後に自動的に生成され、`USBDevice`オブジェクトの`transferIn`メソッドによって返されます。このメソッドを使用することで、特定のエンドポイントからデータを非同期的に取得できます。

```javascript
async function receiveData(device) {
    const endpointNumber = 1; // 使用するエンドポイントの番号
    const transferResult = await device.transferIn(endpointNumber, 64); // 64バイトのデータを受信

    // データを処理する
    const data = transferResult.data;
    console.log(new Uint8Array(data));
}
```

## 例
以下は、`USBInTransferResult`を使用してUSBデバイスからデータを受信する基本的な例です。

```javascript
async function connectAndReceive() {
    const device = await navigator.usb.requestDevice({ filters: [{ vendorId: 0x1234 }] });
    await device.open();
    await device.selectConfiguration(1);
    await device.claimInterface(0);

    const transferResult = await device.transferIn(1, 64);
    console.log("受信データ:", new Uint8Array(transferResult.data));
}

connectAndReceive().catch(console.error);
```

## 説明
`USBInTransferResult`を使用する際の一般的な落とし穴として、以下の点に注意が必要です。

- **エンドポイントの番号**: 使用するエンドポイントが正しいことを確認してください。間違った番号を指定すると、データの受信に失敗します。
- **データサイズ**: `transferIn`メソッドで指定するデータサイズは、エンドポイントの最大パケットサイズを超えてはいけません。
- **非同期処理**: `transferIn`は非同期メソッドであるため、`await`を使用して結果を待つ必要があります。

## 一言まとめ
`USBInTransferResult`は、WebUSB APIにおいてUSBデバイスからのデータ転送結果を効率的に管理するための重要なオブジェクトです。