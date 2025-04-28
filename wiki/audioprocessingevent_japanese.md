<!--
Meta Description: # AudioProcessingEvent に関する完全ガイド：JavaScriptでのオーディオ処理イベント ## 概要 `AudioProcessingEvent` は、Web Audio API の一部であり、リアルタイムオーディオ処理を可能にするイベントです。このイベントは、スクリプトプロ...
Meta Keywords: audioprocessingevent, inputbuffer, const, audiocontext, channel
-->

# AudioProcessingEvent に関する完全ガイド：JavaScriptでのオーディオ処理イベント

## 概要
`AudioProcessingEvent` は、Web Audio API の一部であり、リアルタイムオーディオ処理を可能にするイベントです。このイベントは、スクリプトプロセッサノード（`ScriptProcessorNode`）によって生成され、音声データの処理や分析を行う際に使用されます。

## ドキュメント
`AudioProcessingEvent` は、オーディオデータの処理を行う際に発生するイベントで、以下のプロパティを持っています：

- **inputBuffer**: `AudioBuffer` オブジェクトで、現在の入力オーディオデータを含みます。
- **outputBuffer**: `AudioBuffer` オブジェクトで、処理したオーディオデータを格納するためのバッファです。
- **playbackTime**: オーディオの再生時間を示す、現在の再生位置（秒）。

### 使用方法
`AudioProcessingEvent` は、`ScriptProcessorNode` の `onaudioprocess` イベントハンドラ内で利用されます。以下の手順で使用できます：

1. `AudioContext` を生成します。
2. `ScriptProcessorNode` を作成します。
3. `onaudioprocess` イベントを設定し、`AudioProcessingEvent` を処理します。

## 例
以下は、`AudioProcessingEvent` を使用した基本的な例です：

```javascript
// AudioContextの作成
const audioContext = new (window.AudioContext || window.webkitAudioContext)();

// ScriptProcessorNodeの作成
const scriptNode = audioContext.createScriptProcessor(4096, 1, 1);

// onAudioProcess イベントの設定
scriptNode.onaudioprocess = (event) => {
    const inputBuffer = event.inputBuffer;   // 入力バッファ
    const outputBuffer = event.outputBuffer; // 出力バッファ

    // オーディオデータの処理（例：全てのサンプルを2倍にする）
    for (let channel = 0; channel < inputBuffer.numberOfChannels; channel++) {
        const inputData = inputBuffer.getChannelData(channel);
        const outputData = outputBuffer.getChannelData(channel);
        
        for (let sample = 0; sample < inputBuffer.length; sample++) {
            outputData[sample] = inputData[sample] * 2; // 音量を2倍にする
        }
    }
};

// AudioContextにノードを接続
scriptNode.connect(audioContext.destination);
```

## 説明
`AudioProcessingEvent` を使用する際の注意点：

- `ScriptProcessorNode` は、非推奨となっており、将来的には `AudioWorklet` への移行が推奨されています。`AudioWorklet` は、より効率的で柔軟なオーディオ処理を提供します。
- イベントが発生する頻度が高いため、パフォーマンスに影響を与えないように、処理の内容を最適化することが重要です。
- 同期処理が行われるため、処理が重い場合は音質に影響が出る可能性があります。

## 一文要約
`AudioProcessingEvent` は、Web Audio API におけるオーディオデータのリアルタイム処理を可能にするイベントです。