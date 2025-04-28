<!--
Meta Description: # ConstantSourceNode（JavaScriptにおける定数ソースノード） ## 概要 ConstantSourceNodeは、Web Audio APIの一部であり、定数信号を生成するためのノードです。このノードは、音声処理や合成において、一定の振幅を持つ信号を生成する際に使用されま...
Meta Keywords: constantsource, audioctx, const, window, start
-->

# ConstantSourceNode（JavaScriptにおける定数ソースノード）

## 概要
ConstantSourceNodeは、Web Audio APIの一部であり、定数信号を生成するためのノードです。このノードは、音声処理や合成において、一定の振幅を持つ信号を生成する際に使用されます。

## ドキュメント
### 目的
ConstantSourceNodeは、一定の値（定数）である信号を生成し、他のオーディオノードに接続して使用することができます。このノードは、持続的な音や、特定のオーディオエフェクトを実現するために役立ちます。

### 使用法
ConstantSourceNodeを使用するには、まずAudioContextを作成し、その後ConstantSourceNodeを生成します。このノードは、start()およびstop()メソッドを使用して信号の生成を制御します。

```javascript
// AudioContextの作成
const audioCtx = new (window.AudioContext || window.webkitAudioContext)();

// ConstantSourceNodeの作成
const constantSource = audioCtx.createConstantSource();

// 定数値の設定（例えば、0.5）
constantSource.offset.value = 0.5;

// ノードを接続
constantSource.connect(audioCtx.destination);

// 信号の生成を開始
constantSource.start();
```

### 詳細
- **プロパティ**
  - `offset`: 生成される信号の定数値を設定するプロパティです。デフォルトは0です。
  
- **メソッド**
  - `start(when)`: 指定した時間に信号生成を開始します。
  - `stop(when)`: 指定した時間に信号生成を停止します。

- **接続**
  - ConstantSourceNodeは、他のオーディオノード（例：GainNodeやAnalyserNode）に接続して、音声の加工や分析を行うことができます。

## 例
基本的な使用例を示します。

### 例1: 定数信号の生成
```javascript
const audioCtx = new (window.AudioContext || window.webkitAudioContext)();
const constantSource = audioCtx.createConstantSource();
constantSource.offset.value = 0.8;
constantSource.connect(audioCtx.destination);
constantSource.start();
```

### 例2: 一定の信号を一時的に生成
```javascript
const audioCtx = new (window.AudioContext || window.webkitAudioContext)();
const constantSource = audioCtx.createConstantSource();
constantSource.offset.value = 0.2;
constantSource.connect(audioCtx.destination);
constantSource.start();
setTimeout(() => constantSource.stop(), 2000); // 2秒後に停止
```

## 説明
常に同じ値を出力するため、ConstantSourceNodeは非常にシンプルですが、以下の点に注意が必要です：

- **オフセットの変更**: ノードがスタートした後は、オフセットの値を変更しても、現在の信号には影響しません。信号を止めてから再度開始する必要があります。
- **複数の接続**: ConstantSourceNodeは複数のオーディオノードに接続できますが、同時に複数のConstantSourceNodeを使用することは、オーディオの混合や管理に工夫が必要です。

## 一文要約
ConstantSourceNodeは、Web Audio APIを使用して一定の信号を生成するためのノードです。