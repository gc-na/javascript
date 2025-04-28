<!--
Meta Description: # ConvolverNode: JavaScriptでの音声信号処理の基礎 ## 概要 `ConvolverNode`は、Web Audio APIの一部であり、音声信号にリバーブ効果を追加するために使用されるノードです。このノードは、インパルス応答（IR）を基にした音響効果を実現し、リアルな音場...
Meta Keywords: convolvernode, audiocontext, buffer, audio, convolver
-->

# ConvolverNode: JavaScriptでの音声信号処理の基礎

## 概要
`ConvolverNode`は、Web Audio APIの一部であり、音声信号にリバーブ効果を追加するために使用されるノードです。このノードは、インパルス応答（IR）を基にした音響効果を実現し、リアルな音場を再現します。

## ドキュメンテーション
### 目的
`ConvolverNode`は、音声信号にリバーブ効果を与えるためのオーディオノードです。これを使用することで、ユーザーは録音した音声や楽器の音に、特定の空間的特徴を追加することができます。たとえば、ホール、スタジオ、または小さな部屋のようなエコー効果を模倣することが可能です。

### 使用方法
`ConvolverNode`は、Web Audio APIの`AudioContext`を使用して生成します。以下は基本的な使用方法です。

1. `AudioContext`を作成します。
2. `ConvolverNode`を生成します。
3. インパルス応答を`AudioBuffer`に読み込みます。
4. `ConvolverNode`にインパルス応答を設定します。
5. 音声信号を`ConvolverNode`に接続します。

### 詳細
- **プロパティ**
  - `buffer`: `AudioBuffer`オブジェクトを設定し、リバーブ効果の元となるインパルス応答を指定します。
  - `normalize`: ブール値で、`true`の場合、インパルス応答の音量を正規化します。

- **メソッド**
  - `connect()`: 他のオーディオノードに接続するためのメソッド。
  - `disconnect()`: 接続を解除するためのメソッド。

## 例
### 基本的な使用例
以下は、`ConvolverNode`を使用して簡単なリバーブ効果を追加する例です。

```javascript
// AudioContextの作成
const audioContext = new (window.AudioContext || window.webkitAudioContext)();

// ConvolverNodeの作成
const convolver = audioContext.createConvolver();

// インパルス応答をAudioBufferとして読み込む
fetch('path/to/impulse-response.wav')
  .then(response => response.arrayBuffer())
  .then(data => audioContext.decodeAudioData(data))
  .then(buffer => {
    convolver.buffer = buffer; // bufferプロパティに設定
  });

// 音声ソースを作成
const source = audioContext.createBufferSource();
// ソースに別のAudioBufferを設定（例: 音楽ファイル）
source.buffer = musicBuffer; // musicBufferは別に読み込まれたAudioBuffer

// ノードを接続
source.connect(convolver);
convolver.connect(audioContext.destination);

// 音声を再生
source.start();
```

## 説明
`ConvolverNode`を使用する際の一般的な落とし穴には、次のようなものがあります。

- **インパルス応答の長さ**: 非常に長いインパルス応答を使用すると、CPUリソースを大量に消費することがあります。適切な長さのIRを選択しましょう。
- **非同期処理**: `fetch`や`decodeAudioData`は非同期で動作するため、インパルス応答の読み込みが完了する前に音声を再生しようとすると、エラーが発生する可能性があります。
- **ブラウザの互換性**: 一部のブラウザではWeb Audio APIの実装が異なるため、動作確認が必要です。

## 一文要約
`ConvolverNode`は、Web Audio APIを使用して音声信号にリバーブ効果を追加するための強力なオーディオノードです。