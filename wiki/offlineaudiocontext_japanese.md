<!--
Meta Description: # OfflineAudioContext: JavaScriptでのオフラインオーディオ処理 ## 概要 `OfflineAudioContext`は、Web Audio APIの一部として、ブラウザ上でオーディオデータを非同期的に生成および処理するためのコンテキストです。オフラインでオーディオを...
Meta Keywords: offlineaudiocontext, offlinecontext, oscillator, javascript, const
-->

# OfflineAudioContext: JavaScriptでのオフラインオーディオ処理

## 概要
`OfflineAudioContext`は、Web Audio APIの一部として、ブラウザ上でオーディオデータを非同期的に生成および処理するためのコンテキストです。オフラインでオーディオをレンダリングし、最終的なオーディオ出力を生成するのに最適です。

## ドキュメント
### 目的
`OfflineAudioContext`は、オーディオをリアルタイムで処理するのではなく、指定された時間の間にオーディオグラフを構築し、最終的なオーディオデータを生成するために使用されます。これにより、エフェクトの適用やミキシングをオフラインで行うことが可能です。

### 使用法
`OfflineAudioContext`は次のように作成します。

```javascript
const offlineContext = new OfflineAudioContext(numberOfChannels, length, sampleRate);
```

- `numberOfChannels`: チャンネル数（モノラルは1、ステレオは2）。
- `length`: レンダリングするオーディオの長さ（サンプル単位）。
- `sampleRate`: オーディオのサンプルレート（通常は44100Hzや48000Hz）。

### 詳細
1. **オーディオグラフの構築**: `OfflineAudioContext`を使用して、入力ソース、エフェクト、さらに出力を接続してオーディオグラフを構築します。
2. **レンダリング**: `startRendering()`メソッドを呼び出すことで、オーディオをレンダリングし、`Promise`を返します。この`Promise`は、レンダリングが完了した後に生成された`AudioBuffer`を解決します。

```javascript
offlineContext.startRendering().then((audioBuffer) => {
    // オーディオデータが生成されました
});
```

## 例
以下は、`OfflineAudioContext`を使用して、オーディオサンプルを生成する基本的な例です。

```javascript
// オフラインオーディオコンテキストの作成
const offlineContext = new OfflineAudioContext(2, 44100 * 2, 44100);

// オシレーターの作成
const oscillator = offlineContext.createOscillator();
oscillator.frequency.setValueAtTime(440, 0); // A4の周波数
oscillator.start(0);

// 出力を接続
oscillator.connect(offlineContext.destination);

// レンダリング
offlineContext.startRendering().then((buffer) => {
    console.log('オーディオデータが生成されました', buffer);
});
```

## 説明
- **一般的な落とし穴**: `OfflineAudioContext`でレンダリングしたオーディオは、音声の遅延や非同期処理に関連する問題が発生しないため、リアルタイム処理との違いを理解することが重要です。
- **最大長**: オフラインコンテキストの長さは、ブラウザによって制限されることがあります。非常に長いオーディオを処理しようとすると、エラーが発生する可能性があります。

## ワンラインサマリー
`OfflineAudioContext`は、Web Audio APIの一部として、オフラインでオーディオを生成・処理するための強力なツールです。