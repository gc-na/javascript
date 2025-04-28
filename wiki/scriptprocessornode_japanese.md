<!--
Meta Description: # ScriptProcessorNode（スクリプトプロセッサノード）に関する詳細ガイド ## 概要 ScriptProcessorNodeは、Web Audio APIの一部であり、音声信号をリアルタイムで処理するためのノードです。このノードを利用することで、ユーザーは音声データをカスタマイズし...
Meta Keywords: const, audiocontext, scriptprocessornode, javascript, event
-->

# ScriptProcessorNode（スクリプトプロセッサノード）に関する詳細ガイド

## 概要
ScriptProcessorNodeは、Web Audio APIの一部であり、音声信号をリアルタイムで処理するためのノードです。このノードを利用することで、ユーザーは音声データをカスタマイズしたり、エフェクトを適用したりすることができます。

## ドキュメンテーション
### 目的
ScriptProcessorNodeは、オーディオデータをプログラムで処理するためのインターフェースを提供します。これにより、開発者は自分のJavaScriptコードを使って音声信号を操作できます。

### 使用方法
1. **オーディオコンテキストの作成**: ScriptProcessorNodeを使用する前に、AudioContextを作成する必要があります。
    ```javascript
    const audioContext = new (window.AudioContext || window.webkitAudioContext)();
    ```

2. **ScriptProcessorNodeの生成**: `createScriptProcessor`メソッドを使用してノードを作成します。
    ```javascript
    const scriptProcessorNode = audioContext.createScriptProcessor(bufferSize, inputChannels, outputChannels);
    ```

    - `bufferSize`: サンプル数を指定します（通常は256、512、1024など）。
    - `inputChannels`: 入力チャネルの数（通常は1または2）。
    - `outputChannels`: 出力チャネルの数（通常は1または2）。

3. **音声処理関数の定義**: `onaudioprocess`イベントリスナーを設定して、音声データにアクセスし、処理を行います。
    ```javascript
    scriptProcessorNode.onaudioprocess = function(event) {
        const inputBuffer = event.inputBuffer;
        const outputBuffer = event.outputBuffer;

        for (let channel = 0; channel < outputBuffer.numberOfChannels; channel++) {
            const inputData = inputBuffer.getChannelData(channel);
            const outputData = outputBuffer.getChannelData(channel);

            for (let sample = 0; sample < inputBuffer.length; sample++) {
                // 例: 入力信号をそのまま出力する
                outputData[sample] = inputData[sample];
            }
        }
    };
    ```

4. **ノードの接続**: AudioContextの他のノードと接続します。
    ```javascript
    const sourceNode = audioContext.createBufferSource();
    sourceNode.connect(scriptProcessorNode);
    scriptProcessorNode.connect(audioContext.destination);
    ```

5. **再生**: ソースノードを再生します。
    ```javascript
    sourceNode.start();
    ```

## 例
### 基本的な使用例
```javascript
const audioContext = new (window.AudioContext || window.webkitAudioContext)();
const scriptProcessorNode = audioContext.createScriptProcessor(256, 1, 1);

scriptProcessorNode.onaudioprocess = function(event) {
    const inputData = event.inputBuffer.getChannelData(0);
    const outputData = event.outputBuffer.getChannelData(0);

    for (let i = 0; i < inputData.length; i++) {
        outputData[i] = inputData[i] * 0.5; // 音量を半分にする
    }
};

const oscillator = audioContext.createOscillator();
oscillator.connect(scriptProcessorNode);
scriptProcessorNode.connect(audioContext.destination);
oscillator.start();
```

## 説明
### 一般的な落とし穴
- **非推奨の使用**: 現在、ScriptProcessorNodeは将来的に非推奨となる可能性があるため、AudioWorkletNodeの使用が推奨されています。新規プロジェクトではAudioWorkletNodeを検討してください。
- **パフォーマンスの問題**: 大きなバッファサイズを使用すると、遅延が増加し、リアルタイム処理が困難になる場合があります。適切なサイズを選択してください。

### 注意点
- ScriptProcessorNodeは、音声処理において便利なツールですが、特定の用途に特化しているため、他の音声処理手法と併用することが重要です。

## 一文要約
ScriptProcessorNodeは、Web Audio APIを使用したリアルタイム音声処理のためのノードで、音声データをプログラムで操作する能力を提供します。