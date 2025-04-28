<!--
Meta Description: # BackgroundFetchRecord: JavaScriptにおけるバックグラウンドフェッチの記録 ## 概要 `BackgroundFetchRecord`は、JavaScriptのバックグラウンドフェッチAPIに関連するインターフェースで、バックグラウンドでダウンロードが行われているリ...
Meta Keywords: backgroundfetchrecord, record, status, bgfetchmanager, const
-->

# BackgroundFetchRecord: JavaScriptにおけるバックグラウンドフェッチの記録

## 概要
`BackgroundFetchRecord`は、JavaScriptのバックグラウンドフェッチAPIに関連するインターフェースで、バックグラウンドでダウンロードが行われているリソースの状態を追跡するために使用されます。このAPIは、アプリケーションがユーザーのネットワーク接続に依存せずにデータを取得し、オフライン環境でも機能することを可能にします。

## ドキュメンテーション
`BackgroundFetchRecord`は、バックグラウンドでのリソース取得を管理するためのオブジェクトです。このオブジェクトは、フェッチプロセスに関する情報を提供し、完了、進行中、または失敗したリクエストの状態を確認できます。

### 主なプロパティ
- **id**: フェッチリクエストの一意の識別子。
- **status**: フェッチの現在の状態（例：`pending`, `in-progress`, `completed`, `failed`）。
- **uploadedBytes**: アップロードされたバイト数。
- **downloadedBytes**: ダウンロードされたバイト数。
- **result**: フェッチの結果（成功または失敗）。

### 使用方法
`BackgroundFetchRecord`は、`BackgroundFetchManager`を介して取得されます。通常、次のようにインスタンスを取得し、プロパティにアクセスします。

```javascript
// バックグラウンドフェッチのインスタンスを取得
const bgFetchManager = navigator.backgroundFetch;

// バックグラウンドフェッチの記録を取得
bgFetchManager.getRecords().then(records => {
    records.forEach(record => {
        console.log(`ID: ${record.id}, Status: ${record.status}`);
    });
});
```

## 例
以下に、`BackgroundFetchRecord`の基本的な使用例を示します。

```javascript
async function fetchWithBackground() {
    const bgFetchManager = navigator.backgroundFetch;

    // バックグラウンドフェッチの開始
    const registration = await bgFetchManager.fetch('my-fetch', ['/resource1', '/resource2']);

    // フェッチの記録を取得
    const records = await bgFetchManager.getRecords();

    records.forEach(record => {
        console.log(`ID: ${record.id}, Status: ${record.status}, Downloaded: ${record.downloadedBytes} bytes`);
    });
}

fetchWithBackground();
```

## 説明
`BackgroundFetchRecord`を使用する際の一般的な注意点：
- **ブラウザのサポート**: このAPIはすべてのブラウザでサポートされているわけではありません。最新のブラウザでの動作を確認することが重要です。
- **ネットワーク接続**: バックグラウンドフェッチは、ユーザーがアプリケーションを使用していない間にデータを取得するため、ネットワーク状態が変わる可能性があることを考慮する必要があります。
- **プライバシー**: ユーザーのプライバシーに配慮し、必要なデータのみを取得するよう心掛けましょう。

## 一文要約
`BackgroundFetchRecord`は、JavaScriptのバックグラウンドフェッチAPIでリソースの取得状況を管理するための重要なインターフェースです。