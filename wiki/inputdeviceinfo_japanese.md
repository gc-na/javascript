<!--
Meta Description: # InputDeviceInfo: JavaScriptにおけるデバイス情報の取得 ## 概要 `InputDeviceInfo`は、ウェブアプリケーションが接続されている入力デバイス（キーボード、マウス、ゲームパッドなど）の情報を取得するために使用されるAPIです。 ## ドキュメンテーション ...
Meta Keywords: inputdeviceinfo, device, console, kind, label
-->

# InputDeviceInfo: JavaScriptにおけるデバイス情報の取得

## 概要
`InputDeviceInfo`は、ウェブアプリケーションが接続されている入力デバイス（キーボード、マウス、ゲームパッドなど）の情報を取得するために使用されるAPIです。

## ドキュメンテーション
`InputDeviceInfo`は、Web APIの一部であり、ブラウザがサポートする入力デバイスに関する詳細情報を提供します。これにより、開発者はユーザーが使用しているデバイスに基づいてインターフェースを調整したり、特定の機能を有効化または無効化したりできます。

### 目的
- ユーザーの入力デバイスに関する情報を取得。
- デバイスに依存した機能を提供。

### 使用法
`InputDeviceInfo`は、`navigator.getInputDevices()`メソッドを使用して取得されます。このメソッドは、接続されているすべての入出力デバイスのリストを返します。

### 詳細
- **プロパティ**:
  - `deviceId`: デバイスの一意の識別子。
  - `kind`: デバイスの種類（例: 'audioinput', 'audiooutput', 'videoinput'）。
  - `label`: デバイスの名前またはラベル。

### 使用例
```javascript
navigator.getInputDevices().then(devices => {
    devices.forEach(device => {
        console.log(`Device ID: ${device.deviceId}`);
        console.log(`Kind: ${device.kind}`);
        console.log(`Label: ${device.label}`);
    });
}).catch(error => {
    console.error('デバイス情報の取得に失敗しました:', error);
});
```

## 説明
`InputDeviceInfo`を使用する際の一般的な問題点や注意事項には以下があります。

- **ブラウザのサポート**: 全てのブラウザがこのAPIをサポートしているわけではなく、使用前にサポート状況を確認する必要があります。
- **ユーザーの許可**: 一部のデバイス情報は、ユーザーの許可が必要です。特に、マイクやカメラの情報を取得する際は、ユーザーからの明示的な許可が求められます。
- **非同期処理**: デバイス情報の取得は非同期的に行われるため、Promiseを使用して結果を処理する必要があります。

## 一文の要約
`InputDeviceInfo`は、ブラウザが接続されている入力デバイスに関する情報を取得するためのAPIです。