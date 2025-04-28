<!--
Meta Description: # AudioScheduledSourceNode: JavaScriptでの音声スケジューリングの基礎 ## 概要 `AudioScheduledSourceNode`は、Web Audio APIの一部であり、オーディオデータをスケジュールし、再生するための基本的なノードです。このノードは、音...
Meta Keywords: audioscheduledsourcenode, audiocontext, audio, start, number
-->

# AudioScheduledSourceNode: JavaScriptでの音声スケジューリングの基礎

## 概要
`AudioScheduledSourceNode`は、Web Audio APIの一部であり、オーディオデータをスケジュールし、再生するための基本的なノードです。このノードは、音声の生成や再生を制御するための重要な機能を提供します。

## ドキュメンテーション
`AudioScheduledSourceNode`は、音声の再生を管理し、特定の時間に音声を再生するために利用されます。このノードは、サウンドの生成元として機能し、音声信号を処理するための様々なサブクラス（例：`AudioBufferSourceNode`や`ConstantSourceNode`）を持っています。

### 主な目的と使用法
1. **音声データのスケジューリング**: 音声を特定の時間に再生することができ、音楽制作やゲーム開発などで重要です。
2. **再生の制御**: 音声の開始、停止、再生位置の変更などをプログラム的に制御できます。

### 詳細
- **プロパティ**:
  - `context`: このノードが属するオーディオコンテキストを取得します。
  - `start()`: 指定した時間から音声を再生開始します。
  - `stop()`: 音声の再生を停止します。

- **メソッド**:
  - `start(when: number, offset?: number, duration?: number)`: 音声を指定された時間に開始します。
  - `stop(when: number)`: 指定された時間に音声の再生を停止します。

## 例
以下は、`AudioBufferSourceNode`を使用して音声をスケジュールする基本的な例です。

```javascript
// オーディオコンテキストの作成
const audioContext = new (window.AudioContext || window.webkitAudioContext)();

// オーディオバッファの読み込み
fetch('path/to/audio/file.mp3')
  .then(response => response.arrayBuffer())
  .then(data => audioContext.decodeAudioData(data))
  .then(buffer => {
    // AudioBufferSourceNodeの作成
    const source = audioContext.createBufferSource();
    source.buffer = buffer;

    // 音声の再生開始
    source.start(0);
    
    // 音声の再生停止
    source.stop(audioContext.currentTime + 5); // 5秒後に停止
  })
  .catch(error => console.error('Error with decoding audio data', error));
```

## 説明
`AudioScheduledSourceNode`を使用する際の一般的な落とし穴には、音声の再生タイミングの誤設定、音声データの準備不足、またはオーディオコンテキストの状態（例：ユーザーの操作が必要な状態）などがあります。これらを考慮し、しっかりとエラーハンドリングを行うことが重要です。

音声の再生時間やオフセットを正確に設定することも重要です。`start()`メソッドを使用する際は、音声の準備が完全に整ってから呼び出すようにしてください。

## 一文要約
`AudioScheduledSourceNode`は、Web Audio APIを利用して音声をスケジュールし、再生を制御するための基本的なノードです。