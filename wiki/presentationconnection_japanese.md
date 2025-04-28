<!--
Meta Description: # PresentationConnection: JavaScriptによるプレゼンテーション接続の利用 ## 概要 `PresentationConnection`は、Webアプリケーションがプレゼンテーションデバイス（例：スマートTVやプロジェクター）と接続し、コンテンツを表示するためのAPI...
Meta Keywords: connection, presentationconnection, presentation, state, onstatechange
-->

# PresentationConnection: JavaScriptによるプレゼンテーション接続の利用

## 概要
`PresentationConnection`は、Webアプリケーションがプレゼンテーションデバイス（例：スマートTVやプロジェクター）と接続し、コンテンツを表示するためのAPIです。この機能により、ユーザーはモバイルデバイスやPCからリモートデバイスにコンテンツをストリーミングできます。

## ドキュメント

### 目的
`PresentationConnection`は、プレゼンテーションデバイスとの接続を管理し、データの送受信を行うためのインターフェースを提供します。このAPIを使用することで、開発者はプレゼンテーションの開始、データの送信、接続の状態管理を行うことができます。

### 使用法
`PresentationConnection`は、通常、`Presentation` APIと組み合わせて使用されます。以下の基本的なステップで利用できます。

1. プレゼンテーションデバイスへの接続を開始する。
2. 接続が確立されたら、データを送信する。
3. 接続状態を監視し、必要に応じて接続を終了する。

### 詳細
- **プロパティ**
  - `connectionId`: 接続の一意の識別子。
  - `state`: 接続の状態（例：`connecting`, `connected`, `disconnected`, `terminated`）。
  
- **メソッド**
  - `send(data)`: プレゼンテーションデバイスにデータを送信します。
  - `close()`: 接続を終了します。
  
- **イベント**
  - `onstatechange`: 接続の状態が変更されたときに発生します。

## 例

### 基本的な使用例
```javascript
// プレゼンテーションを開始する
let presentation = new Presentation();
presentation.start().then((connection) => {
    // 接続が確立された場合
    console.log("接続されました:", connection.connectionId);

    // データを送信する
    connection.send("こんにちは、プレゼンテーションデバイス！");
    
    // 接続状態を監視
    connection.onstatechange = () => {
        console.log("接続状態:", connection.state);
        if (connection.state === 'disconnected') {
            connection.close();
        }
    };
}).catch((error) => {
    console.error("接続エラー:", error);
});
```

## 説明

### よくある落とし穴
- **接続のタイミング**: プレゼンテーションデバイスが利用可能でないと接続できません。デバイスの準備状況を確認することが重要です。
- **状態管理**: `onstatechange`イベントを適切に設定しないと、接続状態の変化を見逃すことがあります。
- **データ形式**: 送信するデータの形式に注意が必要です。適切な形式でないと、デバイス側で正しく解釈されない可能性があります。

### 注意点
- `PresentationConnection`は、Webブラウザの実装によって異なるため、互換性の確認が必要です。
- セキュリティに関する制約もあるため、HTTPS環境での使用が推奨されます。

## 一文要約
`PresentationConnection`は、JavaScriptを使用してプレゼンテーションデバイスと接続し、コンテンツをストリーミングするためのAPIです。