<!--
Meta Description: # AudioContextとは？JavaScriptにおける音声処理の基礎 ## 概要 `AudioContext`は、Web Audio APIの中心的なオブジェクトであり、音声の生成、処理、再生を行うための機能を提供します。これにより、開発者は高品質な音声アプリケーションを構築することができま...
Meta Keywords: audiocontext, audioctx, oscillator, const, web
-->

# AudioContextとは？JavaScriptにおける音声処理の基礎

## 概要
`AudioContext`は、Web Audio APIの中心的なオブジェクトであり、音声の生成、処理、再生を行うための機能を提供します。これにより、開発者は高品質な音声アプリケーションを構築することができます。

## ドキュメンテーション

### 目的
`AudioContext`は、音声処理を行うためのコンテキストを提供します。これを利用することで、音声データの操作、エフェクトの追加、音声の再生などを行うことが可能です。

### 使用方法
`AudioContext`を使用するには、まず新しいインスタンスを作成します。以下は基本的な構文です。

```javascript
const audioCtx = new AudioContext();
```

### 詳細
- **プロパティ**
  - `sampleRate`: オーディオデータのサンプリングレートを取得します。
  - `state`: 現在のオーディオコンテキストの状態（"suspended", "running", "closed"）を取得します。
  
- **メソッド**
  - `resume()`: 一時停止中のオーディオコンテキストを再開します。
  - `suspend()`: オーディオコンテキストを一時停止します。
  - `close()`: オーディオコンテキストを閉じます。

## 例

### 基本的な使用例

```javascript
// AudioContextの作成
const audioCtx = new AudioContext();

// オシレーターの作成
const oscillator = audioCtx.createOscillator();
oscillator.type = 'sine'; // 波形のタイプ
oscillator.frequency.setValueAtTime(440, audioCtx.currentTime); // A4音の周波数
oscillator.connect(audioCtx.destination); // 出力先を接続

// 音を再生
oscillator.start();
oscillator.stop(audioCtx.currentTime + 2); // 2秒後に停止
```

## 説明

### 一般的な落とし穴
- **オーディオコンテキストの状態**: `AudioContext`を作成した直後に音を再生しようとすると、特にモバイルデバイスでは、ユーザーの操作なしに音声が再生されない場合があります。ユーザーのインタラクション（クリックなど）を待ってから再生してください。

- **非同期処理の理解**: 音声データの読み込みや処理には非同期操作が多く含まれます。Promiseやasync/awaitを使用して、音声データのロードを管理することが重要です。

## 一文の要約
`AudioContext`は、Web Audio APIを通じて高品質な音声処理を実現するための中心的なオブジェクトです。