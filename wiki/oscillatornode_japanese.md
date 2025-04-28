<!--
Meta Description: # OscillatorNode（オシレーター・ノード）: JavaScriptでの音声合成の基礎 ## 概要 `OscillatorNode`は、Web Audio APIの一部であり、音声信号を生成するためのノードです。サイン波、三角波、矩形波、ノコギリ波などの基本的な波形を生成することができま...
Meta Keywords: audiocontext, oscillatornode, oscillator, currenttime, sineoscillator
-->

# OscillatorNode（オシレーター・ノード）: JavaScriptでの音声合成の基礎

## 概要
`OscillatorNode`は、Web Audio APIの一部であり、音声信号を生成するためのノードです。サイン波、三角波、矩形波、ノコギリ波などの基本的な波形を生成することができます。

## ドキュメント
### 目的
`OscillatorNode`は、音声合成や音楽制作において、基本的な音の波形を生成するために使用されます。音声データの処理や、リアルタイムでの音声合成において重要な役割を果たします。

### 使用法
`OscillatorNode`を使用するには、まず`AudioContext`を作成し、そのコンテキストに基づいてオシレーターを生成します。以下は基本的な使用方法です。

```javascript
// AudioContextの作成
const audioContext = new (window.AudioContext || window.webkitAudioContext)();

// OscillatorNodeの作成
const oscillator = audioContext.createOscillator();

// 波形の設定
oscillator.type = 'sine'; // 'sine', 'square', 'sawtooth', or 'triangle'

// 周波数の設定
oscillator.frequency.setValueAtTime(440, audioContext.currentTime); // A4の音（440Hz）

// 出力先の設定
oscillator.connect(audioContext.destination);

// オシレーターの開始
oscillator.start();

// 一定時間後にオシレーターを停止
oscillator.stop(audioContext.currentTime + 1); // 1秒後に停止
```

### 詳細
- `type`プロパティ：生成する波形の種類を指定します。可能な値は`'sine'`, `'square'`, `'sawtooth'`, `triangle`です。
- `frequency`プロパティ：オシレーターの周波数を設定します。`setValueAtTime`メソッドを使用して、指定した時刻に値を設定できます。
- `start()`メソッド：オシレーターの生成を開始します。
- `stop()`メソッド：オシレーターの生成を停止します。

## 例
以下は、異なる波形を生成する例です。

```javascript
// サイン波のオシレーター
const sineOscillator = audioContext.createOscillator();
sineOscillator.type = 'sine';
sineOscillator.frequency.setValueAtTime(440, audioContext.currentTime);
sineOscillator.connect(audioContext.destination);
sineOscillator.start();
sineOscillator.stop(audioContext.currentTime + 1);

// 矩形波のオシレーター
const squareOscillator = audioContext.createOscillator();
squareOscillator.type = 'square';
squareOscillator.frequency.setValueAtTime(440, audioContext.currentTime);
squareOscillator.connect(audioContext.destination);
squareOscillator.start();
squareOscillator.stop(audioContext.currentTime + 1);
```

## 説明
`OscillatorNode`を使用する際の一般的な落とし穴には、オーディオコンテキストが正しく作成されていない場合や、オシレーターが停止する前に再び開始される場合が挙げられます。また、ブラウザによってはオーディオコンテキストの自動再生が制限されているため、ユーザーの操作が必要です。

## 一文要約
`OscillatorNode`は、Web Audio APIを使用して基本的な音声波形を生成するための強力なツールです。