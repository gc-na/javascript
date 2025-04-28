<!--
Meta Description: # StereoPannerNode: JavaScriptにおけるステレオパンナーの使い方 ## 概要 StereoPannerNodeは、Web Audio APIの一部であり、音声信号をステレオの左右にパン（配置）するためのノードです。これにより、ユーザーは音源の位置をリアルタイムで制御し、立...
Meta Keywords: audiocontext, stereopannernodeは, source, panner, connect
-->

# StereoPannerNode: JavaScriptにおけるステレオパンナーの使い方

## 概要
StereoPannerNodeは、Web Audio APIの一部であり、音声信号をステレオの左右にパン（配置）するためのノードです。これにより、ユーザーは音源の位置をリアルタイムで制御し、立体的な音場を作り出すことができます。

## ドキュメンテーション
### 目的
StereoPannerNodeは、音声信号のステレオ配置を調整するために使用されます。これにより、オーディオの空間的な広がりや方向をコントロールでき、より没入感のある音体験を提供します。

### 使用法
StereoPannerNodeは、AudioContextオブジェクトから作成されます。ノードは、パンの位置を指定するためのプロパティやメソッドを持っています。

#### プロパティ
- **pan**: 音声のパンニング位置を示す値で、-1.0（左）から1.0（右）の範囲で設定します。

#### メソッド
- **connect(destination)**: コンテキスト内の他のノードに接続します。
- **disconnect(destination)**: 接続を切断します。

### 基本的な使用例
以下は、StereoPannerNodeの基本的な使用例です。

```javascript
// AudioContextの作成
const audioContext = new (window.AudioContext || window.webkitAudioContext)();

// AudioBufferSourceNodeの作成
const source = audioContext.createBufferSource();

// StereoPannerNodeの作成
const panner = audioContext.createStereoPanner();

// 音源データの読み込み（例: audioDataはAudioBuffer）
source.buffer = audioData;

// パンの設定
panner.pan.value = -1.0; // 左にパン

// ノードの接続
source.connect(panner);
panner.connect(audioContext.destination);

// 音声の再生
source.start();
```

## 説明
StereoPannerNodeを使用する際の一般的な落とし穴には、以下の点が含まれます。

- **音声信号の遅延**: パンニングを行うと、音声信号が遅延することがあります。特に複数のノードを連結する場合、遅延を考慮する必要があります。
- **パンの範囲の理解**: panプロパティの値は-1.0から1.0の範囲であるため、適切な値を設定することが重要です。値が範囲外の場合、意図した結果にならないことがあります。
- **ブラウザの互換性**: StereoPannerNodeはすべてのブラウザでサポートされているわけではないため、使用前に互換性を確認する必要があります。

## 一文要約
StereoPannerNodeは、Web Audio APIを利用して音声信号の左右のパンニングを制御するためのノードです。