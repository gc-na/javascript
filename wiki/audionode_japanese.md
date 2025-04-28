<!--
Meta Description: # AudioNode：JavaScriptにおけるオーディオノードの完全ガイド ## 概要 AudioNodeは、Web Audio APIにおける基本的なオーディオ処理の構成要素です。このインターフェースは、オーディオ信号の生成、処理、操作を行うための機能を提供します。 ## ドキュメンテーショ...
Meta Keywords: audiocontext, oscillator, const, javascript, audionodeは
-->

# AudioNode：JavaScriptにおけるオーディオノードの完全ガイド

## 概要
AudioNodeは、Web Audio APIにおける基本的なオーディオ処理の構成要素です。このインターフェースは、オーディオ信号の生成、処理、操作を行うための機能を提供します。

## ドキュメンテーション
AudioNodeは、Web Audio APIの中心的な要素であり、音声の生成や操作を行うためのインターフェースです。AudioNodeは、オーディオコンテキストの中で、オーディオデータを処理するノードとして機能します。主な目的は、オーディオ信号の流れを制御し、様々なオーディオエフェクトを適用することです。

### 使用方法
AudioNodeは、次のように使用されます。

1. **AudioContextの作成**  
   ```javascript
   const audioContext = new AudioContext();
   ```

2. **ノードの生成**  
   ```javascript
   const oscillator = audioContext.createOscillator();
   ```

3. **ノードの接続**  
   ```javascript
   oscillator.connect(audioContext.destination);
   ```

4. **ノードの開始**  
   ```javascript
   oscillator.start();
   ```

### 詳細
AudioNodeにはさまざまな派生クラスがあり、それぞれ異なる機能を持っています。例えば、`GainNode`は音量を調整するためのノードであり、`BiquadFilterNode`は音質を変更するためのフィルターノードです。これらのノードを組み合わせることで、複雑なオーディオ処理が可能になります。

## 例
以下は、基本的なAudioNodeの使用例です。

### オシレーターの例
```javascript
const audioContext = new AudioContext();
const oscillator = audioContext.createOscillator();
oscillator.type = 'sine'; // オシレーターの波形を指定
oscillator.frequency.setValueAtTime(440, audioContext.currentTime); // 周波数を設定
oscillator.connect(audioContext.destination);
oscillator.start();
```

### ゲインノードの例
```javascript
const audioContext = new AudioContext();
const gainNode = audioContext.createGain();
gainNode.gain.setValueAtTime(0.5, audioContext.currentTime); // 音量を0.5に設定

const oscillator = audioContext.createOscillator();
oscillator.connect(gainNode);
gainNode.connect(audioContext.destination);
oscillator.start();
```

## 説明
AudioNodeを使用する際の一般的な落とし穴には、以下の点があります。

- **オーディオコンテキストの状態**: オーディオコンテキストが「suspended」状態の場合、ノードを開始できません。`audioContext.resume()`を呼び出して、コンテキストを再開させる必要があります。
- **ノードの接続**: ノードは正しい順序で接続する必要があります。接続を忘れると、音が再生されません。
- **ブラウザの互換性**: Web Audio APIは、すべてのブラウザで同じようにサポートされているわけではないため、対応状況を確認することが重要です。

## 一行要約
AudioNodeは、Web Audio APIにおけるオーディオ処理の基本的な構成要素であり、音声の生成や操作を行うために使用されます。