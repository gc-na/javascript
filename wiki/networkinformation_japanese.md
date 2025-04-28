<!--
Meta Description: # ネットワーク情報 (NetworkInformation) - JavaScriptによるネットワーク状態の取得 ## 概要 NetworkInformationは、JavaScriptを用いてユーザーのデバイスのネットワーク接続状況を取得するためのAPIです。このAPIは、ネットワークの状態を...
Meta Keywords: connection, navigator, console, log, networkinformation
-->

# ネットワーク情報 (NetworkInformation) - JavaScriptによるネットワーク状態の取得

## 概要
NetworkInformationは、JavaScriptを用いてユーザーのデバイスのネットワーク接続状況を取得するためのAPIです。このAPIは、ネットワークの状態を監視し、変更があった際にリアルタイムで反応することを可能にします。

## ドキュメント
### 目的
NetworkInformation APIは、ウェブアプリケーションがユーザーのネットワーク接続状況を把握し、適切なアクションを取るための情報を提供します。これにより、アプリケーションはネットワークの状態に応じて最適な動作を行うことができます。

### 使用方法
NetworkInformation APIは、`navigator.connection`オブジェクトを通じてアクセスできます。このオブジェクトには、ネットワーク接続の種類や状態に関するプロパティとメソッドが含まれています。

#### 主なプロパティ
- `type`: 接続の種類（例: 'wifi', 'cellular'など）。
- `effectiveType`: ネットワークの速度に基づいた接続品質（例: 'slow-2g', '2g', '3g', '4g'など）。
- `downlink`: 接続のダウンリンク速度（Mbps）。
- `rtt`: 往復時間（ms）。
- `saveData`: ユーザーがデータセーブモードを有効にしているかどうか。

#### イベント
`change`イベントをリッスンすることで、ネットワーク状態が変化した際に通知を受け取ることができます。

```javascript
const connection = navigator.connection || navigator.mozConnection || navigator.webkitConnection;

connection.addEventListener('change', () => {
    console.log(`接続の種類が変更されました: ${connection.type}`);
});
```

## 例
### 基本的な使用例
以下は、ネットワーク接続の情報を取得し、コンソールに表示する簡単な例です。

```javascript
if ('connection' in navigator) {
    const connection = navigator.connection;
    console.log(`接続の種類: ${connection.type}`);
    console.log(`接続の効果的なタイプ: ${connection.effectiveType}`);
    console.log(`ダウンリンク速度: ${connection.downlink} Mbps`);
    console.log(`往復時間: ${connection.rtt} ms`);
    console.log(`データセーブモード: ${connection.saveData}`);
}
```

## 説明
### 一般的な落とし穴
- **ブラウザのサポート**: NetworkInformation APIはすべてのブラウザでサポートされているわけではありません。一部の古いブラウザや特定のモバイルブラウザでは利用できないことがあります。使用する前に、ブラウザの互換性を確認することが重要です。
- **イベントのリッスン**: `change`イベントは、ネットワークの種類や状態が変わったときにのみ発火します。初期状態を取得する際には、明示的にプロパティを参照する必要があります。

### 注意点
- ユーザーのプライバシーを尊重し、必要以上の情報を収集しないように心掛けましょう。
- ネットワーク情報は動的に変化するため、アプリケーションの状態を適切に管理することが重要です。

## 一文の要約
NetworkInformationは、JavaScriptを用いてユーザーのネットワーク接続状況を取得し、リアルタイムで変化に対応するためのAPIです。