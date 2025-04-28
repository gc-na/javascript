<!--
Meta Description: # DelayNode（デレイノード）: JavaScriptにおける音声処理の時間遅延 ## 概要 DelayNodeは、Web Audio APIの一部であり、音声信号に遅延を追加するためのノードです。この機能は、音楽やサウンドデザインにおいてエコーやリバーブ効果を作成する際に非常に便利です。 ...
Meta Keywords: audiocontext, delaynode, const, source, javascript
-->

# DelayNode（デレイノード）: JavaScriptにおける音声処理の時間遅延

## 概要
DelayNodeは、Web Audio APIの一部であり、音声信号に遅延を追加するためのノードです。この機能は、音楽やサウンドデザインにおいてエコーやリバーブ効果を作成する際に非常に便利です。

## ドキュメンテーション
### 目的
DelayNodeは、音声の再生に遅延を加えることで、サウンドの空間的な広がりや深みを演出します。これにより、音楽制作やゲーム音響など、多くの用途で活用されます。

### 使い方
DelayNodeを使用するためには、まずAudioContextを作成し、その中にDelayNodeを生成します。次に、音声ソースノードとDelayNodeを接続し、音声信号をDelayNodeに送ります。

### 詳細
- **生成方法**: 
  ```javascript
  const audioContext = new (window.AudioContext || window.webkitAudioContext)();
  const delayNode = audioContext.createDelay();
  ```

- **プロパティ**:
  - `delayTime`: 遅延の時間を秒単位で指定します。最大遅延時間は、通常は 20 秒です。

- **接続方法**:
  ```javascript
  const source = audioContext.createBufferSource();
  source.connect(delayNode);
  delayNode.connect(audioContext.destination);
  ```

- **遅延時間の設定**:
  ```javascript
  delayNode.delayTime.value = 0.5; // 500msの遅延
  ```

## 例
### 基本的な使用例
以下は、DelayNodeを使用して500ミリ秒の遅延を持つ音声を再生する基本的な例です。

```javascript
const audioContext = new (window.AudioContext || window.webkitAudioContext)();
const delayNode = audioContext.createDelay();
delayNode.delayTime.value = 0.5; // 500msの遅延

const source = audioContext.createBufferSource();
// バッファに音声データを設定
source.buffer = yourAudioBuffer; // あなたのオーディオバッファ
source.connect(delayNode);
delayNode.connect(audioContext.destination);
source.start();
```

## 説明
DelayNodeを使用する際の一般的な落とし穴には、遅延時間の設定が不適切であることや、音声ソースとDelayNodeの接続を忘れることがあります。また、delayTimeプロパティは、常に数値として設定する必要があります。無効な値を指定すると、期待通りに動作しません。

## 一文要約
DelayNodeは、Web Audio APIを利用して音声信号に遅延を追加するためのノードで、エコーやリバーブ効果を生み出すのに役立ちます。