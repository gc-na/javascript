<!--
Meta Description: # SpeechSynthesis: JavaScriptによる音声合成の活用法 ## 概要 SpeechSynthesisは、Web Speech APIの一部であり、JavaScriptを使用して音声を合成する機能を提供します。この機能を利用することで、ユーザーはテキストを音声に変換し、インタラ...
Meta Keywords: speechsynthesis, utterance, window, speechsynthesisutterance, speak
-->

# SpeechSynthesis: JavaScriptによる音声合成の活用法

## 概要
SpeechSynthesisは、Web Speech APIの一部であり、JavaScriptを使用して音声を合成する機能を提供します。この機能を利用することで、ユーザーはテキストを音声に変換し、インタラクティブなアプリケーションやウェブサイトを作成することができます。

## ドキュメント
### 目的
SpeechSynthesis APIは、音声合成を通じてウェブアプリケーションに音声機能を追加することを目的としています。これにより、視覚障害のあるユーザーや、音声で情報を受け取ることを好むユーザーに向けて、よりアクセシブルな体験を提供できます。

### 使用方法
SpeechSynthesis APIを使用するには、まず`window.speechSynthesis`オブジェクトを使用して音声合成機能にアクセスします。次に、`SpeechSynthesisUtterance`オブジェクトを作成し、読み上げるテキストを指定します。最後に、`speechSynthesis.speak()`メソッドを呼び出して音声を再生します。

### 詳細
- **音声の選択**: 利用可能な音声は、`speechSynthesis.getVoices()`メソッドを使用して取得できます。
- **音声のプロパティ**: `SpeechSynthesisUtterance`オブジェクトには、音声の速度（`rate`）、ピッチ（`pitch`）、音量（`volume`）などのプロパティがあります。
- **イベントリスナー**: 音声合成中に発生するイベント（開始、終了、エラーなど）を処理するために、リスナーを追加することができます。

## 例
以下は、基本的な使用例です。

```javascript
// SpeechSynthesis APIの利用
const utterance = new SpeechSynthesisUtterance("こんにちは、これは音声合成のデモです。");
utterance.lang = "ja-JP"; // 日本語を指定

// 音声の合成を開始
window.speechSynthesis.speak(utterance);
```

### 音声の選択例
```javascript
// 利用可能な音声を取得
const voices = window.speechSynthesis.getVoices();
const utterance = new SpeechSynthesisUtterance("こんにちは！");

// 利用可能な音声から日本語音声を選択
utterance.voice = voices.find(voice => voice.lang === "ja-JP");

// 音声の合成を開始
window.speechSynthesis.speak(utterance);
```

## 説明
- **共通の落とし穴**: `getVoices()`メソッドは非同期であり、音声が利用可能になる前に呼び出すと空の配列が返されることがあります。音声がロードされるのを待つために、`voiceschanged`イベントをリッスンすることが推奨されます。
- **ブラウザの互換性**: SpeechSynthesis APIは、主要なブラウザでサポートされていますが、実際の音声合成の品質や言語のサポートはブラウザによって異なる場合があります。
- **音声のカスタマイズ**: `rate`、`pitch`、`volume`のプロパティを調整することで、音声の特性を変更できますが、使用するブラウザによっては一部のプロパティが無視されることがあります。

## 一文要約
SpeechSynthesisは、JavaScriptを使用してテキストを音声に変換し、ウェブアプリケーションにインタラクティブな音声機能を追加するためのAPIです。