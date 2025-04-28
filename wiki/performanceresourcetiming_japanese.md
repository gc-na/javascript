<!--
Meta Description: # PerformanceResourceTiming: JavaScriptによるリソースパフォーマンスの測定 ## 概要 `PerformanceResourceTiming`は、Webアプリケーションが外部リソース（画像、スクリプト、スタイルシートなど）を取得する際のパフォーマンスデータを取得...
Meta Keywords: resource, performanceresourcetiming, console, log, ミリ秒単位
-->

# PerformanceResourceTiming: JavaScriptによるリソースパフォーマンスの測定

## 概要
`PerformanceResourceTiming`は、Webアプリケーションが外部リソース（画像、スクリプト、スタイルシートなど）を取得する際のパフォーマンスデータを取得するためのインターフェースです。このインターフェースは、開発者がアプリケーションのロード時間やリソースの取得時間を詳細に分析するために使用されます。

## ドキュメンテーション
`PerformanceResourceTiming`は、`PerformanceEntry`のサブクラスであり、特定のリソースのパフォーマンスデータを提供します。このデータには、リソースの取得にかかった時間、開始時刻、終端時刻、HTTP ステータスコードなどが含まれます。

### 主なプロパティ
- **name**: リソースのURLを示します。
- **entryType**: エントリの種類（通常は`resource`）。
- **startTime**: リソースのリクエストが開始された時刻（ミリ秒単位）。
- **duration**: リソースの取得にかかった時間（ミリ秒単位）。
- **responseEnd**: レスポンスが完了した時刻（ミリ秒単位）。
- **fetchStart**: リソースのフェッチが開始された時刻（ミリ秒単位）。
- **connectEnd**: 接続が確立された時刻（ミリ秒単位）。
- **transferSize**: 転送されたバイト数。
- **encodedBodySize**: エンコードされたボディのサイズ。

### 使用方法
`PerformanceResourceTiming`のデータは、`performance.getEntriesByType("resource")`メソッドを使用して取得します。これにより、ページがロード中に取得されたすべてのリソースのパフォーマンスデータを集約できます。

```javascript
const resources = performance.getEntriesByType("resource");

resources.forEach((resource) => {
    console.log(`リソース名: ${resource.name}`);
    console.log(`取得時間: ${resource.duration}ms`);
});
```

## 例
以下の例は、ページが読み込まれた後にリソースのパフォーマンスデータを取得し、コンソールに表示します。

```javascript
window.addEventListener('load', () => {
    const resources = performance.getEntriesByType("resource");
    resources.forEach((resource) => {
        console.log(`リソース名: ${resource.name}`);
        console.log(`開始時刻: ${resource.startTime}ms`);
        console.log(`取得時間: ${resource.duration}ms`);
        console.log(`HTTP ステータスコード: ${resource.responseEnd}`);
    });
});
```

## 説明
`PerformanceResourceTiming`を使用する際の一般的な落とし穴や注意点には以下があります：
- **クロスオリジンリソースの制約**: 一部のリソースは、CORSポリシーにより、データの取得が制限されることがあります。これにより、`PerformanceResourceTiming`のプロパティが完全に取得できないことがあります。
- **ブラウザのサポート**: すべてのブラウザがこのAPIをサポートしているわけではありません。使用前にブラウザの互換性を確認してください。

## 一行まとめ
`PerformanceResourceTiming`は、Webアプリケーションの外部リソースのパフォーマンスデータを取得するための強力なインターフェースです。