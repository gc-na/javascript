<!--
Meta Description: # PerformanceTiming: JavaScriptによるウェブパフォーマンスの測定 ## 概要 `PerformanceTiming`は、ウェブページの読み込み時間やパフォーマンスを測定するために使用されるJavaScript APIです。このオブジェクトは、ページのライフサイクルにおけ...
Meta Keywords: performancetiming, timing, performance, const, javascript
-->

# PerformanceTiming: JavaScriptによるウェブパフォーマンスの測定

## 概要
`PerformanceTiming`は、ウェブページの読み込み時間やパフォーマンスを測定するために使用されるJavaScript APIです。このオブジェクトは、ページのライフサイクルにおけるさまざまなタイミングデータを提供し、開発者がパフォーマンスを最適化するための重要な情報を得る手助けをします。

## ドキュメンテーション
`PerformanceTiming`は、Web Performance APIの一部であり、ブラウザがページの読み込みに関して記録した各種タイミングを提供します。これにより、ページの読み込みプロセス全体を分析し、最適化の手がかりを得ることができます。

### 目的
`PerformanceTiming`は、ページの読み込みにかかる各ステップの時間を測定し、開発者がボトルネックを特定し、パフォーマンスを向上させるためのデータを提供します。

### 使用方法
`PerformanceTiming`オブジェクトは、`performance`オブジェクトを介してアクセスできます。以下のように取得できます。

```javascript
const timing = performance.timing;
```

### 詳細
`PerformanceTiming`には、以下のような重要なプロパティがあります：

- `navigationStart`: ページのナビゲーションが開始された時間。
- `unloadEventStart`: 前のページのアンロードイベントが始まった時間。
- `unloadEventEnd`: 前のページのアンロードイベントが完了した時間。
- `redirectStart`: ページのリダイレクトが始まった時間。
- `redirectEnd`: ページのリダイレクトが完了した時間。
- `fetchStart`: リソースの取得が開始された時間。
- `domainLookupStart`: ドメイン名の解決が開始された時間。
- `domainLookupEnd`: ドメイン名の解決が完了した時間。
- `connectStart`: サーバーへの接続が開始された時間。
- `connectEnd`: サーバーへの接続が完了した時間。
- `requestStart`: リクエストが開始された時間。
- `responseEnd`: サーバーからのレスポンスが完了した時間。
- `domLoading`: DOMの読み込みが開始された時間。
- `domInteractive`: DOMの操作が可能になった時間。
- `domContentLoadedEventStart`: DOMContentLoadedイベントが開始された時間。
- `domContentLoadedEventEnd`: DOMContentLoadedイベントが完了した時間。
- `loadEventStart`: ページのloadイベントが開始された時間。
- `loadEventEnd`: ページのloadイベントが完了した時間。

## 例
以下は、`PerformanceTiming`を使用してページの読み込み時間を計測する基本的な例です。

```javascript
window.onload = function() {
    const timing = performance.timing;

    const pageLoadTime = timing.loadEventEnd - timing.navigationStart;
    console.log("ページの読み込み時間: " + pageLoadTime + "ミリ秒");
};
```

このコードは、ページが完全に読み込まれた後に、読み込みにかかった時間を計算し、コンソールに表示します。

## 説明
`PerformanceTiming`を使用する際の一般的な落とし穴には、以下のようなものがあります：

- **ブラウザの互換性**: 一部の古いブラウザでは、`PerformanceTiming`がサポートされていないことがあります。使用する前にブラウザの互換性を確認してください。
- **非同期処理**: 読み込み時間を正確に計測するためには、`window.onload`や`DOMContentLoaded`イベントを適切に利用することが重要です。
- **データの解釈**: 各プロパティの意味を理解しないと、タイミングデータを誤解する可能性があります。特に、リダイレクトや接続の遅延など、異なる要因が全体の読み込み時間に影響を与えることがあります。

## 一文要約
`PerformanceTiming`は、ウェブページの読み込み時間を測定し、パフォーマンス最適化のためのデータを提供するJavaScriptのAPIです。