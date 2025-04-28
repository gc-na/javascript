<!--
Meta Description: # PerformanceServerTiming: JavaScript におけるパフォーマンス測定の新機能 ## 概要 `PerformanceServerTiming` は、Web パフォーマンスを測定するための API で、サーバーからの応答時間を詳細に分析することを可能にします。これにより...
Meta Keywords: performanceservertiming, server, timing, javascript, dur
-->

# PerformanceServerTiming: JavaScript におけるパフォーマンス測定の新機能

## 概要
`PerformanceServerTiming` は、Web パフォーマンスを測定するための API で、サーバーからの応答時間を詳細に分析することを可能にします。これにより、開発者はアプリケーションのパフォーマンスを向上させるための貴重な情報を得ることができます。

## ドキュメンテーション
`PerformanceServerTiming` は、サーバーが応答を返す際に、サーバー側の処理時間を測定するための機能です。これにより、クライアント側でのパフォーマンス分析が可能となり、特にバックエンド処理がボトルネックとなっている場合に有用です。

### 目的
- サーバーの応答時間を把握することで、パフォーマンスの最適化ができる。
- フロントエンドとバックエンドのパフォーマンスを総合的に分析するためのデータを提供する。

### 使い方
`PerformanceServerTiming` は、HTTP レスポンスヘッダーとして追加される `Server-Timing` ヘッダーを介して使用されます。以下の構文を使用して、サーバー側からの応答時間を指定します。

```http
Server-Timing: <metric-name>;dur=<duration>;desc="<description>"
```

### 詳細
- `<metric-name>`: 測定の名前。任意の文字列を使用可能。
- `<duration>`: 測定にかかった時間 (ミリ秒)。
- `<description>`: 測定の詳細を説明する文字列。

クライアント側では、`performance.getEntriesByType('navigation')` を使用して、これらのサーバータイミングメトリクスを取得することができます。

## 例
### サーバー側の設定例
以下の例は、Node.js を使用したサーバー側の設定です。

```javascript
response.setHeader('Server-Timing', 'db;dur=53;desc="Database Search", cache;dur=47;desc="Cache Lookup"');
response.send('Hello, world!');
```

### クライアント側の取得例
クライアント側での取得方法の例は以下の通りです。

```javascript
const navEntries = performance.getEntriesByType('navigation');
navEntries.forEach(entry => {
    console.log(entry.serverTiming);
});
```

## 解説
- **一般的な落とし穴**: `Server-Timing` ヘッダーを適切に設定しないと、クライアント側で正確なデータが得られない場合があります。
- **互換性**: 現在、主要なブラウザはこの機能をサポートしていますが、古いブラウザでは動作しない可能性があります。
- **パフォーマンスへの影響**: 過剰なメトリクスの追加は、サーバーのレスポンス時間に影響を及ぼす可能性があるため、必要なものだけを指定することが推奨されます。

## 一文要約
`PerformanceServerTiming` は、サーバーの応答時間を測定し、Web アプリケーションのパフォーマンスを最適化するための重要なツールです。