<!--
Meta Description: # PeriodicWave: JavaScriptにおける周期波の作成と利用 ## 概要 PeriodicWaveは、Web Audio APIの一部であり、音波の周期的な波形を表現するためのオブジェクトです。このオブジェクトを使用することで、複雑な音声合成や音響効果を簡単に行うことができます。 ...
Meta Keywords: audiocontext, const, real, imaginary, periodicwaveは
-->

# PeriodicWave: JavaScriptにおける周期波の作成と利用

## 概要
PeriodicWaveは、Web Audio APIの一部であり、音波の周期的な波形を表現するためのオブジェクトです。このオブジェクトを使用することで、複雑な音声合成や音響効果を簡単に行うことができます。

## ドキュメンテーション
### 目的
PeriodicWaveは、音の波形を定義し、AudioNodeに渡すことで、音声合成を行うための機能を提供します。これにより、ユーザーは独自の音波を作成し、音楽やサウンドデザインに応用できます。

### 使用法
PeriodicWaveを使用するには、まずAudioContextを作成し、その中でPeriodicWaveオブジェクトを生成します。次に、AudioNode（例：OscillatorNode）にこの波形を適用します。

#### 基本的な構文
```javascript
const audioContext = new AudioContext();
const periodicWave = audioContext.createPeriodicWave(real, imaginary);
```

- `real`: 周期波の実部を定義するFloat32Array。
- `imaginary`: 周期波の虚部を定義するFloat32Array（省略可能）。

### 詳細
- **real**と**imaginary**は、波形の特性を決定します。これらの配列は、音の高さや音色に影響を与えます。
- PeriodicWaveは、オシレーターと組み合わせて使用することが一般的です。
- Web Audio APIの他の機能と連携することで、リアルタイム音声処理が可能です。

## 例
以下に、PeriodicWaveを使用した基本的な例を示します。

### 例1: 単純な周期波の作成
```javascript
const audioContext = new AudioContext();
const real = new Float32Array([0, 1, 0, 0]); // 実部
const imaginary = new Float32Array([0, 0, 0, 0]); // 虚部

const periodicWave = audioContext.createPeriodicWave(real, imaginary);
const oscillator = audioContext.createOscillator();

oscillator.setPeriodicWave(periodicWave);
oscillator.frequency.setValueAtTime(440, audioContext.currentTime); // A4の音
oscillator.connect(audioContext.destination);
oscillator.start();
```

## 説明
- **共通の落とし穴**: `real`および`imaginary`の配列は、必ず同じ長さでなければなりません。長さが異なる場合、エラーが発生します。
- **サポートされているブラウザ**: PeriodicWaveは、最新の主要なブラウザでサポートされていますが、古いバージョンのブラウザでは動作しない可能性があります。
- **パフォーマンス**: 複雑な波形を生成する場合、計算が重くなることがありますので、パフォーマンスに注意が必要です。

## 一文の要約
PeriodicWaveは、Web Audio APIを利用してカスタム音波を生成し、音声合成を行うための強力なツールです。