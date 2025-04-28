<!--
Meta Description: # IIRFilterNode（JavaScriptにおけるIIRフィルターノード） ## 概要 IIRFilterNodeは、Web Audio APIの一部であり、デジタル信号処理におけるInfinite Impulse Response（IIR）フィルタを実装するためのノードです。このノードを...
Meta Keywords: const, audiocontext, iirfilternode, feedback, feedforward
-->

# IIRFilterNode（JavaScriptにおけるIIRフィルターノード）

## 概要
IIRFilterNodeは、Web Audio APIの一部であり、デジタル信号処理におけるInfinite Impulse Response（IIR）フィルタを実装するためのノードです。このノードを使用することで、音声信号の周波数特性を調整し、特定の音を強調したり、不要な周波数を除去したりすることができます。

## ドキュメント
### 目的
IIRFilterNodeは、音声処理において高い柔軟性と効率を提供します。主に、音楽や音声のミキシング、エフェクトの適用、音質の調整に利用されます。このノードは、フィルタの係数を直接設定することで、さまざまなフィルタリング効果を実現します。

### 使用方法
IIRFilterNodeを使用するには、まずAudioContextオブジェクトを作成し、次にIIRFilterNodeを生成します。以下は、IIRフィルタノードの基本的な作成手順です。

```javascript
// AudioContextの作成
const audioContext = new (window.AudioContext || window.webkitAudioContext)();

// フィルタ係数の定義
const feedback = [1, -0.9]; // フィードバック係数
const feedforward = [0.1]; // フィードフォワード係数

// IIRFilterNodeの作成
const iirFilterNode = audioContext.createIIRFilter(feedforward, feedback);

// 音源を接続
const source = audioContext.createBufferSource();
// ここで音源を設定（例: audioContext.decodeAudioDataを使用）

source.connect(iirFilterNode);
iirFilterNode.connect(audioContext.destination);

// 音源を再生
source.start();
```

### 詳細
- **フィードバックとフィードフォワード**: IIRFilterNodeでは、フィルタの特性を決定するために、フィードバックとフィードフォワードの係数を指定する必要があります。
- **フィルタタイプ**: IIRフィルタには、ローパス、ハイパス、バンドパスなどがあります。これらのフィルタを適切に設計することで、特定の周波数帯域を強調または抑制できます。
- **パフォーマンス**: IIRフィルタは、FIRフィルタに比べて計算コストが低く、高速に動作しますが、安定性を注意深く管理する必要があります。

## 例
### 基本的なIIRフィルタの使用例

```javascript
const audioContext = new (window.AudioContext || window.webkitAudioContext)();
const feedback = [1, -0.5];
const feedforward = [0.5];

const iirFilterNode = audioContext.createIIRFilter(feedforward, feedback);
const oscillator = audioContext.createOscillator();

oscillator.connect(iirFilterNode);
iirFilterNode.connect(audioContext.destination);

oscillator.start();
```

### ハイパスフィルタの例

```javascript
const feedforward = [0, -0.5];
const feedback = [1, -0.5];

const highPassFilter = audioContext.createIIRFilter(feedforward, feedback);
```

## 説明
IIRFilterNodeを使用する際の一般的な落とし穴は、フィルタ係数の設計の難しさです。適切な係数を選ばないと、音質が劣化したり、フィルタが不安定になったりする可能性があります。また、IIRフィルタは過去の出力に依存するため、初期条件の設定も重要です。これにより、フィルタの応答が変化することがあります。

## 一行要約
IIRFilterNodeは、Web Audio APIでデジタル信号処理を行うための強力なツールであり、音声信号の周波数特性を柔軟に調整できるノードです。