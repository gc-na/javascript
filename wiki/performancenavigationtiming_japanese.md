<!--
Meta Description: # PerformanceNavigationTiming: JavaScriptにおけるパフォーマンス測定の最前線 ## 概要 `PerformanceNavigationTiming`は、Webページのナビゲーションに関連する詳細なパフォーマンスデータを提供するWeb APIです。このAPIを使...
Meta Keywords: performancenavigationtiming, navigationtiming, console, log, apiです
-->

# PerformanceNavigationTiming: JavaScriptにおけるパフォーマンス測定の最前線

## 概要
`PerformanceNavigationTiming`は、Webページのナビゲーションに関連する詳細なパフォーマンスデータを提供するWeb APIです。このAPIを使用することで、開発者はページの読み込み時間やリダイレクトの回数など、ナビゲーションに関するメトリクスを取得できます。

## ドキュメント
### 目的
`PerformanceNavigationTiming`は、ブラウザでページがどのように読み込まれるかを測定し、パフォーマンスの向上に役立てるためのデータを提供します。これにより、Webアプリケーションの効率を分析し、ユーザーエクスペリエンスを向上させることが可能になります。

### 使用法
`PerformanceNavigationTiming`は、`performance.getEntriesByType("navigation")`メソッドを使用して取得します。このメソッドは、ナビゲーションに関するパフォーマンスエントリを配列として返します。

#### 基本的なプロパティ
- `startTime`: ページが最初に要求された時刻。
- `redirectCount`: リダイレクトの回数。
- `domContentLoadedEventEnd`: DOMコンテンツが読み込まれた時刻。
- `loadEventEnd`: ページ全体が読み込まれた時刻。

### 詳細な使用例
以下は、`PerformanceNavigationTiming`を使用してページのパフォーマンスを測定する基本的な例です。

```javascript
window.onload = function() {
    const [navigationTiming] = performance.getEntriesByType("navigation");

    console.log("ページが読み込まれるまでの時間:", navigationTiming.loadEventEnd - navigationTiming.startTime, "ミリ秒");
    console.log("リダイレクトの回数:", navigationTiming.redirectCount);
    console.log("DOMContentLoadedイベントの終了時刻:", navigationTiming.domContentLoadedEventEnd, "ミリ秒");
};
```

## 説明
### 共通の落とし穴
- **ブラウザの互換性**: 一部の古いブラウザでは、`PerformanceNavigationTiming`がサポートされていない場合があります。これにより、予期しない動作が発生する可能性があります。
- **データの取得タイミング**: ページが完全に読み込まれる前にデータを取得すると、正確なメトリクスが得られないことがあります。`window.onload`を使用して、ページの読み込みが完了してからデータを取得することが推奨されます。

### 追加の注意点
- `PerformanceNavigationTiming`は、ページナビゲーションに関する詳細な情報を提供しますが、他のパフォーマンスAPI（例えば、`PerformanceResourceTiming`）と組み合わせて使用することで、より包括的なパフォーマンス分析が可能です。
- 開発中の環境では、パフォーマンスデータが正確でない場合があります。実際のユーザー環境での測定が重要です。

## 一行要約
`PerformanceNavigationTiming`は、Webページのナビゲーションパフォーマンスを詳細に測定するためのJavaScript APIです。