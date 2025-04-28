<!--
Meta Description: # PresentationConnectionCloseEvent: JavaScriptにおけるプレゼンテーション接続の終了イベント ## 概要 `PresentationConnectionCloseEvent`は、WebプレゼンテーションAPIにおいて、プレゼンテーション接続が閉じられた際に...
Meta Keywords: presentationconnectioncloseevent, event, presentation, close, console
-->

# PresentationConnectionCloseEvent: JavaScriptにおけるプレゼンテーション接続の終了イベント

## 概要
`PresentationConnectionCloseEvent`は、WebプレゼンテーションAPIにおいて、プレゼンテーション接続が閉じられた際に発生するイベントです。このイベントをリッスンすることで、プレゼンテーション接続の状態を適切に管理することができます。

## ドキュメント
### 機能
`PresentationConnectionCloseEvent`は、プレゼンテーション接続が終了したときに、関連する情報を持つイベントオブジェクトを生成します。このイベントは、接続が正常に閉じられた場合や、異常による閉鎖が発生した場合にトリガーされます。

### 使用方法
`PresentationConnectionCloseEvent`は、`PresentationConnection`オブジェクトの`close`イベントとして発生します。以下のように、イベントリスナーを設定することで、プレゼンテーション接続の終了を監視できます。

```javascript
const connection = new PresentationConnection();

connection.addEventListener('close', (event) => {
    console.log('プレゼンテーション接続が閉じられました。');
    console.log('イベント情報:', event);
});
```

### 詳細
- **プロパティ**: `PresentationConnectionCloseEvent`には、接続が閉じられた理由などの情報を含むプロパティがあります。
- **イベントの発生**: 接続が正常に終わった場合や、エラーによって強制的に終了した場合、いずれもこのイベントが発生します。
- **互換性**: WebプレゼンテーションAPIは、特定のブラウザでのみサポートされていますので、実装の前に対応ブラウザを確認することが重要です。

## 例
以下は、`PresentationConnectionCloseEvent`を使用した簡単な例です。

```javascript
const presentation = new Presentation();
presentation.addEventListener('close', (event) => {
    console.log('接続が閉じられました。理由:', event.reason);
});

// プレゼンテーションを開始するコード
presentation.start();
```

## 説明
- **一般的な落とし穴**: イベントリスナーを正しく設定しないと、接続が閉じられたことに気づかない場合があります。また、異常終了の場合には、リスナー内で適切なエラーハンドリングを行う必要があります。
- **注意点**: `PresentationConnectionCloseEvent`が発生した際には、どのようにアプリケーションの状態を更新するかを考慮することが重要です。

## 一文要約
`PresentationConnectionCloseEvent`は、WebプレゼンテーションAPIにおいて、プレゼンテーション接続が閉じられた際に発生する重要なイベントです。