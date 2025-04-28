<!--
Meta Description: # OfflineAudioCompletionEvent（オフラインオーディオ完了イベント）に関するJavaScriptの詳細ガイド ## 概要 `OfflineAudioCompletionEvent`は、Web Audio APIの一部であり、オフラインオーディオ処理が完了した際に発生するイベ...
Meta Keywords: offlineaudiocompletionevent, offlinecontext, renderedbuffer, oscillator, offlineaudiocontext
-->

# OfflineAudioCompletionEvent（オフラインオーディオ完了イベント）に関するJavaScriptの詳細ガイド

## 概要
`OfflineAudioCompletionEvent`は、Web Audio APIの一部であり、オフラインオーディオ処理が完了した際に発生するイベントです。このイベントは、オフラインオーディオコンテキストの音声処理が終了した後に、生成されたオーディオバッファを取得するために使用されます。

## ドキュメンテーション
`OfflineAudioCompletionEvent`は、`OfflineAudioContext`の`oncomplete`イベントリスナーに関連付けられます。このイベントは、オフラインオーディオ処理が完了したときにトリガーされ、生成されたオーディオデータを含む`renderedBuffer`プロパティを持つオブジェクトとして提供されます。

### 目的
- オフラインオーディオ処理の完了を検知する。
- 処理結果のオーディオバッファを取得する。

### 使用法
1. `OfflineAudioContext`を作成します。
2. 必要な音声処理を行います。
3. `startRendering()`メソッドを呼び出します。
4. `oncomplete`イベントリスナーを設定し、`OfflineAudioCompletionEvent`を取得します。

### 詳細
`OfflineAudioCompletionEvent`のプロパティには以下があります：
- `renderedBuffer`: 処理が完了したオーディオデータを含む`AudioBuffer`オブジェクト。

## 例
以下は、`OfflineAudioCompletionEvent`を使用する基本的な例です。

```javascript
// オフラインオーディオコンテキストの作成
const offlineContext = new OfflineAudioContext(2, 44100 * 40, 44100);

// 音声ソースの設定
const oscillator = offlineContext.createOscillator();
oscillator.frequency.setValueAtTime(440, 0); // 440Hzの音を生成
oscillator.start(0);
oscillator.stop(offlineContext.length / offlineContext.sampleRate);

// 音声をオフラインコンテキストに接続
oscillator.connect(offlineContext.destination);

// レンダリング開始
offlineContext.startRendering().then((renderedBuffer) => {
    // オフライン処理が完了したときの処理
    console.log("Rendering complete. Buffer length:", renderedBuffer.length);
});
```

## 説明
`OfflineAudioCompletionEvent`を利用する際の一般的な注意点:
- `startRendering()`メソッドが呼ばれると、オフラインオーディオ処理が開始されますが、適切な音声ソースやエフェクトが設定されていないと、期待する結果が得られない場合があります。
- イベントリスナーは、必ず`startRendering()`を呼び出す前に設定してください。さもないと、イベントがトリガーされない可能性があります。
- `renderedBuffer`のサンプルレートやチャンネル数は、`OfflineAudioContext`で設定したものと一致します。

## 一文要約
`OfflineAudioCompletionEvent`は、オフラインオーディオ処理が完了した際に発生し、生成されたオーディオデータを取得するために使用されるイベントです。