<!--
Meta Description: # AudioBufferSourceNode: JavaScriptでの音声再生の基盤 ## 概要 `AudioBufferSourceNode`は、Web Audio APIの一部であり、音声データを再生するためのノードです。このノードは、`AudioBuffer`オブジェクトに格納された音声デ...
Meta Keywords: audiocontext, audiobuffersourcenode, source, then, buffer
-->

# AudioBufferSourceNode: JavaScriptでの音声再生の基盤

## 概要
`AudioBufferSourceNode`は、Web Audio APIの一部であり、音声データを再生するためのノードです。このノードは、`AudioBuffer`オブジェクトに格納された音声データを効率的に再生するために使用されます。JavaScriptを使用して、ブラウザ上で音声アプリケーションやゲーム音楽の実装を容易にします。

## ドキュメント
`AudioBufferSourceNode`は、オーディオコンテキスト内で音声を再生するためのインターフェースを提供します。主な目的は、`AudioBuffer`に格納された音声データを再生することです。

### 使用方法
1. **AudioContextの作成**:
   最初に、`AudioContext`を作成します。これにより、音声処理のための環境が整います。
   ```javascript
   const audioContext = new (window.AudioContext || window.webkitAudioContext)();
   ```

2. **AudioBufferの読み込み**:
   音声データを`AudioBuffer`に読み込みます。通常、Fetch APIやXMLHttpRequestを使用して音声ファイルを取得し、デコードします。
   ```javascript
   fetch('path/to/audio/file.mp3')
     .then(response => response.arrayBuffer())
     .then(data => audioContext.decodeAudioData(data))
     .then(buffer => {
       // bufferに音声データが格納されます
     });
   ```

3. **AudioBufferSourceNodeの作成**:
   `AudioBufferSourceNode`を作成し、読み込んだ`AudioBuffer`を設定します。
   ```javascript
   const source = audioContext.createBufferSource();
   source.buffer = buffer; // 読み込んだAudioBufferを設定
   ```

4. **再生の開始**:
   `start()`メソッドを呼び出すことで、音声の再生を開始します。
   ```javascript
   source.connect(audioContext.destination); // 出力先に接続
   source.start();
   ```

### 詳細
- `AudioBufferSourceNode`は一度だけ再生可能であり、再生が完了すると自動的に終了します。
- ループ再生が必要な場合は、`loop`プロパティを`true`に設定します。
- 音声の再生中に音量を調整するには、`GainNode`を使用して接続することができます。

## 例
以下は、`AudioBufferSourceNode`を使用した基本的な音声再生の例です。

```javascript
const audioContext = new (window.AudioContext || window.webkitAudioContext)();

fetch('path/to/audio/file.mp3')
  .then(response => response.arrayBuffer())
  .then(data => audioContext.decodeAudioData(data))
  .then(buffer => {
    const source = audioContext.createBufferSource();
    source.buffer = buffer;
    source.connect(audioContext.destination);
    source.start();
  })
  .catch(error => console.error("Error with decoding audio data", error));
```

## 説明
`AudioBufferSourceNode`を使用する際の一般的な落とし穴として、以下の点に注意が必要です。
- `AudioBufferSourceNode`は再生後に破棄されるため、再生を再度行うには新しいノードを作成する必要があります。
- 音声データがデコードされる前に再生を開始しようとすると、エラーが発生します。必ず`decodeAudioData`のPromiseが解決された後に再生を開始してください。
- 音声のサンプルレートが`AudioContext`のサンプルレートと一致しない場合、音質に影響を与えることがあります。

## 一文要約
`AudioBufferSourceNode`は、JavaScriptのWeb Audio APIにおいて、音声データを再生するための強力なノードです。