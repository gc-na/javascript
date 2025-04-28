<!--
Meta Description: # SpeechSynthesisUtterance: JavaScriptによる音声合成の基礎 ## 概要 `SpeechSynthesisUtterance`は、Web Speech APIの一部として、ブラウザで音声を合成するためのオブジェクトです。このオブジェクトを使用することで、テキストを...
Meta Keywords: utterance, speechsynthesisutterance, javascript, lang, speechsynthesis
-->

# SpeechSynthesisUtterance: JavaScriptによる音声合成の基礎

## 概要
`SpeechSynthesisUtterance`は、Web Speech APIの一部として、ブラウザで音声を合成するためのオブジェクトです。このオブジェクトを使用することで、テキストを音声に変換し、ユーザーに音声で情報を提供することができます。

## ドキュメンテーション
`SpeechSynthesisUtterance`は、音声合成に関する機能を提供するために設計されています。主な目的は、アプリケーションやウェブサイトでテキストを音声に変換することです。これにより、視覚的な情報を補完したり、アクセシビリティを向上させたりすることができます。

### 使用方法
1. **オブジェクトの生成**: `SpeechSynthesisUtterance`のインスタンスを作成します。
   ```javascript
   const utterance = new SpeechSynthesisUtterance('こんにちは、世界！');
   ```

2. **プロパティの設定**: 音声の言語、ピッチ、速度などを設定できます。
   ```javascript
   utterance.lang = 'ja-JP';
   utterance.pitch = 1;
   utterance.rate = 1;
   ```

3. **音声の再生**: `speechSynthesis`オブジェクトを使用して、音声を再生します。
   ```javascript
   window.speechSynthesis.speak(utterance);
   ```

### プロパティ
- `text`: 読み上げるテキスト。
- `lang`: 音声の言語（例: 'ja-JP'）。
- `pitch`: 音声のピッチ（0.0から2.0の範囲）。
- `rate`: 音声の速度（0.1から10.0の範囲）。
- `volume`: 音声の音量（0.0から1.0の範囲）。

## 例
以下は、基本的な使用例です。

### 例1: 簡単な音声合成
```javascript
const utterance = new SpeechSynthesisUtterance('こんにちは、ユーザー！');
utterance.lang = 'ja-JP';
window.speechSynthesis.speak(utterance);
```

### 例2: ピッチと速度の調整
```javascript
const utterance = new SpeechSynthesisUtterance('お元気ですか？');
utterance.lang = 'ja-JP';
utterance.pitch = 1.5; // 高いピッチ
utterance.rate = 0.8; // ゆっくりとした速度
window.speechSynthesis.speak(utterance);
```

## 説明
`SpeechSynthesisUtterance`を使用する際の一般的な落とし穴や注意点には以下のようなものがあります。

- **音声のサポート**: すべてのブラウザが同じ音声をサポートしているわけではないため、異なるブラウザでの動作を確認することが重要です。
- **非同期処理**: 音声合成は非同期で行われるため、音声の再生が完了するまで他の処理が進行することがあります。
- **アクセシビリティ**: 音声合成を使用する際は、視覚障害者や聴覚障害者など、さまざまなユーザーに配慮した設計が必要です。

## 1文の要約
`SpeechSynthesisUtterance`は、JavaScriptを使用してテキストを音声に変換するための強力なツールです。